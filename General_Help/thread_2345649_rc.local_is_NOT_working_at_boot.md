---
title: "rc.local is NOT working at boot"
date: 2016-12-06
forum: General Help
---

### Post by satimis on 2016-12-06
Hi all,

Host - Ubuntu 16.04
VM - Ubuntu 16.04
VirtualBox

/etc/rc.local is NOT working.

&#10219; sudo systemctl status rc-local```

&#9679; rc-local.service - /etc/rc.local Compatibility
   Loaded: loaded (/lib/systemd/system/rc-local.service; static; vendor preset: 
  Drop-In: /lib/systemd/system/rc-local.service.d
           &#9492;&#9472;debian.conf
   Active: failed (Result: exit-code) since Wed 2016-12-07 00:05:27 HKT; 14min a

Dec 07 00:05:27 ub1604dkpc101 systemd[1]: Starting /etc/rc.local Compatibility..
Dec 07 00:05:27 ub1604dkpc101 rc.local[1179]: /sbin/mount.vboxsf: mounting faile
Dec 07 00:05:27 ub1604dkpc101 systemd[1]: rc-local.service: Control process exit
Dec 07 00:05:27 ub1604dkpc101 systemd[1]: Failed to start /etc/rc.local Compatib
Dec 07 00:05:27 ub1604dkpc101 systemd[1]: rc-local.service: Unit entered failed 
Dec 07 00:05:27 ub1604dkpc101 systemd[1]: rc-local.service: Failed with result 

```

sudo sysv-rc-conf
(please see attached screenshot)

Have tried advice on following link without result;
Why is the command in /etc/rc.local not executed during startup?
[http://askubuntu.com/questions/299792/why-is-the-command-in-etc-rc-local-not-executed-during-startup](http://askubuntu.com/questions/299792/why-is-the-command-in-etc-rc-local-not-executed-during-startup)

Found another doc;
How to Enable /etc/rc.local with Systemd
[https://www.linuxbabe.com/linux-server/how-to-enable-etcrc-local-with-systemd](https://www.linuxbabe.com/linux-server/how-to-enable-etcrc-local-with-systemd)

But haven't tried it.  Please help

Regards
satimis

---

### Post by HermanAB on 2016-12-06
You are running systemd, so...

---

### Post by satimis on 2016-12-06
> **HermanAB said:**
> You are running systemd, so...
Hi,

systemd is running on this VM

&#10219; which systemd```

/bin/systemd

```

I have been running rc.local for long time.  All Ubuntu 14.04 VMs with rc.local to run certain commands at boot work great without problem.

satimis

---

### Post by ajgreeny on 2016-12-06
It might help if we could see the content of your **/etc/rc.local** file to see if that gives us any clues.

---

### Post by satimis on 2016-12-06
> **ajgreeny said:**
> It might help if we could see the content of your **/etc/rc.local** file to see if that gives us any clues.
Hi,

Tried both versions:-

1)```

#!/bin/bash
mount -t vboxsf Transfer_Directory_PC1A /home/satimis/Transfer_Directory_PC1A

exit 0

```

2)```

#!/bin/sh -e
mount -t vboxsf Transfer_Directory_PC1A /home/satimis/Transfer_Directory_PC1A

exit 0

```

Version 2) works on Ubuntu 14.04

If after booting up the VM and run```

sudo mount -t vboxsf Transfer_Directory_PC1A /home/satimis/Transfer_Directory_PC1A

```
The folder can be mounted.

Regards
satimis

---

### Post by satimis on 2016-12-06
Hi all,

I found the cause of problem

```

sudo chown satimis:satimis /home/satimis/Transfer_Directory_PC1A

```

unable to change ownership

$ cat /etc/sudoers```

Defaults	env_reset
Defaults	mail_badpass
Defaults	secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin"

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo	ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d

```

Even login as root and running;
```

chown satimis:satimis /home/satimis/Transfer_Directory_PC1A/

```

Still failed.  Very strange

satimis

---

### Post by SeijiSensei on 2016-12-06
I would never create a root-owned mount point in a user's home directory.  I generally create all my mount points under /media these days; before I'd use /mnt.  If root is going to mount the file share, have root own the mount point as well.

---

### Post by satimis on 2016-12-06
> **SeijiSensei said:**
> I would never create a root-owned mount point in a user's home directory.  I generally create all my mount points under /media these days; before I'd use /mnt.  If root is going to mount the file share, have root own the mount point as well.
Hi,

I used following steps creating /home/satimis/Transfer_Directory_PC1A/

$ sudo mkdir /home/satimis/Transfer_Directory_PC1A/
$ sudo chown satimis:satimis /home/satimis/Transfer_Directory_PC1A/

It worked for me for years on Ubuntu 14.04 without problem.

Performed following steps:-

~&#10219; sudo rmdir /home/satimis/Transfer_Directory_PC1A/

~&#10219;  sudo mkdir /mnt/Transfer_Directory_PC1A/

~&#10219; sudo chown satimis:satimis /mnt/Transfer_Directory_PC1A/

&#10219; cat /etc/rc.local```

#!/bin/bash

mount -t vboxsf Transfer_Directory_PC1A /mnt/Transfer_Directory_PC1A

exit 0
```
Remark: also tried
#!/bin/sh -e

Rebooted VM
Still failed to mount.

I have to run on terminal```

&#10219; sudo mount -t vboxsf Transfer_Directory_PC1A /mnt/Transfer_Directory_PC1A/

```

Besides the folder won't be displayed on satimis' nautilus

satimis

---

### Post by satimis on 2016-12-07
Hi all,

Problem solved.  It is NOT necessary creating the folder /home/satimis/Transfer_Directory_PC1A, nor creating the file /etc/rc.local.

The trick is as follows;

On Oracle VM VirtualBox Manager
-> Settings -> Shared Folders -> Add New Shared Folder

Start VM
On terminal run;```

$ su -
$ usermod -a -G vboxsf satimis
$ reboot

```

Then
folder "sf_Transfer_Directory_PC1A" can be read.

satimis

---

### Post by ajgreeny on 2016-12-07
What a pity you did not say at the start this was a shared folder in VBox; I could have told you straight away how to do what you have now found, and it would have been a 10 second job.
Never-mind - you got there eventually.

---

