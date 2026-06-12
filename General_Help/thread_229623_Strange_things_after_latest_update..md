---
title: "Strange things after latest update."
date: 2006-08-04
forum: General Help
---

### Post by z-vet on 2006-08-04
Latest KDE and kernel update did a strange things to my installation: 
1. kpersonalizer runs on every restart - how to disable?
2. root filesystem mounts as read-only. It causes problems running apps as root: trying to run Kate shows warnings about unability to write config files since root filesystem mounted read-only and crashes Kate. Same with KWrite... I edited /grub/menu.lst to read
```
kernel	/vmlinuz-2.6.15-26-686 root=/dev/hda1 rw
```
and it works (no errors or crashes anymore), but how did it worked before? I checked menu.lst on another (not yet updated) machine and it says "ro" in kernel parameters. I don't get something here... :confused:

---

### Post by MarinaraOfDeath on 2006-08-04
I cannot suggest any detail or solutions, but I agree. Something in the last batch of updates completely broke tetex and lyx, so badly that I'm going to write my thesis in texniccenter in XP. Both fail to compile their files, claiming that they cannot write to the drive the files are housed on *even though the permissions on those partitions and all file thereon are 777*. A complete removal and reinstall did nothing.

I am rapidly getting pissed off with updates breaking everything that worked so well previously, especially since there's no way to tell what broke what. (Rolling back and installing one by one is not an option when 50 things update at a time and I have a deadline bearing down. And it should never be the user's duty to do that anyways.)

---

### Post by mexlinux on 2006-08-07
I also got the kpersonalizer issue, if you found a solution, please post it.
Thanks,
Miguel

---

### Post by Firetech on 2006-08-08
> **mexlinux said:**
> I also got the kpersonalizer issue, if you found a solution, please post it.
Thanks,
Miguel

Try the following, it helped me:
[LIST=1]
[*]Click K-menu > Run Command... (Or press Alt+F2.)
[*]Type the following into the box:
```

kate ~/.kde/share/config/startupconfig

```
[*]Click on Run. (Or press Enter...)
[*]Edit the line that says:
```

kpersonalizerrc_general_firstlogin="true"

```
Change it to say the following instead:
```

kpersonalizerrc_general_firstlogin="false"

```
(Change "true" to "false")
[*]Logout and login again.
[/LIST]

**If it didn't help**, try *redoing* the above steps *except 5.(Logout and login again)* and then do this (I'm not sure about this because the above stuff worked for me):
[LIST=1]
[*]Click K-menu > Run Command... (Or press Alt+F2.)
[*]Type the following into the box:
```

kwriteconfig --file kpersonalizerrc --group General --key FirstLogin false

```
[*]Click on Run. (Or press Enter...)
[*]Logout and login again.
[/LIST]

**NOTE!**
The reason I'm not sure about the second part is because the file in question doesn't exist on the "offending" computer (my laptop, running a fresh Dapper with KDE 3.5.4), but it does on this one (my desktop, running a Dapper (also with KDE 3.5.4) upgraded via Breezy from Hoary), and I found a post in Kubuntu Forums from a guy for whom the change from the first part here was reverted on reboot. If the first part doesn't work, try the second part, it should do no harm, but it might not solve the problem.

---

### Post by Firetech on 2006-08-08
> **z-vet said:**
> 
2. root filesystem mounts as read-only. It causes problems running apps as root: trying to run Kate shows warnings about unability to write config files since root filesystem mounted read-only and crashes Kate. Same with KWrite... I edited /grub/menu.lst to read
```
kernel	/vmlinuz-2.6.15-26-686 root=/dev/hda1 rw
```
and it works (no errors or crashes anymore), but how did it worked before? I checked menu.lst on another (not yet updated) machine and it says "ro" in kernel parameters. I don't get something here... :confused:

You should never change the "ro" parameter to "rw". Reason?

[QUOTE=http://www.cyberciti.biz/nixcraft/vivek/blogger/2006/03/10-boot-time-parameters-you-should.php]
ro
This argument tells the kernel to mount root file system as read-only. _This is done so that fsck program can check and repair a Linux file system._ Please note that you should _never ever_ run fsck on read/write file system.
[/QUOTE]

After the fsck check, the system will remount the filesystem as read & write, if I understand things correctly.

However, the root file system is by default told in /etc/fstab to remount read-only on error (at least for ext3, "errors=remount-ro"), which might be your problem. To check for errors on your root fs, do the following:
[LIST=1]
[*]Make **sure** your kernel will boot with "ro" and **not** "rw"! (I.E. Revert your previous change.)
[*]Start Konsole (if not already running)
[*]Type in the following command (and press Enter afterwards): 
```

sudo touch /forcefsck

```
(If you're asked for a password, enter your normal login password)
[*]Reboot
[/LIST]

---

### Post by z-vet on 2006-08-08
> **Firetech said:**
> Try the following, it helped me:
[LIST=1]
[*]Click K-menu > Run Command... (Or press Alt+F2.)
[*]Type the following into the box:
```

kate ~/.kde/share/config/startupconfig

```
[*]Click on Run. (Or press Enter...)
[*]Edit the line that says:
```

kpersonalizerrc_general_firstlogin="true"

```
Change it to say the following instead:
```

kpersonalizerrc_general_firstlogin="false"

```
(Change "true" to "false")
[*]Logout and login again.
[/LIST]

**If it didn't help**, try *redoing* the above steps *except 5.(Logout and login again)* and then do this (I'm not sure about this because the above stuff worked for me):
[LIST=1]
[*]Click K-menu > Run Command... (Or press Alt+F2.)
[*]Type the following into the box:
```

kwriteconfig --file kpersonalizerrc --group General --key FirstLogin false

```
[*]Click on Run. (Or press Enter...)
[*]Logout and login again.
[/LIST]

**NOTE!**
The reason I'm not sure about the second part is because the file in question doesn't exist on the "offending" computer (my laptop, running a fresh Dapper with KDE 3.5.4), but it does on this one (my desktop, running a Dapper (also with KDE 3.5.4) upgraded via Breezy from Hoary), and I found a post in Kubuntu Forums from a guy for whom the change from the first part here was reverted on reboot. If the first part doesn't work, try the second part, it should do no harm, but it might not solve the problem.

Or you can just do
```
cp /usr/share/kubuntu-default-settings/kde-profile/default/share/config/kpersonalizerrc ~/.kde/share/config
```

---

