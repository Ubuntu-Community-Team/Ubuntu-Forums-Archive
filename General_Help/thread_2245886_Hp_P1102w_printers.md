---
title: "Hp P1102w printers"
date: 2014-09-26
forum: General Help
---

### Post by TheTinyt1 on 2014-09-26
I have a ASUS 4 Core desktop and running Kubuntu [FONT=sans-serif, Tahoma, Calibri, Verdana, Geneva][COLOR=#000000]KDE SC Version 4.13.3. I just got this P1102w printer for my b-day and wanted to get it up and running. HP printers have never given me a problem before now. However, this printer is not printing. [/COLOR][/FONT]

[FONT=sans-serif, Tahoma, Calibri, Verdana, Geneva][COLOR=#000000]When I went into settings and the printer was automatically detected and I tried the alternative driver and still not good. 
The print Que says that there is a filter error. I tried to down load the  file [/COLOR][/FONT]hplip-3.14.6.run but can not get it to run?
Then I down loaded foo2zjs.tar.gz and went though the install and all I get is program not found, etc. 

So what do you suggest?

It also seem that I can not access that root either and this may be a problem. though I am the only one on this machine and use the admin password every time.

---

### Post by buzzingrobot on 2014-09-26
It needs an HP proprietary driver, which isn't in the Ubuntu repos (or anyone's repo, as far as I know).

Install "hplip-gui", which is in the repos, and run it.(Look for a pretty obvious "HP" icon/menu item.)  It will detect your printer, download and install the driver, and setup the printer. When you're satisfied it's working, go back to Ubuntu's Printer applet and be sure it is set as the default.

---

### Post by TheTinyt1 on 2014-09-27
Thanks you for the help it did work great. I have the printer up and running thanks to you.

However, just in case someone else reads this post and does not know exactly how to down load and install this, I got this off of another post and will copy here for quicker reference.  

[COLOR=#000000][[COLOR=#000000]daniell59[/COLOR]]("http://ubuntuforums.org/member.php?u=492861") 
[IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG]**Skinny Soy Caramel Ubuntu****[IMG]http://ubuntuforums.org/images/rank_21.png[/IMG]**


[RIGHT]Join DateJan 2008Beans690[/RIGHT]

[/COLOR]
[COLOR=#000000][h=2]Re: Problem installing HPLIP[/h][INDENT]Someone on the HP Linux Imaging and Printing site helped me. The following commands in the terminal did it.

=> Reconfigure print queue using below commands.
=> hp-setup -r (remove all print queues)

=> sudo hp-plugin (This will download right plugin)

=> hp-setup



again many thanks...[/INDENT]


[/COLOR]

---

