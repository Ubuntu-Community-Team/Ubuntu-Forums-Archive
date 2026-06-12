---
title: "installing firefox2.0.0.7"
date: 2007-09-26
forum: General Help
---

### Post by oxhaksi on 2007-09-26
hi
i am a newbee in linux.i am trying to update firefox to 2.0.0.7 and i cant figure out how to install it.i extracted the downloaded file and i went to /home/name/desktop/firefox/ and i tried all the files inside and nothing worked. 

can someone please tell me what i am doing wrong?

---

### Post by por100pre1 on 2007-09-26
Try using [Ubuntuzilla]("http://ubuntuzilla.wiki.sourceforge.net/"). It makes easy to install the newest Firefox version.

---

### Post by Perpetual on 2007-09-26
Thanks for the link.  Question though, if I update using Ubuntuzilla and then do a system upgrade when Gutsy releases, is it going to cause a problem if Gutsy has a version that is older than what I have?  Maybe that won't be the case, just trying to not cause myself problems when the upgrade comes out next month.

Thanks!

---

### Post by caver1 on 2007-09-26
You can open Firefox as root in Terminal and you will have the update function enabled.
In Terminal;  sudo Firefox  enter your password.  :)
caver1

---

### Post by Perpetual on 2007-09-26
> **caver1 said:**
> You can open Firefox as root in Terminal and you will have the update function enabled.
In Terminal;  sudo Firefox  enter your password.  :)
caver1

I tried that and the Help > Check For Update is not available.

---

### Post by nanotube on 2007-09-26
> **Perpetual said:**
> Thanks for the link.  Question though, if I update using Ubuntuzilla and then do a system upgrade when Gutsy releases, is it going to cause a problem if Gutsy has a version that is older than what I have?  Maybe that won't be the case, just trying to not cause myself problems when the upgrade comes out next month.

Thanks!

won't cause a problem - ubuntuzilla doesn't mess with the repository system, so the two firefox versions will coexist side by side without interfering.

---

### Post by nanotube on 2007-09-26
> **caver1 said:**
> You can open Firefox as root in Terminal and you will have the update function enabled.
In Terminal;  sudo Firefox  enter your password.  :)
caver1

that only works if you are using the mozilla build. the repositories version has that feature disabled.

also, even for the mozilla build, your commandline is incorrect. should be
```
gksudo firefox
```
not "sudo firefox". :)

---

### Post by Perpetual on 2007-09-26
> **nanotube said:**
> won't cause a problem - ubuntuzilla doesn't mess with the repository system, so the two firefox versions will coexist side by side without interfering.

Thanks for the clarification.

---

### Post by caver1 on 2007-09-26
> **nanotube said:**
> that only works if you are using the mozilla build. the repositories version has that feature disabled.

also, even for the mozilla build, your commandline is incorrect. should be
```
gksudo firefox
```
not "sudo firefox". :)

All I is the repo version and it works. 
both sudo firefox and gksudo firefox , both take me to the same place so what's wrong with sudo.  Both ask for password and open FF in root.  :confused:
caver1

---

### Post by FuturePilot on 2007-09-26
Using sudo for graphical apps can cause permission problems.
Read here
[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

You should always use gksudo for graphical apps.

---

### Post by mikewhatever on 2007-09-26
> **caver1 said:**
> All I is the repo version and it works. 
both sudo firefox and gksudo firefox , both take me to the same place so what's wrong with sudo.  Both ask for password and open FF in root.  :confused:
caver1

The update option in Firefox is grayed out, no matter if it is sudo or regular. Something must be wrong with yours.:confused:

---

### Post by FuturePilot on 2007-09-26
> **caver1 said:**
> All I is the repo version and it works. 
both sudo firefox and gksudo firefox , both take me to the same place so what's wrong with sudo.  Both ask for password and open FF in root.  :confused:
caver1

Are you sure it's the Ubuntu version? It should still be grayed out even when launched as root. You must be running the Mozilla version.

---

### Post by caver1 on 2007-09-26
No not moz version. 
so far using sudo haven't had a problem but thanks for the heads up. 
Still learning.
caver1

---

