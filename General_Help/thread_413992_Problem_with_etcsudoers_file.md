---
title: "Problem with /etc/sudoers file"
date: 2007-04-19
forum: General Help
---

### Post by bootbat on 2007-04-19
Hi,

I run Edgy. I was attempting to load firestarter at startup. This is what I wanted to do:

> chmod +w /etc/sudoers
echo "$(whoami) ALL= NOPASSWD: /usr/bin/firestarter" >> /etc/sudoers
chmod -w /etc/sudoers

Finally, I thought of adding firestarter to statup sessions with:

> gksudo firestarter --start-hidden

However, right after running "chmod +w /etc/sudoers", I now keep getting the message:

> sudo: /etc/sudoers is mode 0640, should be 0440

I followed [http://ubuntuforums.org/showthread.php?t=411646](http://ubuntuforums.org/showthread.php?t=411646) in an attempt to solve the problem. However, I cannot run in recovery mode as I commented out the recovery mode option under /boot/grub/menu.lst to clear the clutter in the grub menu on this triple boot machine. Now I cannot do anything on the machine. All commands run with sudo in the terminal returns the same error message. I am lost. I searched everywhere to find out a solution for this but found nothing. 

I do not want to install everything all over again. I feel stupid for commenting out grub but can't do much now. Please help me!!

---

### Post by goldaryn on 2007-04-20
Why not boot in using a Live CD, get a root shell, mount the appropriate hard drive, and edit menu.lst back?

g.

---

### Post by bootbat on 2007-04-20
Thanks, I will try that and keep you posted.

---

### Post by ashz on 2007-04-20
look at this one for help...

[http://ubuntuforums.org/showthread.php?t=411646](http://ubuntuforums.org/showthread.php?t=411646)

cheers
ash

---

