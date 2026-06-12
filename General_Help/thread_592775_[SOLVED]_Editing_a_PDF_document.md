---
title: "[SOLVED] Editing a PDF document"
date: 2007-10-26
forum: General Help
---

### Post by lwylie on 2007-10-26
Hi everyone,

     I have an application in PDF format that I am trying to fill out.  Does anyone know of a great utility for making edits to PDF other than PDFedit?  Unfortunately it has locked up after I make a significant amount of edits.  Supposedly Abiword has functionality for converting from PDF to HTML, however, I have yet to figure out how.  Any advice or suggestions are more than welcome!

Thanks

---

### Post by aysiu on 2007-10-26
Make sure you [have extra repositories enabled](http://www.psychocats.net/ubuntu/sources) and then ```
sudo apt-get update
sudo apt-get install acroread-plugins
``` That should allow you to fill out the form *if it's designed to be filled out*. Some forms *look* like forms but really can't be filled out unless you print them out and fill them out by hand.

---

### Post by rudeboyskunk on 2007-10-27
I just download Adobe Reader straight from Adobe's website.  It's not free software but it is no-cost.

---

### Post by lwylie on 2007-10-27
Thanks guys... I sort of have this pseudo mind block for non-free software and forgot about Adobe Acrobat.  It definitely suited its purpose :-D

---

### Post by hrod beraht on 2007-10-27
> **lwylie said:**
> Thanks guys... I sort of have this pseudo mind block for non-free software and forgot about Adobe Acrobat.  It definitely suited its purpose :-D

Gnome 2.20 has an updated version of the [[COLOR="Blue"]Evince document viewer that allows for filling in PDF forms[/COLOR]]("http://www.gnome.org/start/2.20/notes/en/index.html#rnusers-evince").

Bob

---

### Post by pyronicte on 2007-11-22
Evince doesn't print the forms too

---

