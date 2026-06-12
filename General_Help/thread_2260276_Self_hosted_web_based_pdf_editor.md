---
title: "Self hosted web based pdf editor?"
date: 2015-01-10
forum: General Help
---

### Post by k7_madman on 2015-01-10
At my organization there are many users that want want to edit PDF files.  This can range from basic filling in forms on flat pdf files to completely changing the PDF file altogether.

Right now we install Adobe Pro for all users that need to edit PDF files which is expensive and a licensing hell.

In a pinch we have used online PDF editors which work well for basic filling in forms, but I would like to host my own.  Are there any projects like this out there where I can roll my own web based PDF editors?  This would help greatly with basic PDF editing or even converting PDF to word, then I can conserve Adobe Pro licenses for those who really need them.

---

### Post by dragonfly41 on 2015-01-10
Perhaps orbeon meets your enterprise requirements?

[www.orbeon.com]("http://www.orbeon.com")

There is a community version and professional version.

Orbeon runs as standalone (with its own server).  
Or you can install the orbeon.war on a tomcat server.
I have it running on tomcat7 localhost Ubuntu 14.04 for development experimental purposes.

...

You could also look at PHP + XForms.


[p.s]
In Orbeon, PDF templates are only offered in the Professional Version.
But there is a free trial period.

---

### Post by k7_madman on 2015-01-10
@Dragonfly

Thank you for your response.  The Orbeon product looks interesting and we could use it on another project.

What we are looking for is something more like this [http://online2pdf.com/]("http://online2pdf.com/") or [https://www.pdfbuddy.com/]("https://www.pdfbuddy.com/")

These are sites where a user can upload a PDF file and edit the files online. The "free" versions have limits, like the amount of pages that can be modified.

I would like to host my own version of this that does not these limits.

---

### Post by dragonfly41 on 2015-01-11
Can your users source documents be in *.doc, *.docx or *.xml or other non-PDF format

and then return from your server final published content as PDF?

In other words not editing source PDF documents?

This would make the implementation much easier than having to reverse engineer PDF documents.

---

### Post by k7_madman on 2015-01-11
@Dragonfly

Unfortunately, the source document is usually a pdf file from an external organization.  Most of the time it is an application for a government grant or research proposal.  I found a quick example linked below, it is only 1 page, but if you can imagine a multi page pdf form asking for different projected dates and budget information.


[http://www.samhsa.gov/sites/default/files/charchoice_assurance.pdf]("http://www.samhsa.gov/sites/default/files/charchoice_assurance.pdf")

---

### Post by dragonfly41 on 2015-01-11
So as I now understand the source PDF documents are imported, not created, by your users.

A few more questions to clarify before I post some ideas for a prototype system.

i.e a requirements specification.

...

Roughly how large is the user community?

Do the imported PDF documents have editable text fields? i.e. in the example you give there are these editable fields:

signature field
title field
applicant organization field
date submitted field

How would you propose adding a user's personal signature .. by image?

Who should sign the document?

If any downloaded PDF does not have editable fields who do you prefer should add these .. each user or a document admin manager?

When you say "the source document is *usually* a pdf file" .. what are the *unusual* formats other than pdf?

...

In fact I have made a rough mashup which converts the test PDF you give to an editable form.  But I need to understand the workflow before suggesting a possible server solution.

---

