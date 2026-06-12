---
title: "can't remote open DB2 Control Center"
date: 2007-01-23
forum: General Help
---

### Post by sunx on 2007-01-23
Hi all, 
  I had installed DB2 V9 Express-C on my server Ubuntu 6.10 and it runs 
well. Now, I would like to open DB2 Control Center from my windows (I 
use ssh and putty to connect with server ).In fact, I can do my 
requests using the commands, but I think that it will be better with 
control center. So i install Xming as Xserver. And i use the commands 
xhost + MyAddressIP and export DISPLAY=localhost:0.0 to configuer. Now 
if i login with the usr of linux, it runs well (i had used xclock to 
test). But if I login as db2inst1, all of these variables of envirement 
were reset. And I use the commandsabove for set ces var. But the 
results are: 
   Exception in thread "main" java.lang.NoClassDefFoundError: 
sun.awt.X11.Xtoolkit. 
But it is so strange that : if i use export DISPLAY=:0.0, the control 
center is opened from the server. 
  Any idea? 
  Thanks 
  xiaoning

---

