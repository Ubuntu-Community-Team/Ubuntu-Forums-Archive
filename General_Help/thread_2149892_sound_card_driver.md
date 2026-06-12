---
title: "sound card driver"
date: 2013-05-30
forum: General Help
---

### Post by Anoop Jose on 2013-05-30
How to install a realtek audio driver in ubuntu 12.04?
when i use my 5.1 speakers along with ubuntu , and if i test it in audo it detects only two of them. how to solve it?

---

### Post by Charlotte18 on 2013-05-30
Take a look at the link below, particularly the section "Enabling surround sound in libraries":

[https://help.ubuntu.com/community/SurroundSound](https://help.ubuntu.com/community/SurroundSound)

---

### Post by Mark Phelps on 2013-05-30
> **Anoop Jose said:**
> How to install a realtek audio driver in ubuntu 12.04?

Where did you get the drivers?  

If these are on a CD that came with a sound card, they are most likely MS Windows drivers -- and you can't install or use them in Ubuntu.

---

### Post by Anoop Jose on 2013-05-31
i got it downloaded from realtek website. they says its for ubuntu

---

### Post by Charlotte18 on 2013-06-01
If your sound is working but only using two channels, then you may not have a driver issue. Have you tried editing the sample channels digit in /etc/pulse/daemon.conf?

---

### Post by Mark Phelps on 2013-06-01
> **Anoop Jose said:**
> i got it downloaded from realtek website. they says its for ubuntu

Actually, what I saw the other day said they were for Linux ...

Also, there are two very different sets of drivers: (1) HD Audio, (2) AC'97.  You need to be sure you downloaded the ones for your hardware.  The wrong ones will not work.

---

