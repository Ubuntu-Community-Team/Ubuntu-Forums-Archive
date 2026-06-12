---
title: "Can't mount UDF CDROM"
date: 2007-07-02
forum: General Help
---

### Post by jw5801 on 2007-07-02
I have a UDF CD created using Windows that I can't seem to mount on Ubuntu. I haven't followed any of the writing parts of this HOW-TO as I don't want to be able to write to the CD, simply to read from it.
The important line of my fstab file reads as follows:I have posted elsewhere but I'm not getting a response there so 
```
/dev/hda /media/cdrom0 udf,iso9660 rw,user,noauto 0 0
```
and here is my udftools file:
```
# Drives to register for packet writing:
DEVICES="/dev/hda"

# Pktcdvd patches for kernels 2.6.8 and later use a new interface for
# talking to the kernel, as well as a new set of device nodes. In case
# detection of the proper interface on your system fails, override
# it here. Possible values are "true" or "false".
# NEWINT=true

# Only when using the new interface do you have the option to choose the
# names for the packet writing devices. This is ignored otherwise.
# For example, if DEVICES="/dev/hdd /dev/sr0" and
# NEWINTNAMES="cdwriter dvdwriter", then /dev/hdd will correspond to
# /dev/pktcdvd/cdwriter, and /dev/sr0 will correspond to
# /dev/pktcdvd/dvdwriter. The default setting is NEWINTNAMES="0 1 2 3".
NEWINTNAMES="0 1 2 3"
```
If I try to stop and then start udftools this is what happens:
```
jw5801@jw5801-laptop:~$ sudo /etc/init.d/udftools stop
Stopping udftools packet writing:
/dev/pktcdvd/0=/dev/hda Can't find major/minor numbers

jw5801@jw5801-laptop:~$ sudo /etc/init.d/udftools start
Starting udftools packet writing:
/dev/pktcdvd/0=/dev/hda Device node '0' already in use
```
and if i uncomment and change the NEWINT line to NEWINT=false, this is what I get:
```
jw5801@jw5801-laptop:~$ sudo /etc/init.d/udftools stop
Stopping udftools packet writing:
/dev/pktcdvd/0=/dev/hda ioctl: Inappropriate ioctl for device

jw5801@jw5801-laptop:~$ sudo /etc/init.d/udftools start
Starting udftools packet writing:
/dev/pktcdvd/0=/dev/hda ioctl: Inappropriate ioctl for device
```

So the packet writer cannot open properly therefore attempting to mount through it gets this:
```
jw5801@jw5801-laptop:~$ sudo mount -t udf -o utf8,noatime /dev/pktcdvd/0 /media/cdrom0
mount: /dev/pktcdvd/0 is not a block device (maybe try `-o loop'?)
jw5801@jw5801-laptop:~$ sudo mount -t udf -o loop /dev/pktcdvd/0 /media/cdrom0mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

