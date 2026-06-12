---
title: "samba with no username and password"
date: 2007-03-27
forum: General Help
---

### Post by closeyourwindows on 2007-03-27
Hi.  I have 25 computers that run XP and I use my Ubuntu as a workstation/server.  I have all computers mapped to a shared drive where I store files, executables and more.  Everytime I restart an XP computer I have to re-login to the samba computer.  I dont need security on these computers as they dont access the internet and young kids are on the other ends of the xp machines.  How do I set up the smb.conf to no security so that I do not have to use a username and password to access this?
by the way I used an XP machine at first but only 12 machines can be accessed at the same time.  Ubuntu will let all 25 machines login at the same time with minimal delay.:)

---

### Post by dcstar on 2007-03-27
> **closeyourwindows said:**
> 
.........
by the way I used an XP machine at first but only 12 machines can be accessed at the same time.  Ubuntu will let all 25 machines login at the same time with minimal delay.:)

XP has a software limit on simultaneous connections (even though it uses a lot of Server 2003 code and can handle the load) - I believe that a Registry tweak can bypass it.

Microsoft limits a lot of features in XP, I actually have patched a few files and now can use Volume Mirroring on XP.........    :)

---

### Post by pepa on 2007-03-27
Hi there,

I've had the same issue before, checkout this site it solved all my samba problems.

(I'm assuming you are using edgy?)


[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server)

---

### Post by closeyourwindows on 2007-03-28
Thanks for the last reply and seems to work.
I dont want to tweak xp because I really like having a ubuntu computer in the lab.

---

