---
title: "configured multiple times"
date: 2018-09-24
forum: General Help
---

### Post by jgw on 2018-09-24
I am getting the 'configured multiple times" error on two files:
/etc/apt/sources.list:40 and /etc/apt/sources.list.d/vivaldi.list

there are files listed in the sources.list but vivaldi.list has:
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://repo.vivaldi.com/stable/deb/](http://repo.vivaldi.com/stable/deb/) stable main

I have noticed that when the configured multiple times thing come up the solution seems to be to delete a file out of /etc/apt/sources.list.d so, should I delete the vivaldi.list file (contents above)?

this started when running "sudo apt update" when it got to (I can post the whole thing if you wish):
Building dependency tree       
Reading state information... Done
67 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list.d/vivaldi.list:3


Thank you...................

---

### Post by ajgreeny on 2018-09-25
Yes, I suggest you remove that /etc/apt/sources.list.d/vivaldi.list file (temporarily if you prefer, just in case) then run **sudo apt update** again to see if the error goes away; I think it will.

Alternatively you can just comment out the vivaldi line in **/etc/apt/sources.list** by putting a # at the front of it.  Don't do both or you will lose the vivaldi repos completely.

---

### Post by jgw on 2018-09-25
Thanks for the reply.
first I tried to rename the files and got:
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list.d/Xvivaldi.list:3
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list.d/Xvivaldi.list:3

Now I will just delete them.  Removed the files - the errors went away.  

Oh, strange thing.  I can normally do sudo apt nautilus to get to super use and do stuff.  This time it wouldn't work.  Then I did an SU and then ran nautilus.  It ran but the cursor disappeared so I just used rm.  Still, not behaving as it used to.  Given that I am getting upgrades every day (today its 25, yesterday more), on basically the same stuff (no errors on upgrades) I suspect folks are working on it.

Thanks again!

---

### Post by ajgreeny on 2018-09-25
I am not sure what you think the command ```
sudo apt nautilus
``` does, but if you believe that is how to open nautilus with root permissions, I'm afraid it is not.  I am also not sure what you mean by **Then I did an SU and then ran nautilus.** as command SU will do nothing in Ubuntu; did you simply mean that you did it as superuser in some way, and if so, how did you do that?

If possible, I recommend you use the terminal to carry out operations on system files, but back up files first with ```
sudo cp /path/to/file /path/to/file-backup
``` and do so only when you know exactly what you're doing and why or you could easily totally kill your operating system.

---

### Post by jgw on 2018-09-26
Thank you for the reply............

I have no idea why I said "sudo apt nautilus" and have no idea what that would do.  However, I do use "sudo nautilus" which works.  There used to be gksu but that went away.  I have also used gksudo but that too has gone away, or needs to be installed.  SU makes me a super user until exited and is a standard command (needs to be setup first)  These are all terminal commands.

---

### Post by ajgreeny on 2018-09-26
> **jgw said:**
> Thank you for the reply............

I have no idea why I said "sudo apt nautilus" and have no idea what that would do.  However, I do use "sudo nautilus" which works.  There used to be gksu but that went away.  I have also used gksudo but that too has gone away, or needs to be installed.  SU makes me a super user until exited and is a standard command (needs to be setup first)  These are all terminal commands.

Yes, I know they are all terminal commands, but I will now say what I have said to many other users, NEVER use sudo for a GUI application.

You may get away doing so with some GUI apps but there is a very real possibility that doing so with nautilus, in particular, will eventually lock you out of your own system by changing ownership of files and folders in your home to root.  You would then have to boot to a live system or recovery mode to change ownership back to your user.

If you want to use a GUI app such as gedit to edit a file use command **sudo -H gedit** or **sudo -H nautilus** as that avoids the ownership change possibilities.

Incidentally, have you set an alias for SU to give you root or superuser permissions or have you set up the root account, which is disabled by default in Ubuntu and frowned upon by this forum?

---

