---
title: "Error w/ mounted network drive returning from suspend"
date: 2007-02-19
forum: General Help
---

### Post by jwest21 on 2007-02-19
I recently upgraded to Edgy Ubuntu using gnome and started using amarok 1.4 as my music player.  I am using another computer on my network to hold all my music and mount this drive so that I can stream it with amarok.

I used [http://amarok.kde.org/amarokwiki/index.php/Samba]("http://amarok.kde.org/amarokwiki/index.php/Samba") to configure my mount to work correctly in amarok, using the first option:
```
mount -t smbfs -o fmask=444,dmask=555,guest //server/share /path/to/mount-point

```

Everything works fine until I suspend/sleep my computer.  When it returns amarok is frozen and I no longer have access to my mounted drive.  The only way I've found to fix this is a) restart the computer or b) force kill amarok, unmount the network drive, remount, restart amarok.

Not sure if anyone else is having this problem; maybe even a solution.  Can I possibly put a script in to unmount before sleep and remount after sleep?  Though I'm sure how I would go about this (and I would probably also need to close amarok as well).

Please let me know if you need more information and bear with me, I'm only a few months into linux still :)

---

### Post by jwest21 on 2007-02-19
Guess I'll just have to figure this one out on my own :(

---

### Post by judgekaster on 2007-03-02
> **jwest21 said:**
> Guess I'll just have to figure this one out on my own :(

I'm not sure if you had already this figured out. Anyhow, I had a similar problem and came across your post. My solution was to create a unmount script in /etc/acpi/suspend.d/ and a mount script in /etc/acpi/resume.d/. 

I created the file /etc/acpi/suspend.d/30-smbfs-umount and placed the following:

```

#!/bin/sh

umount -t smbfs -a

```

and created the file /etc/acpi/resume.d/30-smbfs-mount with the following lines:

```

#!/bin/sh

mount -t smbfs -a

```

Works fine now...

---

### Post by legalizemeth on 2007-04-21
Thank you, I had the same problem.  Making those scripts did the trick.

---

### Post by msjacoby on 2007-04-30
Nice solution. I was having the problem that once my system woke up from sleep or suspend, my mounted samba shares would freeze. This solves it. Thanks!

BTW - I'm running Feisty and this works.

---

### Post by finster on 2007-10-21
I'm having similar problems with my laptop under gutsy.

judgekaster - thanks for the scripts - I think they're going to be part of the solution. I was initially having problems with the unmount bit - it was saying "device busy" so I added the "-l" option for lazy unmount.

Another issue was the scripts seem to need a ".sh" extension on the end of them to be run properly by the suspend/resume processes.

The problem I am having now is that when the laptop resumes, the wireless connection hasn't been re-established by the time the mount is executed. I've tried adding a "sleep" to the script but its very hit and miss. Is there any way I can check the wireless link is running before running the mount?

Anybody any ideas?

Thanks.

---

### Post by wsuetholz on 2007-11-30
In cases like that I would add in a ping command to the script that will verify connectivity to your required host before proceeding.  First you might wish to look into either the ifconfig or ip commands to use them to verify that your required interface is up, then run the ping to verify connectivity.

---

### Post by PaganBlasphemy on 2008-02-07
I am having this same problem.  I've tried the suggestions here, at: [http://ubuntuforums.org/showthread.php?t=359548&highlight=hibernation](http://ubuntuforums.org/showthread.php?t=359548&highlight=hibernation) and at: [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/24864](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/24864)

I have it to the point where when I come back from suspend all I have to do is open a terminal and 'sudo mount -a' and everything instantly works again (doing this frequently as this is a laptop which gets the lid closed and moved a lot).  However I had to remove the samba-shares script listed at launchpad.  All of the other scripts and workarounds listed I have installed currently, and none of them individually or in combination restored the mounted network drives.  

I tried to make a shortcut on my toolbar for the mount function, but running it causes no password prompt to show up, running it as 'gksudo mount -a' asks for a password but doesn't actually do anything, it only works when I run it in a terminal.  I've no experiences with scripts but I made one using the template of the other scripts and the command I wanted to run, but nothing came up.  

I could be going about this in entirely the wrong fashion, anyone have any advice on getting /etc/fstab mounted network drives to 're-mount' correctly when resuming from suspend?

UPDATE: I notice that the networked drives are 'broken'  if I switch from my wireless to my wired connection.  I first have to unmount them, and then remount them again from the command line.  It seems to me that this is a fundamental mistake in the way the mounting is handled, as in the network connection should be the thing that triggers mounting and unmounting, rather than the machine suspending, hibernating, and so on.  Since the network connection going down and coming up is the common (and essential) function, it ought to be the function triggering the mounting behavior.  The fact that I suspended, hibernated, or switched network connections is beside the point and should be invisibly repaired from the end users standpoint.

---

