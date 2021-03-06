.. _doc_implementation_models:

Implementation Models
=====================

RPKI is designed to allow every resource holder to generate and publish cryptographic material on their own systems. This is commonly referred to as delegated RPKI. To offer a turn-key solution, each RIR also offers a hosted RPKI system in their member portals. Both models have their own advantages, based on the specific requirements of the organisation using the system. 

Hosted RPKI
-----------

In 2008, when the five RIRs committed to start offering RPKI services, it was clear that there would be an early adopters phase for a considerable amount of time. Given the past experiences with IPv6 and DNSSEC uptake, the RIRs decided to offer a hosted RPKI solution to lower the entry barrier into the technology. This way, organisations could easily get operational experience with the technology, without having to manage a certificate authority themselves.

Hosted RPKI offers a fair balance between ease-of-use, maintenance and flexibility. It allows users to log into their RIR member portal and request a resource certificate, which is securely hosted on the servers of the RIR. All cryptographic operations, such as key roll overs, are automated. The certificates and ROA are published in repositories hosted by the RIR. In short, there is nothing that the user has to manage, apart from creating and maintaining ROAs.

The functionality and user interfaces of the hosted RPKI implementations vary greatly across the five RIRs. Some automate nearly everything, and ROAs can be created based on the announcements that are seen in BGP using the resources on the certificate. In other implementations, ROAs have to be created manually and individually signed with a separate key.

Despite these variations, if you are an organisation with a single ASN and a handful of statically announced IP address blocks that are not delegated to customers, hosted RPKI is sufficient for most use cases.

.. figure:: img/ripe-ncc-hosted-rpki.png
    :align: center
    :width: 100%
    :alt: Example of the Hosted RPKI interface by the RIPE NCC

    Example of the Hosted RPKI interface of the RIPE NCC

Delegated RPKI
--------------

Operators who prefer more control and have better integration with their systems can run their own child CA. This is model is usually referred to as delegated RPKI. 

In this model, the certificate authority that manages object signing is functionally separated from the publication of cryptographic material. This means that an organisation can run a CA and either publish themselves, or delegate this responsibility to a third party, such as a hosting company or cloud provider. 

There may be various reasons for organisations to choose this model. For example, this may be useful for organisations that need to be able to delegate RPKI to their customers or different business units, so that that they can run their a CA on their systems and manage ROAs themselves.

Alternatively, enterprises who manage large amounts of address space across various RIRs, may not want to manage ROAs in up to five different web interfaces. Instead, they might prefer to be operationally independent from the RIR and manage everything from within one package this is tightly integrated with IP address management and provisioning systems. 

Lastly, in the LACNIC and APNIC regions there are several National Internet Registries who provide registration services on a national level to their members and constituents. They also need to be operationally independent and run a certificate authority as a child of their RIR.