---
title: "Ubuntu + Kubuntu GRUB"
date: 2008-02-15
forum: General Help
---

### Post by rangerguy39 on 2008-02-15
I am using Ubuntu Gutsy and Kubuntu Gutsy both on the same box. I know that I can use them both on the same system with only one install, but I want to have them both installed separately. Grub worked for Kubuntu, which I installed first. Then, I installed Ubuntu on a separate partiton, and it overwrote my Kubuntu grub file. What can I put in my grub config to make them both show up in the Grub Menu?
Thanks,
rangerguy39

---

### Post by jken146 on 2008-02-15
Please post the output of the following commands.

```
sudo fdisk -l
```

```
cat /boot/grub/menu.lst
```

---

### Post by ajgreeny on 2008-02-15
You mean it didn't add kubuntu to the menu automatically?  That is very unusual for ubuntu installs which normally find other linux installations and add them without any problem.  You need to mount the kubuntu partition and then navigate to the menu.lst from that and add its first entry manually to the ubuntu menu.lst.  Jken146's suggestion will allow you to do just that.

---

### Post by rangerguy39 on 2008-02-15
```

#
Disk /dev/sda: 40.0 GB, 40020664320 bytes
#
255 heads, 63 sectors/track, 4865 cylinders
#
Units = cylinders of 16065 * 512 = 8225280 bytes
#
Disk identifier: 0x9dc96e9e
#
#
   Device Boot      Start         End      Blocks   Id  System
#
/dev/sda1               1        2274    18265873+  83  Linux
#
/dev/sda2   *        2275        4709    19559137+  83  Linux
#
/dev/sda4            4710        4865     1253070    5  Extended
#
/dev/sda5            4803        4865      506016   82  Linux swap / Solaris
#
/dev/sda6            4710        4802      746959+  82  Linux swap / Solaris
#
#
Partition table entries are not in disk order
#
_____________________________
#
#
# menu.lst - See: grub(8), info grub, update-grub(8)
#
#            grub-install(8), grub-floppy(8),
#
#            grub-md5-crypt, /usr/share/doc/grub
#
#            and /usr/share/doc/grub-doc/.
#
#
## default num
#
# Set the default entry to the entry number NUM. Numbering starts from 0, and
#
# the entry number 0 is the default if the command is not used.
#
#
#
# You can specify 'saved' instead of a number. In this case, the default entry
#
# is the entry saved with the command 'savedefault'.
#
# WARNING: If you are using dmraid do not use 'savedefault' or your
#
# array will desync and will not let you boot your system.
#
default         0
#
#
## timeout sec
#
# Set a timeout, in SEC seconds, before automatically booting the default entry
#
# (normally the first entry defined).
#
timeout         30
#
#
## hiddenmenu
#
# Hides the menu by default (press ESC to see the menu)
#
hiddenmenu
#
#
# Pretty colours
#
#color cyan/blue white/blue
#
#
## password ['--md5'] passwd
#
# If used in the first section of a menu file, disable all interactive editing
#
# control (menu entry editor and command-line)  and entries protected by the
#
# command 'lock'
#
# e.g. password topsecret
#
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
#
# password topsecret
#
#
#
#
# examples
#
#
#
# title         Windows 95/98/NT/2000
#
# root          (hd0,0)
#
# makeactive
#
# chainloader   +1
#
#
#
# title         Linux
#
# root          (hd0,1)
#
# kernel        /vmlinuz root=/dev/hda2 ro
#
#
#
#
#
#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST
#
#
### BEGIN AUTOMAGIC KERNELS LIST
#
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
#
## by the debian update-grub script except for the default options below
#
#
## DO NOT UNCOMMENT THEM, Just edit them to your needs
#
#
## ## Start Default Options ##
#
## default kernel options
#
## default kernel options for automagic boot options
#
## If you want special options for specific kernels use kopt_x_y_z
#
## where x.y.z is kernel version. Minor versions can be omitted.
#
## e.g. kopt=root=/dev/hda1 ro
#
##      kopt_2_6_8=root=/dev/hdc1 ro
#
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
#
# kopt=root=UUID=ce1e19b0-6411-491d-9e15-c56c587075d2 ro
#
#
## Setup crashdump menu entries
#
## e.g. crashdump=1
#
# crashdump=0
#
#
## default grub root device
#
## e.g. groot=(hd0,0)
#
# groot=(hd0,1)
#
#
## should update-grub create alternative automagic boot options
#
## e.g. alternative=true
#
##      alternative=false
#
# alternative=true
#
#
## should update-grub lock alternative automagic boot options
#
## e.g. lockalternative=true
#
##      lockalternative=false
#
# lockalternative=false
#
#
## additional options to use with the default boot option, but not with the
#
## alternatives
#
## e.g. defoptions=vga=791 resume=/dev/hda5
#
# defoptions=quiet splash
#
#
## should update-grub lock old automagic boot options
#
## e.g. lockold=false
#
##      lockold=true
#
# lockold=false
#
#
## Xen hypervisor options to use with the default Xen boot option
#
# xenhopt=
#
#
## Xen Linux kernel options to use with the default Xen boot option
#
# xenkopt=console=tty0
#
#
## altoption boot targets option
#
## multiple altoptions lines are allowed
#
## e.g. altoptions=(extra menu suffix) extra boot options
#
##      altoptions=(recovery) single
#
# altoptions=(recovery mode) single
#
#
## controls how many kernels should be put into the menu.lst
#
## only counts the first occurence of a kernel, not the
#
## alternative kernel options
#
## e.g. howmany=all
#
##      howmany=7
#
# howmany=all
#
#
## should update-grub create memtest86 boot option
#
## e.g. memtest86=true
#
##      memtest86=false
#
# memtest86=true
#
#
## should update-grub adjust the value of the default booted system
#
## can be true or false
#
# updatedefaultentry=false
#
#
## should update-grub add savedefault to the default options
#
## can be true or false
#
# savedefault=false
#
#
## ## End Default Options ##
#
#
title           Ubuntu 7.10, kernel 2.6.22-14-generic
#
root            (hd0,1)
#
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=ce1e19b0-6411-491d-9e15-c56c587075d2 ro quiet splash
#
initrd          /boot/initrd.img-2.6.22-14-generic
#
quiet
#
#
title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
#
root            (hd0,1)
#
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=ce1e19b0-6411-491d-9e15-c56c587075d2 ro single
#
initrd          /boot/initrd.img-2.6.22-14-generic
#
#
title           Kubuntu 7.10, kernel 2.6.22-14-generic
#
root            (hd0,3)
#
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=ce1e19b0-6411-491d-9e15-c56c587075d2 ro single
#
initrd          /boot/initrd.img-2.6.22-14-generic
#
quiet
#
#
### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by cabaro on 2008-02-15
Hmm..

Something doesn't add up here, as far as i can see.

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)

that would be 
/dev/sda2   *        2275        4709    19559137+  83  Linux

Right?


title           Kubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,3)

that would be (with my math)
/dev/sda4            4710        4865     1253070    5  Extended


Dunno, maybe i should get some sleep ;)

---

### Post by cabaro on 2008-02-15
Just noticed 'Partition table entries are not in disk order'

---

### Post by jken146 on 2008-02-15
I notice that your two linux partitions are sda1 and sda2, which in GRUB-speak translate to hd0,0 and hd0,1 respectively.  You should modify the Kubuntu entry in menu.lst, changing, **root (hd0,3)** to **root (hd0,0)** and see if this fixes it.

---

### Post by jken146 on 2008-02-15
> **cabaro said:**
> Just noticed 'Partition table entries are not in disk order'

That doesn't matter, it always says that.

---

### Post by cabaro on 2008-02-15
> **jken146 said:**
> I notice that your two linux partitions are sda1 and sda2, which in GRUB-speak translate to hd0,0 and hd0,1 respectively.  You should modify the Kubuntu entry in menu.lst, changing, **root (hd0,3)** to **root (hd0,0)** and see if this fixes it.

That's pretty much where i was gonna go with this :KS

---

### Post by rangerguy39 on 2008-02-15
says "File not found" :(

---

### Post by jken146 on 2008-02-15
> **rangerguy39 said:**
> says "File not found" :(

Could you be more specific please?

---

### Post by rangerguy39 on 2008-02-15
Grub says 'File Not Found!'... i cant get much more specific than that. :confused:

---

### Post by cabaro on 2008-02-15
ok

```
ls /media
```

Can you find sda1 or sda2?

```
cat /media/sdaX/boot/grub/menu.lst
```

Does it work? (X being the one you found under /media)

---

### Post by rangerguy39 on 2008-02-15
No, they are not there. They are in /dev/, though they are files, not directories.

---

### Post by cabaro on 2008-02-15
```
mount
```

---

### Post by rangerguy39 on 2008-02-15
```


   1.
      /dev/sda2 on / type ext3 (rw,errors=remount-ro)
   2.
      proc on /proc type proc (rw,noexec,nosuid,nodev)
   3.
      /sys on /sys type sysfs (rw,noexec,nosuid,nodev)
   4.
      varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
   5.
      varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
   6.
      udev on /dev type tmpfs (rw,mode=0755)
   7.
      devshm on /dev/shm type tmpfs (rw)
   8.
      devpts on /dev/pts type devpts (rw,gid=5,mode=620)
   9.
      lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
  10.
      securityfs on /sys/kernel/security type securityfs (rw)
  11.
       


