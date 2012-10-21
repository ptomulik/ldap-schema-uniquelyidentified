uniquelyidentified.schema
=========================

This package contains single LDAP schema with an **uniquelyIdentified** and 
**uniquelyIdentifiedMust** auxiliary object classes having only the
[uniqueIdentifier](http://tools.ietf.org/html/rfc4524#section-2.24) attribute.

WORD OF CAUTION
===============

This is experimental schema. It is possible, that the object classes defined
here may collide with some objects from other schemas. Before installing it
into your production machine check your other schemas. It is also advisable to
test it on non-production directory server first.

INTRODUCTION
============
The **uniqueIdentifier** attribute is defined in
[cosine.schema](http://tools.ietf.org/html/rfc4524#section-2.24). However,
there seems to be no OpenLDAP schema available containing objects with this
attribute. This attribute was previously part of the **pilotObject** object
defined by [RFC1274](http://www.ietf.org/rfc/rfc1274.txt) and was also
inherited by **pilotPerson** object class. However, the RFC1274 was obsoleted
by more recent **RFC4524**, and the **pilotObject** is no longer provided (see
**RFC4524** [Appendix-A.2](http://tools.ietf.org/html/rfc4524#appendix-A.2)).
In the current version of OpenLDAP (2.4.31) the **cosine.schema** still defines
the **pilotPerson**, but **pilotObject** is not there anymore.

The **uniqueIdentifier** may be easily used in OpenLDAP by adding
**extensibleObject** objectClass to an entry. However, not all directory servers
support it so problems may arise when migrating data from one directory server
to another. Also general-purpose LDAP front-ends may have problems with handling
the **extensibleObject** well (usually the extra attributes can be added only
in second pass/modification after the object has been created).

This simple schema allows to easily introduce the **uniqueIdentifier** attribute
to your LDAP directory.

REQUIREMENTS
============

This schema depends on **cosine.schema** and its dependencies.

INSTALLATION
============

The files to install are located in the **schema** directory. The
**schema/uniquelyidentified.schema** may be used for traditionally configured
servers. Follow standard instructions for your directory server. For OpenLDAP
with new-style config (olcXxx) use **schema/uniquelyidentified.ldif** as
follows:

`sudo ldapadd -Y EXTERNAL -H ldapi:/// < schema/uniquelyidentified.ldif`

LICENSE
=======

Copyright &copy; 2012 by Paweł Tomulik

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE
