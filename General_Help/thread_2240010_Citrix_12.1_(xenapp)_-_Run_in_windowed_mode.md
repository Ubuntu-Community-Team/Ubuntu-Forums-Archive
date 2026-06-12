---
title: "Citrix 12.1 (xenapp) - Run in windowed mode"
date: 2014-08-17
forum: General Help
---

### Post by andradejose89 on 2014-08-17
Hello all,


  Is there a way I can force the Citrix client - run through xenapp - to run in  windowed mode? I have tried using the wfcmgr but it doesn't seem to save my  settings. 

Would also love to be able to alt-tab out of Citrix.

  
Many thanks in advance,


  José

[I]Using Ubuntu 14.04
[/I]

---

### Post by Rob Sayer on 2014-08-17
[http://www.citrix.com/support.html?posit=glnav](http://www.citrix.com/support.html?posit=glnav)

---

### Post by andradejose89 on 2014-08-18
Thank you Rob but no luck. 

Is there a way I can force ubuntu to run the program in windowed mode?

---

### Post by andradejose89 on 2014-08-19
Solved. 

Open terminal: 

gedit ~/.ICAClient/All_Regions.ini

Then edit lines 852/3 to your desired resolution.

DesiredHRES=1366
DesiredVRES=768

---

