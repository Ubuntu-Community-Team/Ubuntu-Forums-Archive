---
title: "What's up with WINE?"
date: 2005-10-01
forum: General Help
---

### Post by Sirin on 2005-10-01
Every time I use WINE with a Windows Application, it suddenly increases the ram hold to over 1GB. I had to reinstall Ubuntu all over again just to get back on my feet, but I want to know if there's any problem with WINE or is there any solution to this problem, or what?

---

### Post by aysiu on 2005-10-07
I've never heard of this problem before. I can only assume it has something to do with the kinds of Windows applications you're opening. Did a reinstall fix the problem?

---

### Post by Joeb on 2005-10-07
[QUOTE=Sirin]Every time I use WINE with a Windows Application, it suddenly increases the ram hold to over 1GB. I had to reinstall Ubuntu all over again just to get back on my feet, but I want to know if there's any problem with WINE or is there any solution to this problem, or what?[/QUOTE]

I am using Wine without the problems you are indicating.  Did you install it from the repository, compile it yourself or install it from some other source?  I only ask because maybe if you didn't use the Ubuntu repository, some bug has been introduced.

Regardless, you shouldn't have to re-install Ubuntu.  At worst a reboot, but before that, I would open a terminal and do a top command to see if any wine processes are still running and then kill them.

---

### Post by Sirin on 2005-10-10
[QUOTE=Joeb]I am using Wine without the problems you are indicating. Did you install it from the repository, compile it yourself or install it from some other source? I only ask because maybe if you didn't use the Ubuntu repository, some bug has been introduced. Regardless, you shouldn't have to re-install Ubuntu. At worst a reboot, but before that, I would open a terminal and do a top command to see if any wine processes are still running and then kill them.[/QUOTE]
 First I installed it with a package from their site. It then rendered my computer down to a turtle-like speed, but then I could'nt find a way to uninstall it. So then I did it, a complete reinstall of Ubuntu :(. Then after, I did it from Synaptic. After trying that version, same problem: 1GB RAM hold. I had to reboot my syste in that case. I'll give you a screenshot of the system monitor with how much It's running. By the way, I only have 248MB Physical RAM, and 740MB Virtual (Swap) RAM. 
[QUOTE=aysiu]I've never heard of this problem before. I can only assume it has something to do with the kinds of Windows applications you're opening.[/QUOTE] It did it on [Saint Paint Studio]("http://www.saintpaint.com/SPWeb/spscreenshot.jpg") <-Screenshot (It is not as heavy as it seems. On Windows, it took up only 4MB of RAM.)

 EDIT: Here is s screenshot. Notice Wine running at a hefty 1.4GBs of RAM.

[[IMG]http://img415.imageshack.us/img415/4042/snapshot16rj.th.png[/IMG]](http://img415.imageshack.us/my.php?image=snapshot16rj.png)

---

### Post by Sirin on 2005-10-14
Well, since nobody's interested in fixing this problem... :rolleyes:

---

