# IO-BPG BPMN Extension

This repository provides access to the supporting tool for the IO-BPG extension proposed by Ribeiro et al. [[1](#ref1)].

## Table of contents
1. [Details](#details)
2. [Repository contents](#repository-contents)
3. [Tool structure](#tool-structure)
4. [Scenario examples](#scenario-examples)
5. [References](#references)


## Details

The IO-BPG (Inter-Organizational Business Process Governance) is a BPMN extension proposed by Ribeiro et al. [[1](#ref1)], and its main focus is to capture governance aspects in inter-organizational business processes that are not explicitly represented by the standard BPMN.

The IO-BPG metamodel was created in the [ADOxx Metamodelling Platform](https://adoxx.org/), based on the BPMN metamodel available in [Bee-Up](https://bee-up.omilab.org/activities/bee-up/), as described in [[2](#ref2)]. The IO-BPG models can be converted into RDF Knowledge Graphs, enabling semantic queries through SPARQL and natural language querying using the following tools:

- [ADOxx-to-RDF generation tool](https://code.omilab.org/resources/adoxx-modules/rdf-transformation/-/tree/master) - transforms IO-BPG models into RDF Knowledge Graphs.
- [GraphDB](https://graphwise.ai/components/graphdb/) - is an RDF triplestore where the resulting graphs can be imported and queried through SPARQL to retrieve information represented in the models or to generate new information.
- [Talk-to-Your-Graph](https://graphdb.ontotext.com/documentation/11.5/talk-to-graph.html) - is a GraphDB feature that enables natural language querying over the stored graphs using LLM-based agents.


## Repository contents

This repository includes the ADOxx library containing the IO-BPG metamodel ([IO-BPG_Library.abl](IO-BPG_Library.abl)), which must be imported into the [ADOxx Metamodelling Platform](https://adoxx.org/). It will also include the packaged IO-BPG modelling tool, which will allow users to install and use the tool on their own devices, as well as example models created with the tool.


## Tool structure

The tool does not introduce new BPMN elements. It enriches the existing ones with governance-specific attributes. 

An IO-BPG scenario includes a main business process, which describes the workflow between network partners. Each partner can act as a Leader or Participant in the process. The partners can also share data between them using a Data Flow arrow, rather than a Message Flow arrow, which focuses on exchanging messages. The tool also provides additional data object and resource types, including private or shared data, personal or non-personal data, Cloud resources, and AI/ML models.

To represent governance aspects, IO-BPG provides a Virtual Inter-Organizational Governance Pool, with lanes corresponding to the partners involved in the main process. The pool contains governance tasks, which are associated with the corresponding tasks from the main process. A task from the main process can have one or more governance-related tasks associated with it. 

For each governance task, the user can specify the governance role, governance operation, traceability, and whether the task is collaborative, meaning that it requires collaboration with another network partner.

All these attributes are represented graphically within the BPMN elements.

## Scenario examples

### 1. Port Management scenario

This scenario describes the geographical location determination between a transport company and a port management company. It was originally proposed by Ribeiro et al. [[1](#ref1)] and modeled in ADOxx in [[2](#ref2)].

![Port Management Scenario](images/port_management.png)

### 2. Store-Supplier Collaboration scenario

Described in [[2](#ref2)], the second scenario captures the collaboration between a store company and a supplier, which exchange product and warehouse data in order to identify an available warehouse and prepare the products for shipment.

![Store_Supplier Scenario](images/store_supplier.png)


### 3. Energy Optimization scenario

The third scenario illustrates a Facility Management Company and an Energy Service Provider which collaborate to optimize the energy consumption of an office building based on measured consumption data.

![Energy_Optimization Scenario](images/energy_optimization.png)


## References
<a name="ref1"></a>
[1] V. H. Ribeiro, J. Barata, P. R. da Cunha, Modeling inter-organizational business process governance in the age of collaborative networks, in: Electronic Markets 34, 2024, article 51, https://doi.org/10.1007/s12525-024-00730-2 

<a name="ref2"></a>
[2] T. M. Grigorovici, A Knowledge Graph Treatment to the IO-BPG Extension of BPMN, in: Proceedings of ISD 2026, AIS eLibrary, 2026, https://doi.org/10.62036/ISD.2026.12
