---
title: "windows network problem!"
date: 2007-10-31
forum: General Help
---

### Post by lattmau on 2007-10-31
i have 2 windows xp machines networked through a router and both computers can see each other fine and share files and such.

i have a 3rd machine that i installed ubuntu 7.10 and it is also connected to the router.  on the ubuntu machine, i can see both xp machines and access files fine, but the xp machines can't see the ubuntu machine.

i installed SMB and through the shared folders dialouge i designated a shared folder and entered the same  workgroup name as the xp machines.  but xp machines still don't see the ubuntu machine

am i missing something? 

also, how can i check what computer name the windows machines would see my ubuntu machine as?

---

### Post by scrooge_74 on 2007-10-31
Are you running a firewall? Check this for some ideas.

[http://www.ubuntuforums.org/showthread.php?t=190542&highlight=open+port+138](http://www.ubuntuforums.org/showthread.php?t=190542&highlight=open+port+138)

The name they would see is the name you gave the your Linux box, you can also check the smb.conf file in /etc/samba for the name

---

### Post by lattmau on 2007-10-31
I just installed Ubuntu on the machine and I haven't set up any firewalls.  The XP machines both have Zone Alarms but I have allowed a Trusted IP Range (includes the ubuntu machine).  

Is there another way to check what name I gave to my linux box w/o going to smb.conf?

---

### Post by scrooge_74 on 2007-10-31
Well if you just open a terminal the name of the machine should be there, in mine it says:

juan@nx6110:~$

been nx6110 the name of the machine, which in my case I choose at install time, plus you can find it also in a file in /etc/hostname

---

### Post by lattmau on 2007-10-31
> **scrooge_74 said:**
> Well if you just open a terminal the name of the machine should be there, in mine it says:

juan@nx6110:~$

been nx6110 the name of the machine, which in my case I choose at install time, plus you can find it also in a file in /etc/hostname

oh ok, thanks


any ideas about the network problem?

---

### Post by scrooge_74 on 2007-10-31
Check [this]("https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto") also can give you clues

---

