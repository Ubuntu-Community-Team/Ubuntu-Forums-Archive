---
title: "Fstab network share mount problem in Feisty"
date: 2007-06-18
forum: General Help
---

### Post by th_11 on 2007-06-18
Hey,
I have a weird problem with my windows shares. I use fstab to mount the network shares so they SHOULD show up even after computer reboot, BUT the problem is that the shares won't work anymore after reboot, I don't get the shortcuts to the shares on my desktop and I can't acces them in anyway.

I can sometimes unmount those "broken" shares using sudo umount /media/sharename, it just takes very long (like 30 seconds) to complete it. And sometimes I just get error message something like "Volume is busy". If I manage to unmount them all, then I can do sudo mount -a and after that those shares works correctly.

Anyway I have now commented all those share lines in /etc/fstab file, so those shares won't  get mounted on reboot. And after the boot I uncomment the lines and I manually do sudo mount -a and everything works correctly. But this is kind of frustrating to do it always manually and I would like to hear is there any solution to make it work correctly without those manual steps?

Here is an example line from the fstab:
//windows/share1 /media/share1 smbfs username=myname,password=mypass,dmask=777,fmask=777 0 0

I have fully updated Feisty with 2.6.20-16 kernel, network is set up manually (not dhcp).

Anybody got any suggestions what to do?

---

### Post by vanadium on 2007-06-18
My samba mount lines look like:

```

//windows/share1 		/media/share1	smbfs	rw,user,noauto,credentials=/home/vanadium/.smbpasswd

```

You obviously want to remove the noauto (or replace it with auto)

I am not sure at all whether your mount line would be at culprit, but you might try my variation. Of course, the samba shares on the server side must have been correctly set up as well.

(You can continue to use your username=myname,password=mypass option. I use a file for the credentials, .smbpasswd, that contains
```

username=vanadium
password=your_passwd

```

---

### Post by th_11 on 2007-06-18
Thanks for the reply vanadium. I tried your fstab variation but still no luck, it behaves just the same.

I was wondering that could it be that fstab file gets executed too early (maybe network is not set up in that case yet) and thats why it fails? Could I maybe adjust fstab file to get executed later on when system boots?

I was thinking that because it all works good if I manually do the sudo mount -a from command line...

---

### Post by phillipgi on 2007-06-18
I've got exactly the same problem; when I run
> sudo mount -a
there aren't any problems, and all is fine.

When the system restarts, the system is not remounted. As with th_11, my share is smbfs, but my fstab looks as follows:
> //media-center/music /media/music smbfs

Any ideas?

---

### Post by th_11 on 2007-06-20
I also tried to with older kernel (2.6.20-15-generic) but still no luck.

Any suggestions?

---

### Post by elev on 2007-09-15
Are you guys running a wifi network?
Because I have a similar problem where fstab is trying to mount a network share but my wifi isn't connected yet.  So, fstab halts the boot process while it is waiting to time out twice, then booting continues. 

Not only  do I have to "sudo mount -a" after I've connected to the wifi network, but my boot-up is at least twice as long right now.

---

### Post by shad0w_walker on 2007-09-15
You should be able to take out the fstab entry and modify a bootup script to mount the share if you know how (I would write up a guide but I'm about 10,000 miles from my Linux desktop right now) so I will just put the idea up and let someone else come along and flesh it out.

Basically you should be able to stick the mount command into a startup script (Its own or modify an existing one, GDM for example) and as the boot scripts are run as root it will mount after your network has been brought up and shouldn't have any problems mounting. If you place the code at the end of a script or in its own (Set to run after all other scripts) then you should also be able to avoid delayed booting as a time out won't stop anything else running.

---

