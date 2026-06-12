---
title: "xubunto and xp network"
date: 2007-10-29
forum: General Help
---

### Post by odindio on 2007-10-29
just want to be able to network my xubunto pc with my windows pc. Currently windows can see xubunto shared files. But how do I get xubunto to see shared files and printers on my xp machine? I don't need samba? do I? If so, do I download samba from somewhere?

---

### Post by stump138 on 2007-10-29
make sure that you have the permissions set right on the windows box, then you can open a file browser and try this

smb://ip.to.your.windows.box

---

### Post by odindio on 2007-10-29
I'm not sure what you mean by windows box and file browser?  Xubunto has terminal, thunar file manager, and under system it has network.

---

### Post by airtonix on 2007-10-29
Ok, having found the [B]System -> Network

[/B]Did you set it up?

From that point you neet to Investigate install [B]SMBFS

[/B]start here : 

+ [http://www.xubuntu.org/](http://www.xubuntu.org/)
+ [http://ubuntuforums.org/showthread.php?t=588737&highlight=smbfs](http://ubuntuforums.org/showthread.php?t=588737&highlight=smbfs)
+ [http://ubuntuforums.org/showthread.php?t=71753&highlight=smbfs](http://ubuntuforums.org/showthread.php?t=71753&highlight=smbfs)
+ [http://ubuntuforums.org/showthread.php?t=455972&highlight=smbfs](http://ubuntuforums.org/showthread.php?t=455972&highlight=smbfs)
+ [http://ubuntuforums.org/showthread.php?t=255872&highlight=smbfs](http://ubuntuforums.org/showthread.php?t=255872&highlight=smbfs)
+ [http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)

---

### Post by odindio on 2007-10-29
Could someone please help with my netorking issue?  This is a simple situation with a simple fix.  I could use some help.  Please:)

:confused:This last guy that posted is not trying to help, first on all - I have xubunto installed already, so ubunto is not an option right now.  Second of all microsoft doesn't care about my situation.  And I don't really have the inclination to petition microsoft.  I do understand plenty about computer basics - just not linux.  If I knew linux, I wouldn't be asking for help.

---

### Post by odindio on 2007-10-29
now your helping:) thanks - Yes I've done that. And I've looked on the internet alot already.

---

### Post by odindio on 2007-10-29
Oh! that's pretty odd how you edited your thread like that, so nobody knows what was said initially.   I'll have to look at those threads.  But I do seem to find everything but the answer to my problem.

---

### Post by stump138 on 2007-10-29
Sorry if I seemed cryptic.

What I meant is that on the computer running windows you have set the files up to be shared.  If you have not set the files or drive to be shared, you won't see them when you connect.

Yes, file browser in your case will be Thunar

First do this

1.  On the windows computer open a command prompt "start->run" then type "cmd" and hit enter

2.  Once the command prompt is opened, type  "ipconfig" and hit enter.  It will give you some information.  In this case you are interested in the IP address.  It will most likely be something like 192.168.0.1

3. Go to your xubuntu machine and open thunar, enter  "smb://ip.address.you.got.from.the.windows.computer"
and hit enter.  That should open the windows computer for you to see the shared folders.

---

### Post by odindio on 2007-10-29
they are shared files.  Thunar doesn't have a command line (that I know of).  I typed smb://192.168.1.4 into the terminal.  It doesn't recognize this.

---

### Post by maybeway36 on 2007-10-29
Thunar does not work with SMB. Either use smbfs/cifs or install a SMB client (such as the KDE file manager, Dolphin.)

---

