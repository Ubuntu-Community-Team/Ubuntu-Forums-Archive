---
title: "&quot;Invalid argument&quot; when opening shared folder from Win10"
date: 2016-04-09
forum: General Help
---

### Post by bule2 on 2016-04-09
Hi guys, I'm a new Ubuntu user.I have installed Ubuntu 15.10 on my laptop. I also have a Win10 PC. Now, I've shared some folders on both Ubuntu machine and on Win10 machine. From Win10 I can access -Ubuntu shared folder without any problems. But from Ubuntu I can't access Win10 shared folder. I can see it in Nautilus, but when i try to open it i get this message: [http://imgur.com/712tO7P](http://imgur.com/712tO7P). I have installed Samba but did not configure it much, since I am new to Ubuntu. 

I have turned off Firewall on Windows, also in advanced network settings turned on Sharing. I also gave permissions to Everyone (Full control). My Win10 PC is running while trying to open up shared folder.

I would really appreciate your help.

---

### Post by oldfred on 2016-04-09
Did you leave Windows fast start up on, which is really hibernation?
And Windows leaves all partitions mounted, so any NTFS partition is in hibernated state.

 Fast Startup off/hibernation - Windows 8 or 10 UEFI or BIOS boot.
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)

---

### Post by bule2 on 2016-04-10
Well my Windows PC is not hibernated. It's running and i have my laptop with Ubuntu next to it

---

### Post by oldfred on 2016-04-10
Is this not the same system, or you are really using Samba or network mount?
Do not know about either. 
Probably better if you edit first post and title to clarify, so those that know Samba may reply.

---

### Post by bule2 on 2016-04-14
I have edited my first post, hopefully it gives more information. Bumping for visibility

---

### Post by yancek on 2016-04-14
Have you looked in the /media directory, /media/adrian if that is your user name.  You should see mount points for your other drive partitions there.  Take a look at the owner group as well as permissions or post that info here if you don't understand it.  Get it with:  ls -l /media and ls -l /media/adrian

Do you have an entries in /etc/fstab for the windows partitions?

---

### Post by bule2 on 2016-04-15
Hi, thank you for replying.
I have checked in my media/adrian folder and it is empty (unless I plug in USB device).

Regarding owner group and permissions I've entered commands in terminal and this is what I've got [http://imgur.com/rINyBTc](http://imgur.com/rINyBTc)

Now in fstab I really don't know what to look for so here is another screenshot: [http://imgur.com/YlqbAEn](http://imgur.com/YlqbAEn)

---

### Post by yancek on 2016-04-15
Since you are connecting the two computers to share on a local network, you will need to use samba and configure that.  I don't use it so have no idea how or what to do.  You might use the search function at the forums to search for configuring samba.

---

### Post by bule2 on 2016-04-15
Ok I will definetly do that. Thank you for all help.

---

