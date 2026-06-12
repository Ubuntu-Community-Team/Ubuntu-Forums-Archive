---
title: "AHHH! I Destroyed My ubuntu! HELP!!!"
date: 2007-12-03
forum: General Help
---

### Post by Black Mage on 2007-12-03
Well I can't log in. I was backing up my hard drive by copying the /home folder onto an external hard drive. While doing so, I suddenly lost access to any sudo commands. And then I restart my Ubuntu and it says I can't log in because I'm out of memory or the user files cannot be written too.

Does anyone know how I can fix this? Help wold be much appreciated.

Thnx.

---

### Post by Billy_McBong on 2007-12-03
if you have your /home backed up to an external HDD you could just reinstall Ubuntu without data loss

P.S. the cafe isn't a support section

---

### Post by Black Mage on 2007-12-03
No, not everything is there. I need to get back into it.

---

### Post by blithen on 2007-12-03
> **Billy_McBong said:**
> 
P.S. the cafe isn't a support section
+1

Also You might have just moved(instead of copied) your home folder to your external hard drive. Try copying the home folder back to it's normal spot.....nevermind.

---

### Post by Crashmaxx on 2007-12-03
Make sure you didn't have the disk become unmounted and have it try to write to the main disk instead.

Also, make sure you didn't try to copy the directory you are backing up, causing a loop that will fill the disk infinitely.

---

### Post by xinix111 on 2007-12-03
just login with your live cd, add a diskmounter to your pannel, mount your disks and save your ****!!  goodluck!!

---

### Post by Black Mage on 2007-12-03
WOOT!! It worked. I just need one thing. Where is the directory where evolution stores the mail?

---

### Post by -grubby on 2007-12-03
probably somewhere in /home/username/.evolution

---

### Post by Black Mage on 2007-12-03
alright, so a sudo ls then?

---

### Post by akiratheoni on 2007-12-03
> **Black Mage said:**
> alright, so a sudo ls then?

For /home/username/.evolution? Nope, it's your own file so sudo is not needed.

---

### Post by Black Mage on 2007-12-03
But on the live CD, isnt it no longer my file?

---

### Post by Sef on 2007-12-03
Moved to General Help.

---

### Post by Crashmaxx on 2007-12-05
True, and remember that, but ls shouldn't need root privileges anyway since nearly all files are at least read only to everyone and ls just reads them. To modify them, you may need sudo, to copy them, probably not, to move them, most likely.

---

