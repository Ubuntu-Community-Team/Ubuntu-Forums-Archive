---
title: "no RAID disks..."
date: 2007-09-17
forum: General Help
---

### Post by 1234five on 2007-09-17
Yeah, I got this no RAID disks thing as a problem, so I tried re downloading Wubi, but that didn't help... It would be nice if someone could help me since I'm really not good at this kind of stuff...

---

### Post by ago on 2007-09-18
> **1234five said:**
> Yeah, I got this no RAID disks thing as a problem, so I tried re downloading Wubi, but that didn't help... It would be nice if someone could help me since I'm really not good at this kind of stuff...

no raid disk is not an error, it's an information message: "no raid detected"

Normally, if you have an error you should see a prompt and there you should type

more /tmp/zenigata.log
more /tmp/lupin.log

---

### Post by 1234five on 2007-09-18
I tried typing it but nothing happened, and if I let it sit like that for a few minutes it comes up with "ALERT! DOES NOT EXIST!" and something about "creating shell"...

---

### Post by killaboi on 2007-09-18
yea me too please help asap

---

### Post by 1234five on 2007-09-18
> **ago said:**
> no raid disk is not an error, it's an information message: "no raid detected"

Normally, if you have an error you should see a prompt and there you should type

more /tmp/zenigata.log
more /tmp/lupin.log

Ok, I tried it again and it said "dropping into shell" and gave me a prompt. I put in more /tmp/lupin.log and more /tmp/zenigata.log but it said that neither existed...

---

### Post by 1234five on 2007-09-18
I think I spelled "zenigata" wrong earlier. Here's what it said, but /tmp/lupin.log came up with a ton of errors or something. I'm not real good at this kind of stuff, but here

more /tmp/zenigata.log
+PREREQ=
+ROOTMNT=/root
+HOSTMNT=/media/host
+HOSTFOLDER=
+ISOMNT=/cdrom
+HOSTKEY=
+SUITE=
+DEFAULTSUITE=feisty dapper unstable testing stable
+SETUP_INIT=busybox init
+SETUPISO=
+ROOTIMG=system.virtual.disk
+HOMEIMG=home.virtual.disk
+SWAPIMG=swap.virtual.disk
+EXTRAIMG=extra.virtual.disk
+USRIMG=programs.virtual.disk
+DUMMYIMG=install.virtual.disk
+ROOTDEV=
+HOMEDEV=
+SWAPDEV=
+EXTRADEV=
+USRDEV=
+DUMMYDEV=
+USEFREESPACE=

---

### Post by ago on 2007-09-19
I'd need some more info... See if the /media/host folder is available (ls /media/host) then copy the logs to there with the command cp. /media/host is C:, so you should be able to submit the logs from windows. If /media/host is not available look for error messages, particularly about problems when mounting "host"

---

### Post by 1234five on 2007-09-19
Alright.... well I have to ask, is there a way to copy all the info there? For this other one I wrote it all down and typed it up again. It sucked.


EDIT: ok then, I'll do that a little later today. I've got some stuff to do first.

---

### Post by 1234five on 2007-09-20
I dunno... I put in Is /media/host and it said it didn't exist, so... yeah...

---

### Post by ago on 2007-09-20
grep -i host /tmp/*.log  | grep -i error

---

### Post by 1234five on 2007-09-20
> **ago said:**
> grep -i host /tmp/*.log  | grep -i error

When I did this I saw parts that said /media/host in the text, but it kept telling me it didn't exist... I also couldn't copy it. Sorry I'm so bad at this:-s

---

### Post by 1234five on 2007-09-21
If I tried re downloading the files giving them more or less space, would that change it? I gave it 15 originally, but if I gave it more or less what would happen?

---

### Post by 1234five on 2007-09-23
Also... I don't know if this is the problem or not, but when my friend and I tried to put Ubuntu on normally (partitioning and w/e) it said I had to run chkdsk /f, and it also says to do that if i try to defrag. Whenever I try to run chkdsk /f, it says another process is not letting it (something along those lines) and asks if it should do it on next startup, so I say yes, but it doesn't ever do it 0_0. Could this be related Ago?

---

