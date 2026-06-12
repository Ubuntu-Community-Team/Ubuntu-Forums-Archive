---
title: "Ubuntu freezes at startup when external USB hard disk is connected"
date: 2007-06-10
forum: General Help
---

### Post by trevoore on 2007-06-10
Hi!

I'm pretty much a beginner,  and I'm having lots of fun with Ubuntu.
One problem remains, though: I can't start when I have my external USB hard drive connected.  The computer freezes at the "starting up..." screen. 
I think I saw this problem somewhere in the forum, but I can't find it.

Any suggestions?

Cheers,
t

---

### Post by hotweiss on 2007-09-29
I have the same problem. Any solution out there?

---

### Post by chunchengch on 2007-09-29
What is the content of this external USB hard drive?

---

### Post by FuturePilot on 2007-09-29
I have this problem too. Although it only happens with USB flash drives. It's fine with my USB hard drive.

---

### Post by hotweiss on 2007-09-30
> **chunchengch said:**
> What is the content of this external USB hard drive?

Three of them are NTFS and one is ext3. I'm in the process of slowly converting all of my data into ext3. Do you think that will fix the problem?

---

### Post by hotweiss on 2007-09-30
Well the culprit seems to be the Seagate FreeAgent. I'm going to exchange it for a Vantec enclosure and hard drive tomorrow.

---

### Post by hotweiss on 2007-09-30
The culprit wasn't the FreeAgent, the problem is occurring with the new drive also. One thing I noticed is that if I unplug the drive at start up and then plug it in when Ubuntu starts the drive gets recognized. Either than that if it some how Ubuntu does boot up with it connected, it does not get recognized by Ubuntu.

---

### Post by hotweiss on 2007-09-30
OK, I exchanged my last SATA drive for an IDE drive and yet the problem persists. Although I did notice that when three drives (what ever the combination) are on, they all boot up, but when you add a fourth one, GRUB freezes.

---

### Post by hotweiss on 2007-09-30
Bump, this is a serious issue.

---

### Post by hotweiss on 2007-09-30
OK, this problem has been solved in my case. I can't have more than 4 drives connected at startup. It seems to be a BIOS bug, as I reproduced the same error after installing Windows XP Pro, the computer freezes right at the beginning. Oh boy, time to intall Ubuntu AGAIN. I'm sorry for even thinking of blaming Ubuntu, lol.

---