```

---

### Post by cabaro on 2008-02-15
can you give me the output of
```
mount
```


I'm going for a rolley.
Back in 5.

---

### Post by rangerguy39 on 2008-02-15
the latest ubuntu installation is on /dev/sda1

---

### Post by rangerguy39 on 2008-02-15
> **cabaro said:**
> can you give me the output of
```
mount
```


I'm going for a rolley.
Back in 5.
i did

---

### Post by cabaro on 2008-02-15
Me too, what's the outcome of mount?

---

### Post by rangerguy39 on 2008-02-15
> **rangerguy39 said:**
> ```


   1.
      /dev/sda2 on / type ext3 (rw,errors=remount-ro)
   2.
      proc on /proc type proc (rw,noexec,nosuid,nodev)
   3.
      /sys on /sys type sysfs (rw,noexec,nosuid,nodev)
   4.
      varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
   5.
      varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
   6.
      udev on /dev type tmpfs (rw,mode=0755)
   7.
      devshm on /dev/shm type tmpfs (rw)
   8.
      devpts on /dev/pts type devpts (rw,gid=5,mode=620)
   9.
      lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
  10.
      securityfs on /sys/kernel/security type securityfs (rw)
  11.
       


```

> **cabaro said:**
> Me too, what's the outcome of mount?
no, i mean I posted the outcome...

---

### Post by cabaro on 2008-02-15
Oh, i see .. saving your breath :)

So sda1 is not mounted.

We could try mount it

```
sudo mkdir /mnt/sda1

