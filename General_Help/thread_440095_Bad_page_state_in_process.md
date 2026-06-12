---
title: "Bad page state in process"
date: 2007-05-11
forum: General Help
---

### Post by gerjantd on 2007-05-11
Hi,

Since a week or so, or perhaps since my upgrade from Edgy to Feisty (2007-04-20) I get occasional errors like the following:

> 
May 11 15:24:39 knopje-ubuntu kernel: [ 7224.132000] Bad page state in process 'evince'
May 11 15:24:39 knopje-ubuntu kernel: [ 7224.132000] page:c1939000 flags:0x00000001 mapping:00000000 mapcount:2 count:0
May 11 15:24:39 knopje-ubuntu kernel: [ 7224.132000] Trying to fix it up, but a reboot is needed

The problem doesn't appear to be related to any particular process; so far I've seen it while zipping a folder (archiver), while copying a number of files (nautilus) and while viewing a PDF (evince). Clearly the kernel's not happy about something but I really don't have a clue as to what to do about it. Apart from rebooting as the systems suggests, but then this doesn't really solve the issue and is hardly practical :( 

I followed [this]("http://lkml.org/lkml/2007/4/15/189") ([http://lkml.org/lkml/2007/4/15/189](http://lkml.org/lkml/2007/4/15/189)) advice to check my memory, but a full pass of memtest reported no faults.

I am running 2.6.20-15-generic on an HP Compaq nc8000.

Any suggestions would be most welcome.

Ger-Jan

---

### Post by Astrophobos on 2007-05-20
Hi gerjantd,

I see alot of these error too on one of my system out of 4. Before installing feisty this system was with dapper and except from some trouble with the sky2 drivers I never had problem with it. But since feisty it keep crashing and filling my log file with "Bad page state in process 'put a proccess name here'"

Most of the time the process is kswapd0. Sometime when i'm not in front of the screen the log can fill up very fast, like 1.4Mb/min until I realize it and reboot the pc.

Well just to let you know that you are not alone. I will search in launchpad if I can find something related.

---

