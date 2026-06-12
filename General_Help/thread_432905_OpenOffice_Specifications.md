---
title: "OpenOffice Specifications"
date: 2007-05-04
forum: General Help
---

### Post by Zill on 2007-05-04
Any ideas about where to find OpenOffice 2.0 specifications? 

At the moment I am looking for maximum field lengths for the different Field Types used in the database component.  Similar info on limits for other properties would also be useful to users.

Can't find this on the OOo site or elsewhere but if anyone has a link this would be much appreciated.

Thanks.

---

### Post by Thingymebob on 2007-05-04
My understanding is that OOo Db uses the built in HSQLDB Engine by default which is Java based so your data type properties will be the same as the Java equivalents ie int will be equivalent to java.lang.Integer

You can also connect to JDBC ODBC MySQL Ms Access DBase etc so the data types will be set by whatever type you have connected to.

The documentation for the HSQLDB engine can be found [http://hsqldb.org/web/hsqlDocsFrame.html]("http://hsqldb.org/web/hsqlDocsFrame.html")

with the data type section here [http://hsqldb.org/doc/guide/ch09.html#datatypes-section]("http://hsqldb.org/doc/guide/ch09.html#datatypes-section")

---

### Post by Zill on 2007-05-08
Many thanks for the info Thingymebob.  Lots of reading for me there so it will take a while to digest but looks like I should find what I want.  I was hoping for a simple list in the OOo help - not much chance of that though ;-)

---

