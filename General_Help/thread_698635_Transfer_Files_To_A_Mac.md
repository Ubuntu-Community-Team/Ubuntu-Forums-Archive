---
title: "Transfer Files To A Mac"
date: 2008-02-16
forum: General Help
---

### Post by dethredic on 2008-02-16
Hi, I have some files on my desktop (Linux) and I need to transfer them to my macbook.

How can I do this?

---

### Post by aashay on 2008-02-16
usb thumbdrives?

---

### Post by dethredic on 2008-02-16
I need to transfer over 30 gigs, that will take to long

---

### Post by aashay on 2008-02-16
How about getting a crossover cable to connect the computers.

---

### Post by dethredic on 2008-02-16
We don't own one. ( I assume you mean USB to USB ) We are connected via eathernet though.

---

### Post by aashay on 2008-02-16
The crossover cable is used to connect two computers via their ethernet ports. But since you mention you are already connected, and I have no idea how networking / file sharing on a mac works. I'd suggest, off the top of my head, to host a ftp server on the desktop and  connect to it using the macbook. Not very sophisticated, but would get things done

---

### Post by dethredic on 2008-02-16
Is there a quick and simple tutorial to show me how to do that?

I saw for a quick simple ftp server just do this:
> sudo apt-get install proftpd gproftpd
So, I did that, but now what?

---

### Post by farruinn on 2008-02-16
Easiest solution: turn on FTP or Remote Login on the Mac (Preferences > Sharing). Then connect to it from the PC and copy it that way. If you use Remote Login (SSH) you should be able to use sftp to connect.

---

### Post by aashay on 2008-02-16
[http://ubuntuforums.org/showthread.php?t=91887](http://ubuntuforums.org/showthread.php?t=91887)

---

### Post by dethredic on 2008-02-16
> **farruinn said:**
> Easiest solution: turn on FTP or Remote Login on the Mac (Preferences > Sharing). Then connect to it from the PC and copy it that way. If you use Remote Login (SSH) you should be able to use sftp to connect.

That worked great! Thanks!

---