mount -t ext3 /dev/sda1 /mnt/sda1

```

Can you try that?

---

### Post by rangerguy39 on 2008-02-15
did it

---

### Post by cabaro on 2008-02-15
```
ls /mnt/sda1/boot
```

Is it there?

```
cat /mnt/sda1/boot/grub/menu.lst
```

---

### Post by rangerguy39 on 2008-02-15
```
ls: /mnt/sda1/boot: No such file or directory
```

---

### Post by cabaro on 2008-02-15
No such luck..

I thought the old menu.lst might have been installed to sda1.

what does this give you (first grub, then find command)

```
grub
find /boot/grub/stage1

```

---

### Post by rangerguy39 on 2008-02-15
```
Error 15: File not found
```
thanks for being patient to help me with this

---

### Post by cabaro on 2008-02-15
sorry

```

sudo grub
find /boot/grub/stage1
```

---

### Post by rangerguy39 on 2008-02-15
```
(hd0,1)
```

---

### Post by cabaro on 2008-02-15
Gnah....thats sda2..

I'm starting to be out of ideas at the moment (it's 3AM).

Try editing /boot/grub/menu.lst and make copies of the kubuntu entry with different partition numers and try them... start rebooting, rebooting...

> 
title           Kubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=ce1e19b0-6411-491d-9e15-c56c587075d2 ro single

title           Kubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=ce1e19b0-6411-491d-9e15-c56c587075d2 ro single

title           Kubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=ce1e19b0-6411-491d-9e15-c56c587075d2 ro single

title           Kubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=ce1e19b0-6411-491d-9e15-c56c587075d2 ro single



Are you typing from the same machine?

---

### Post by rangerguy39 on 2008-02-15
no, I am not. I am using a pastebin to transfer outcomes.

---

### Post by rangerguy39 on 2008-02-15
```
0,3 - cannot mount selected partition
0,2 - no such partition
0,0 - file not found
0,4 - cannot mount selected partition
```

---

### Post by cabaro on 2008-02-15
could you still give me output of

```
ls -l /mnt/sda1
```

---

### Post by rangerguy39 on 2008-02-15
when i do 0,1 - it gives me a shell

---

### Post by rangerguy39 on 2008-02-15
```
total 0
```
its there, but its a file. No extension, just a file

---

### Post by cabaro on 2008-02-15
Yes, well that was sda2 (the working ubuntu, as i recall).

```
ls -l /mnt/sda1
```

---

### Post by cabaro on 2008-02-15
```
sudo su -
cd /mnt/sda1
ls -l

