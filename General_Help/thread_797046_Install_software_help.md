---
title: "Install software help"
date: 2008-05-16
forum: General Help
---

### Post by alanw8@oh.rr.com on 2008-05-16
Can someone tell me how to install the BOINC client.I installed the management from add remove programs but the client file is not there. I downloaded the client file for Ubuntu. Its 45-i686-pc-linux-gnu.sh I have played around with linux a little bit but I always gave up when I had to install something. Can someone please throw me a clue? Thank you. Alan

---

### Post by Oldsoldier2003 on 2008-05-16
> **alanw8@oh.rr.com said:**
> Can someone tell me how to install the BOINC client.I installed the management from add remove programs but the client file is not there. I downloaded the client file for Ubuntu. Its 45-i686-pc-linux-gnu.sh I have played around with linux a little bit but I always gave up when I had to install something. Can someone please throw me a clue? Thank you. Alan

```
sudo apt-get install boinc-client boinc-manager
```

---

### Post by agentnixon on 2008-05-16
I'm not exactly sure, but isn't it 

sh 45-i686-pc-linux-gnu.sh?

---

### Post by lswest on 2008-05-16
you'll have to do this:
```
cd **/path/to/sh/file**
chmod +x 45-i686-pc-linux-gnu.sh
sh ./45-i686-pc-linux-gnu.sh
``` where "**/path/to/sh/file**" is the actual path (just replace it with your path to the script)

however, i recommend installing from the repositories

---

### Post by alanw8@oh.rr.com on 2008-05-17
Thanks all. I got it. Alan

---

