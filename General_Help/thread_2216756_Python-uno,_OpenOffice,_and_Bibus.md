---
title: "Python-uno, OpenOffice, and Bibus"
date: 2014-04-13
forum: General Help
---

### Post by rdbowers on 2014-04-13
I've been using OpenOffice for years, although when Ubuntu 12.04LTS came out, I went ahead and tried LibreOffice.  Yesterday I stripped it from the computer because it's too buggy for the stuff I do (copy-and-paste problems, scrambles when saving in Microsoft-type formats, trouble integrating with other packages, and a severe lack of add-ons that I used in OpenOffice).  I installed the latest version of OpenOffice, which always worked well for me.  I need something I don't have to play with to get working (and don't have time to read thread after thread after thread after thread trying to find a solution to a problem).

I can't get Bibus to talk with the new version of Open Office.  After trying all of the "fixes" I've read about, I've narrowed it down to problems with python-uno.  Bibus looks for it before it will allow you to activate the interface between it and OpenOffice, and when you try to install python-uno, it insists on installing LibreOffice.  I tried to install it while leaving LibreOffice out, and it seems that python-uno directs to the non-existent LibreOffice and that causes Bibus to crash.  OpenOffice has drivers that SHOULD interface with the Bibus database, but the directions are obsolete.

I know that OpenOffice has something that works like python-uno (which I think is separate from pyuno which is on this computer).  I'm wondering which file it would be and if there is some way to create a virtual link to that file which would enable Bibus.

I've spent hours on this headache... and I've got three papers to turn in by the end of the month.  I NEED to have my stuff working - completely.  Oh, and I've got good reasons why I run Ubuntu 12.04LTS/OpenOffice/Bibus/Etc..  I'd rather the "change OS - Use what we provide (LibreOffice which is NOT satisfactory)- if you don't like it leave - here's links to 100 pages, start reading" comments be left out.

Please help!

Thanks!

---

### Post by ian-weisser on 2014-04-13
I'm confused. I don't understand the problem, nor the solution you seek.

I've used Python-uno for years, with both OpenOffice and LibreOffice, to link OO/LO with other applications...though not Bibus.

Are you asking specifically for help with Python and Uno and Python-uno? Or are you asking for help troubleshooting the problem from scratch? Or something else?

Are you using compatible versions of OpenOffice and Bibus? What versions? Did you get them from the Ubuntu repositories, or from somewhere else?

What's the specific problem you're seeing? Bibus can't find OO? OO can't find Bibus? You're getting an error message? 
You've spent a lot of time researching the problem...what have you discovered?

---

### Post by rdbowers on 2014-04-13
I'm trying to get Bibus to recognize OO and start functioning with it.  The new version of OO uses something different from python-uno, but from what I read the module (forgot the name) essentially functions the same - and python-uno is not included with the newer versions of OO.  Bibus appears to use python-uno to identify that OO is present and the software may provide some interconnection there.  As far as compatibility, Bibus was made to work with OO.  When you try to install python-uno (or python3-uno) from the repositories the various tools ("Ubuntu Software Center", Synaptic, and apt) also insist on installing libreoffice, or at least the core and some peripherals at the same time.  LO and OO don't play well together at all - what I read indicates you can have one or the other but not both.  I don't think other distros have as much problem.

The version of Bibus is the latest - 1.5.1 (came from the Ubuntu repositories).  The version of OO is 4.01 or something like that - the most recent directly from Apache.  I've already modded the bibus.cfg file so Bibus "knows" where to find the OpenOffice files.  I've already got OO ready to communicate with Bibus.  The problem seems to be the lack of python-uno in the new OO.  

No error codes. Bibus just doesn't recognize the presence of OpenOffice even with the paths laid out for it.  Adding python-uno (without LO) causes Bibus to "see" OO, but it locks up when you try to save the setup.  It all has to do with python-uno for some reason.  Now, I can access Bibus from the Bibliography module in OO (by connecting it through OBDC), but that is pretty much worthless for the sort of heavy citing stuff I do (my Bibus database has several hundred entries - and I'm adding new stuff all the time).

---

