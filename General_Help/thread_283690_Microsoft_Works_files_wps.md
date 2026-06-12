---
title: "Microsoft Works files wps"
date: 2006-10-24
forum: General Help
---

### Post by Stochastic on 2006-10-24
Does anyone have any suggestions for opening a microsoft works file (.wps) in dapper?  Open office give an "Input/Output error" message.  Thanks.
[COLOR="Red"]
Edit 081110: Solution here :[/COLOR]
 
> **akadruid said:**
> 
> The Ubuntu version of OpenOffice.org has been able to open .wps files since at least version 2.2 (on Ubuntu version 7.04).

Alternatively, you can use wps2html to convert the .wps file.  Install like this:
```
sudo apt-get install libwps-tools
```
and use it like this:
```
wps2html document.wps > document.html
```
This also works on other distros and Windows, more information here:
[http://jamesmcdonald.id.au/it-tips/opening-wps-files-on-linux](http://jamesmcdonald.id.au/it-tips/opening-wps-files-on-linux)


---

### Post by dbott67 on 2006-10-24
I read somewhere that you can try to open it with AbiWord.

There are also converters available from MS to convert .wps to .doc, but they require MS Office.  If you're the trusting type (and the data is not private/confidential), I can try to convert it for you or if you have access to Windows & Office you can download the converter from [here]("http://www.microsoft.com/downloads/details.aspx?FamilyID=b9e11e83-f51b-4977-b572-8c042df802c1&displaylang=en").

-Dave

PS - If you want me to convert it, PM me.

---

### Post by canadianwriterman on 2006-10-24
Currently, there is no conversion from a WPS file to anything else, except within MS Office or MS Works. There are even conversion issues when using MS Office to open a WPS file. Dumb, isn't it.

The best thing to do is to ask the originator of the WPS document to resave it as a text document.

---

### Post by dbott67 on 2006-10-24
Gotta love proprietary file formats!  Bring on [ODF]("http://en.wikipedia.org/wiki/OpenDocument").

---

