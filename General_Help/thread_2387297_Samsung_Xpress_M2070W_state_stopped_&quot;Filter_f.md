---
title: "Samsung Xpress M2070W state stopped &quot;Filter failed&quot;"
date: 2018-03-17
forum: General Help
---

### Post by sliack on 2018-03-17
Hi everyone,

I'm trying to use a Samsung printer (Xpress M2070W).
I've installed Xubuntu on my laptop. This are the specifics: 

Kernel 4.13.0-37-generic
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.4 LTS
Release:    16.04
Codename:    xenial

I've installed the printer's drivers from Samsung website (UnifiedLinuxDriver). I chose the driver manually, searching in PPD folder. 
The printer is recognized by the system, but when I try to print gives me a generic error ("There was a problem processing document 'test page').
I read some threads and managed to log in CUPS. Managing my printer from  [http://localhost:631/](http://localhost:631/) the situation is the same. The printer is recognized but trying to print the test page the system gives me back an error message. CUPS overview describe the printer status as: stopped "Filter failed".

I reinstalled the printer drivers many times, trying also the generic ones, but nothing changed. I reinstalled CUPS packages as well, as I read in some threads it could be a solution, but nothing.

Any suggestion?
Thank you a lot in advance.

---

