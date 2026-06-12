---
title: "Firefox will not display pdf"
date: 2008-05-12
forum: General Help
---

### Post by minchina on 2008-05-12
I have installed firefox 3 and adobe.  I can read pdf files in general, but when I try and click on a pdf link in firefox I get the following error:

Could not launch Adobe Reader 8.1.1. Please make sure it exists in PATH variable in the environment. If the problem persists, please reinstall the application.

my about:plugins output has the following table at the bottom:

Adobe Reader 8.0

    File name: nppdf.so
    The Adobe Reader plugin is used to enable viewing of PDF and FDF files from within the browser.

MIME Type 	Description 	Suffixes 	Enabled
application/pdf 	Portable Document Format 	pdf 	Yes
application/vnd.fdf 	Acrobat Forms Data Format 	fdf 	Yes
application/vnd.adobe.xfdf 	XML Version of Acrobat Forms Data Format 	xfdf 	Yes
application/vnd.adobe.xdp+xml 	Acrobat XML Data Package 	xdp 	Yes
application/vnd.adobe.xfd+xml 	Adobe FormFlow99 Data File 	xfd 	Yes

so I think that it is installed. My next step was to try and reinstall the plugin, but I think that it is with the "restricted extras" package and I would rather not have to pull all of those just to *maybe* fix this.  Is there another way?

thanks

---

### Post by minchina on 2008-05-27
Just in case anyone else was having this problem, I managed to fix it.  All I had to do was install mozplugger in adept.  Now everything works.

---

### Post by bbarrons on 2008-05-28
thansk for the info. took care of my problems also. all of them. Well, all that relate to firefox... :-)
Bill

---

