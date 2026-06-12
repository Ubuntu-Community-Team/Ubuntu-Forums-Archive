---
title: "[SOLVED] WINE support for Form Viewer"
date: 2007-10-29
forum: General Help
---

### Post by rsh on 2007-10-29
Wondering if there are any active duty Air Force members out there or anyone else who uses Form  Viewer.

If not, Form Viewer is the (sigh) application of choice for writing performance reports etc.  Unfortunately for me it doesn't appear to be supported by WINE.  Any other ideas on what I might be able to do in order to read .xfdl files short of a dual-boot setup?  Like most I am trying to cut all possible ties with M$.  Here is the URL to the app.  Thanks for any help.

[http://www.e-publishing.af.mil/forms-pubs/viewerdownload.asp](http://www.e-publishing.af.mil/forms-pubs/viewerdownload.asp)

UPDATE:

Got Wine to install the program and open files.  I am getting some errors, though I think they may be related to the program itself being bug infested (at best).  Either way, here are the errors the program's error log produces in case anyone else has seen this.  Thanks.

Mon Oct 29 22:38:45 2007 0 Viewer : 
	at MUCreateDir(\Anthill_Build\Branch-API-Cannae-20050228\Api\src\masqutil\masqutil.c:10427 Tue Apr 19 21:59:46 2005):24:32 -> 17

	at MUCreateAllDirs(\Anthill_Build\Branch-API-Cannae-20050228\Api\src\masqutil\masqutil.c:10521 Tue Apr 19 21:59:46 2005):24:32 -> -1

---

### Post by MrFSL on 2007-10-30
Not Air Force but I have worked with the Army - Does the AF use Pure Edge or is this just an Amry thing?

Regardless I have had some (sigh..) small amount of success with Pure Edge. Of course no luck with digital signatures etc.

---

### Post by rsh on 2007-10-30
Of course the Army and the Air Force could not decide on one piece of software.  I am not worried about digital signatures, I can do those at work.  The only thing I need to be able to do is edit the files and I think I can do that now.  

I will leave the thread open a day longer in hopes that someone might have some insight on the print issue.  If not, I will resort to emailing it back to work and printing it there.  Not a huge sacrifice since I have to go there anyway.

---

### Post by MrFSL on 2007-10-30
Well if you look at the main DoD forms websites you might find that your forms also have editable pdf form version - and that is defiantly supported in Linux. 

> Of course the Army and the Air Force could not decide on one piece of software.

I have worked with both at different times in different ways... trust me... it's not the Air Force's fault ;)

---

### Post by campnavajo on 2007-12-24
We have similar problems in the IT department at Camp Navajo, an Army Nation Guard depot. Our security officers are still using the ancient Jet Form Filler. We want to move away from it in a way that will be flexible enough for our IT staff, easy enough to learn and use for our security officers, and resistant to changing technologies.

Our solution of choice is recreating the necessary forms on a web interface accessible on our LAN. It's OS-independent, secure, future-proof, easily upgradeable, and a browser containing built-in automatic spell-checking (Firefox 2, etc) makes it even more attractive.

But there's still the issue of copying the original forms to include all relevant data in the recreations. For that, I can print a blank PDF with eVince. ;)

Good luck!

---

