---
title: "time problem breaks su?"
date: 2006-11-28
forum: General Help
---

### Post by pseudo_nz on 2006-11-28
I'm running Kubuntu (Dapper) on a Compaq Presario laptop, and everything has been running fine - until I noticed the time was wrong.  If I reset it, then it stays right, but I can no longer log in as root - a popup box tells me tells that 'conversation with su failed'.  I was still able to log in through a terminal to load whatever, until today.

Today when I booted the time was out again, but when I went to log in as root I got:

pseudo@pseudo-laptop:~$ sudo gksu time-admin
sudo: timestamp too far in the future: Nov 29 01:12:41 2006

I've checked the other threads about su failing, and checked /etc/sudoers.  It's still set to pseudo ALL=(ALL) ALL but I can't sign in anywhere.

Any help would be appreciated.

---

### Post by halfvolle melk on 2006-11-28
Do you dual boot? This cause a problem if the one OS writes local time to the BIOS and the other writes UTC. Ubuntu manages this in /etc/default/rcS and is by default set to UTC=yes. If for instance you dual boot with Windows, which I believe uses local, change it to UTC=no.

---

### Post by RAOF on 2006-11-28
You can try "sudo -K", which **should** clear the timestamp (which lets you use sudo without entering a password if you've entered the password 15min before).

---

### Post by jazzgossen on 2006-11-28
It might be a problem with the timestamp of your files. You could check to see if any files in your home directory or in /root have wrong time stamps.

---

### Post by pseudo_nz on 2006-11-29
Thanks guys.  I'm not running a dual boot system, but it never occurred to me to check the BIOS (duh!).  It was set wrong, so I changed it and it seems to have worked, although I haven't rebooted yet to find out (working on the 'if it ain't broke' train of thought).  If it doesn't work, I'll definitely try your suggestions, and let you know how it goes.

---

