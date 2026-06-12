---
title: "[SOLVED] disabling auto-starting of processes"
date: 2008-02-03
forum: General Help
---

### Post by TOM_C_A_T on 2008-02-03
hello linuxians out there,

from last few days I'm facing a new prob,

**prob commenced from :**
since I installed the 'tracker search tool',

**prob:**
as I start my pc,

the processes trackerd, pdftotext and pdfilter are starting automatically

hogging up 60 to 70 % of CPU and 0 to -10 % of NICE !!

reducing the perfo of pc !!

The 'pdftotext' process has multiple instances too !

**my troubleshoot practise:**

1. I tried to remove the tracker search tool, to get rid of 'trackerd ' process,
    but in vain.

2. changed the priority of processes but in vain, after a restart it gets as it was !

3. it releases the cpu usages as soon as delete the file in 
    "/tmp/Tracer-*username*.5829/temp-text-file-*somenumber*

4. after restart a new one is created again in above location

5. tried on net for some similar issues but couldn't find any

**my config. and condi. of pc**:

p4 2.6 ghz, intel 845 gl/gv board, 1gb ddr 333mhz ram

have lot of pdf, chm n txt files ( mostly ebooks) on hdd

use ubuntu 7.10 gutsy gibbons


**so, pls guide me on this**

---

### Post by Rome.konig on 2008-02-03
humm when you go to preferences/sessions uncheck the programs thats hoggins sources. then under current sessions remove its processes and press apply, then close menu and redo the process agian and press apply then in session options save currently running applications. 

this worked for me

---

### Post by Rome.konig on 2008-02-03
how did you try to remove the tracker search tool? through package manger or sudo commands?

---

### Post by TOM_C_A_T on 2008-02-03
yeah man,

thank you very much !!

sessions thing worked !!

I wonder how it got skipped outta my mind :confused:


but one question rises again,

I've already removed the tracker search tool

**through the Add/Remove **

uncheck method,

how it is still there ?

should I del the 'trackerd' daemon file from /usr/bin directory, manually  ?

to get a complete rid of it,

or are there any other remains ???

Please, explain ,

thanx in advance !!!!:)

---

