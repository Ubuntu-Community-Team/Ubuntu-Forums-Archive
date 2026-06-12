---
title: "Firestarter will not start - &quot;eth0 not ready&quot;"
date: 2007-09-24
forum: General Help
---

### Post by bill45 on 2007-09-24
I am on dial-up with a serial modem on ttyS1. I have installed Firestarter configured to run at startup AND start on dial out (both check boxes in GUI).  The Firestarter icon sticks to the panel at startup.  The Firestarter preferences show that the only detected device is thernet (eth0) and not the modem.  There is no modem listed on drop down menu. 

When system starts I get error; 
Firewall not started  
eth0 not ready

When I look at properties in the Network page, the check box always reverts back to wired connection (not modem), and the modem reverts back to pulses regardless of the settings I initially save. 

My network connection button on the panel works and I can dial-out at will and the modem uses tones not pulses and once connected is very reliable.  

Whatsitdoin?

Bill

---

### Post by por100pre1 on 2007-09-24
If Firestarter starts before eth0 is ready it will show the warning, it's normal. The issue can be solved by the disabling the Firestarter startup. It may look convenient, but Firestarter startup is actually a security breach, it's not recommended.

---