```

---

### Post by rangerguy39 on 2008-02-15
```
total 0
```
maybe you can go on freenode and private message me as rufus_ ?

---

### Post by cabaro on 2008-02-15
Have to mount it again

```

mount -t ext3 /dev/sda1 /mnt/sda1

```

ls /mnt/sda1

---

### Post by rangerguy39 on 2008-02-15
```
lost+found
```

---

### Post by cabaro on 2008-02-15
hmm. nothing there?

Could it be, that the kubuntu partition is wiped?

---

### Post by rangerguy39 on 2008-02-15
no, that partition has like 2gigs of used memory on it, i dont think its wiped
again, is it possible for me to talk to you on irc?

---

### Post by cabaro on 2008-02-15
I think i gotta get some sleep.

You could try booting with a live cd and see which partitions hold what.
(i should of thought that some time ago :)

Maybe some Xperts wake up in US soon. I'm still a noob.

Goodnight!

---

### Post by cabaro on 2008-02-15
Dunno, getting late...

Ok, tell me which server to log into and which channel.
Haven't been using irc but at work.

---

### Post by rangerguy39 on 2008-02-15
According to GParted,
/dev/sda1 is mounted at /mnt/sda1 - this is the UBUNTU partition
/dev/sda2 is mounted at / - this is the KUBUNTU partition

---

### Post by rangerguy39 on 2008-02-15
OKAY, i think we have something
____
i did mount -t ext3 /dev/sda2 /mnt/sda2 - and now I get ALL of the directories that I should get for linux

---

### Post by cabaro on 2008-02-15
are you using Kubuntu now?

---

### Post by cabaro on 2008-02-15
ok

```
cat /mnt/sda2/boot/grub/menu.lst
```

---

### Post by cabaro on 2008-02-15
does not get us really anywhere, since sda2 was the root folder already 

[I]   1.
      /dev/sda2 on / type ext3 (rw,errors=remount-ro)
   2.
  [/I]

---

### Post by cabaro on 2008-02-15
```
df -H
```

---

### Post by cabaro on 2008-02-15
4minutes...

---

### Post by rangerguy39 on 2008-02-15
its an exact copy of my ubuntu directories... im confused

---

### Post by cabaro on 2008-02-15
because it's the same partition you're on.

try booting with a livecd and see what's on the partitions. i gotta get some sleep now.
gmt +2 here. see you later.

---

### Post by ajgreeny on 2008-02-16
Me again from post #3.  Try booting into a ubuntu liveCD, or even the current ubuntu install that works, and adding the Disk Mounter to the panel.  You can then see what mountable partitions there are on the machine, and mount them with a simple click on the icon.  In theory you should then be able to see the entry in the kubuntu /boot/grub/menu.lst for kubuntu itself and add it to the ubuntu menu.lst file, more or less as I said in my first post.

However, it almost begins to look as if you overwrote the system files of kubuntu with the ubuntu install, though I must admit the number of partitions you have doesn't seem to agree with that premise.  Very weird, but let's keep trying, never say die!

---

### Post by ch_123 on 2008-02-16
Just a question; considering that you can easily install the Kubuntu environment on 
Ubuntu, and vice-versa, and then switch between them at start up, why are you 
installing two seperate Linux partitions? Seems like a bit of a waste of disk space 
to me...

---

