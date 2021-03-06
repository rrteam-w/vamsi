# Webservices
Webservice is software application or service which is readily available in a particular location.
There are two ways to implement the webservices. Those are:
1. JAX-WS - Java API for XML webservices.
2. JAX-RS - Java APT for Restful webservices.
The main advantage of webservices is interoperability and loosely coupling.

# Legacy Implementation
Core Java - RMI - Remote Method Invocation.
Initially we suppose to use RMI, to develop or access the remote services by using stub and skeleton.
But this is platform dependent.
** CORBA - Common Object Request Broker Architecture.
The Common Object Request Broker Architecture (CORBA) is a specification developed by the Object Management Group (OMG). 
CORBA describes a messaging mechanism by which objects distributed over a network can communicate with each other irrespective of the platform and language used to develop those objects.
This is platform independent to share and access the web services but this is protocol dependent i.e. iiop.
These are all the drawbacks about legacy implementations.

** A2A - Application To Application - WSDL
If you want to share or access the webservices with in organization then you can directly share WSDL file to see details about webservices.
** B2B - Business To Business - UDDI
If you want to share or access the webservices at the global level then register your webservices with UDDI repository.
SOAP - simple object access protocol
XML - Extensible markup language - SOAP uses XML to exchange the data in between webservices.

# SOAP messaging format

soap:envelope
 soap:header </soap:header>
 soap:body </soap:body>
</soap:envelope>

** Note: <soap:header> is optional.

UDDI -  Universal Description, Discovery, and Integration - To register webservices with it.
WSDL - Webservice Description Language - Describes about webservices.

# WSDL structure

definitions
 types </types>
 messages </messages>
 porttype </porttype>
 bindings </bindings>
 services </services>
</definitions>


# JAX-WS styles

1. document - If it is document style then you will see .xsd file in WSDL.
2. RPC - Remote Procedure Call  - If it is RPC style then you should not see .xsd file in WSDL.

** Note: .xsd it is an external file and it contains input elements of web methods in the webservice.

Two ways we can implement the JAX-ws webservices. Those are:
1. Bottom-to-top approach - Here you are creating webservice and generating WSDL file.
2. Top-to-bottom approach - Here you have WSDL file based on that you will implement or create the webservices.
Axis or Axis2 is the specification for JAX-WS.
The following are the some annotations to implement the JAX-WS. Those are:
1. @Webservice
2. @Webmethod(operationName="methodName")
3. @Webparam(name="name") and etc...

# JAX-RS
REST - Representational State Transfer.
JAX-RS is an architectural style and it follows the webstandards and it uses the http protocol.
Http protocol is stateless protocol.
If you want to maintain client conversation with server then use the following concepts.
1. Session
2. Cookies
3. Hiddenelements
4. URL rewriting

** Webstandard methods are
POST, GET, PUT, DELETE
There are so many specifications for JAX-RS implementation.
1. Jersey
2. Spring REST
3. RESTeasy and etc...
The following are the some annotations to implement JAX-RS by using Jersey. Those are:
1. @Path
2. @GET
3. @POST
4. @PUT
5. @DELETE
6. @Pathparam
7. @QueryParam
8. @Produces
9. @Consumes
There are different MIME types. Like
1. text/plain
2. text/html
3. application/xml
4. application/json
5. application/PDF and etc...
In this course, we are using jersey to implement the JAX-RS.

# Advantages of Jersey
1. It provides a server and client library to implement web services and access it.
2. It will do marshalling and un-marshalling for you by using JAXB (Java API for xml binding).
3. It provides a frontcontroller to access the client requests.
4. It is production easy to develop webservices with Jersey.

** marshalling - convert your java object into xml.
** un-marshalling - convert xml into java object.
For example, If you want to convert java object into JSON and vice-versa, then we need to add a library called Jackson and jettison.

POST method is non-idempotent. This method is NOT repetable.
PUT, GET, DELETE methods are Idempotent methods. These methods can be repetable.

Idempotent is the property of certain operations in mathematics and computer science whereby they can be applied multiple times without changing the result beyond the initial application.

# Error codes

200 - ok - SUCCESS
404 - NOT Found - method is not exists
405 - Method Not Allowed - If there is no method exists but still you are making a call, in that scenario you will see this error.
500 - Internal Server Error - If both methods type is same for example GET, when you try to access the resource it will throw ambiguity problem, because both methods types are same and it does not know which one need to pull first.

To overcome this problem, either you need to provide @path to anyone of the method or add the @Produces annotation with different MIME types for both methods.

# Browser Prioritization
If you write all different MIME types without @Path annotation, for get request methods in a class. The browser will display following prioritization. like
1. text/html
2. application/xml
3. text/xml
4. text/plain
5. application/json