jw5801@jw5801-laptop:~$ dmesg | tail
[20681.458436] UDF-fs: No fileset found
[20681.595117] Unable to identify CD-ROM format.
[20798.576184] APIC error on CPU0: 40(40)
[20840.260246] APIC error on CPU0: 40(40)
[20859.772417] APIC error on CPU0: 40(40)
[20892.449063] APIC error on CPU0: 40(40)
[20898.816874] APIC error on CPU0: 40(40)
[20948.112256] APIC error on CPU0: 40(40)
[21351.801021] APIC error on CPU0: 40(40)
[21537.107010] UDF-fs: No partition found (1)
```
Anyone have any ideas?

EDIT: It's not the CD that's bad either, it still mounts fine under XP.

---

### Post by tarasbulba on 2007-07-02
Try to edit /etc/fstab file :
/dev/hda        /media/cdrom0  [COLOR="Red"] auto[/COLOR],user,noauto     0       0
if it works then everything ok!
&#304;f doesn't work, apt-get udf tools package.

---

### Post by jw5801 on 2007-07-02
Thanks for the tips! Editing the /etc/fstab file didn't seem to help. Still returned the same error. I installed the udftools package but i'm not quite sure how i'm meant to get it up and running. Some pointers? I tried uncommenting the first couple of lines of the /etc/default/udftools file, But I just get "no such file or directory" errors when I run "sudo /etc/init.d/udftools start"
I'm not quite sure what it's meant to do. Thanks for helping!

---

### Post by jw5801 on 2007-07-02
Ok i'm attempting to mount the disc using a packet driver and this is what happens:
```
jw5801@jw5801-laptop:/dev$ sudo pktsetup /dev/pktcdvd0 /dev/cdrom
ioctl: Inappropriate ioctl for device
```
I don't think that worked but I took the next step as suggested on a few how-tos anyway:
```
jw5801@jw5801-laptop:/dev$ sudo mount /dev/pktcdvd0 /media/cdrom0 -t udf -o rw,noatime
mount: /dev/pktcdvd0 is not a block device (maybe try `-o loop'?)
jw5801@jw5801-laptop:/dev$ sudo mount /dev/pktcdvd0 /media/cdrom0 -t udf -o rw,noatime,loop
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
Quite a few posts and how-tos around the web mention patching the kernel as part of the setup... would I have to do this in order to mount this cdrom? It would seem kinda strange having something I can install out of the repositories that doesn't work without recompiling the kernel.
Anyway just in case I do need to do that... I'm kinda new at this, so what would it entail? And more importantly would it effect anything else I may have installed? Such as ndiswrapper for my wireless card?
Cheers to anyone who can help!
Jason

---

### Post by jw5801 on 2007-07-05
Bumpity?
I posted here with a complete run-down of everything that I did so that might be a good place to start:
[http://ubuntuforums.org/showpost.php?p=2949501&postcount=44](http://ubuntuforums.org/showpost.php?p=2949501&postcount=44)

---

### Post by bitzbox on 2007-07-07
This is how I got packet writing working with Feisty:

**Step 1**
```
sudo apt-get install udftools
```

**Step 2**
```
sudo gedit /etc/defaults/udftools
```
Add this line:
```
DEVICES="/dev/hdc"
```
Note: my optical drive is /dev/hdc, yours may be different

**Step 3**
```
sudo /etc/init.d/udftools start
```

**Step 4**
Insert a new (unused) CD-RW in the drive

**Step 5**
```
sudo cdrwtool -t 32 -d /dev/hdc -q
```

**Step 6**
```
sudo mkdir -p /media/udfwriter
```

**Step 7**
```
sudo mount -t udf -o utf8,noatime /dev/pktcdvd/0 /media/udfwriter
```

**Step 8**
```
sudo chmod 777 /media/udfwriter/.
```

**Step 9**
```
sudo gedit /etc/fstab
```
Add this line:
```
/dev/pktcdvd/0 /media/udfwriter udf user,noauto,noatime,utf8 0 0
```

**Step 10**
Disable the following in "System/Preferences/Removable Drives and Media":
- Mount removable media whem inserted
- Browse removable media when inserted
I had to do this to stop the system mounting the UDF media at the incorrect mount point.

If you only want to read a UDF CD, you can omit steps 4, 5 and 8

Hope this helps, best of luck :)

Regards .....

---

### Post by Pausanias on 2007-07-14
(ignore this)

---

### Post by Pausanias on 2007-07-14
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/44233](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/44233) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **tarasbulba said:**
> Try to edit /etc/fstab file :
/dev/hda        /media/cdrom0  [COLOR="Red"] auto[/COLOR],user,noauto     0       0
if it works then everything ok!
&#304;f doesn't work, apt-get udf tools package.


There should be **no comma** between auto and user. Just a space. Try that before installing udftools.

---

### Post by jw5801 on 2007-07-15
I tried all of the above to no avail. Unfortuneately I no longer have the CD I was testing on (it was one loaned to me with info for a Uni assignment), so further experimentation is no longer possible! Oh well thanks for the help anyway!

PS. I realised there shouldn't be a space there when I looked at the format of the original fstab file, but neither worked anyway (I tried with the comma after the proper way didn't work, but it just spat out random errors :p).

---

