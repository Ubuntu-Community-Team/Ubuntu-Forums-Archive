---
title: "x wont start"
date: 2007-11-28
forum: General Help
---

### Post by cryo4.rm on 2007-11-28
trying to add a 2nd monitor i had to restart x to activate the settings i had modified..

 now when i try to start X i get an error message -- 

(WW) I810: No matching device section found
(EE) I810 (0): You must have a MonitorLayout defined for us in Dualhead, clone or mergedFB setup.
(EE) I810 (1): Failed to setup second head due to primary head failure.
(EE) Screen(s) found, but none have a usable configuration

Fatal server error:
No screens found
XI0: fatal I0 error 104 (connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining.

---------------------------------------

i tried to get into the config file... /etc/X11/xorg.conf but my command line knowledge is near zero
 please.. can anybody help me fix this issue... im desperate.. i need my computer to study for an exam !!

---

### Post by subs on 2007-11-28
u must still be able to use the text mode even if loading the gui fails....

login to ur user nd try this...
> sudo dpkg-reconfigure xserver-xorg

then reconfigure xserver to make it work

---

### Post by cryo4.rm on 2007-11-28
thanx

---

### Post by cryo4.rm on 2007-11-28
i ran the setup but now the problem is simply that there are no devices detected

any suggestions?

---

