---
title: "Installed Vista Lost Grub..."
date: 2006-12-27
forum: General Help
---

### Post by ofek on 2006-12-27
I've installed vista yesterday (need it for work ...) and well my grub is gone and i can't reach my feisty =/. what should I do or how do I get my grub menu back?

---

### Post by bodhi.zazen on 2006-12-27
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by souldaddy on 2007-08-22
I'm having a similar problem, and i followed that link to help.  I'm actually sitting in the Live CD right now trying to do it.

This is probably the biggest noob problem there is.... but i type in sudo grub, get the grub> prompt and i type root, then press tab and it just tabs over the 7 spaces or w/e.  it doesn't auto complete.  i tried pressing enter, i tried typing root (, then pressing tab etc

This is turning into such a headache!!!  :(

---

### Post by merlinus on 2007-08-22
```

sudo grub
find /boot/grub/stage1
root (hdx,y)
setup (hdx)
quit

```

Substitute results from find for (hdx,y) and setup (hdx).

-merlin

---

### Post by souldaddy on 2007-08-22
i got a successful run.  ty merlin.  gonna reboot and see what happens :D

---

### Post by souldaddy on 2007-08-22
so i rebooted and it just rebooted directly to windows.  it didn't give me a grub option.  i suppose i should explain my setup..

i have 2 hard drives.  i installed vista on one.  then installed ubuntu on a second hard drive.  everything was fine, but i was getting sick of vista and i was told that if i wanted to dual boot vista/xp i'd have to install xp on a separate drive.  so i installed xp on the ubuntu drive.  ubuntu has it's own partition though and still exists.

so basically, i have ubuntu and xp on one drive(different partitions) and vista on a separate physical drive.

any suggestions on where to go from here?

---

### Post by livestockPimp on 2007-08-22
ensure that BIOS is not booting from the Vista drive first.

---

### Post by splintercellguy on 2007-08-22
You could try the Super GRUB CD.

---

### Post by souldaddy on 2007-08-22
I don't quite understand SuperGrub.  Does it fix the problem or is it more of a temporary solution?  Like, do you have to boot with that CD/USB drive every single time you start your PC?

---

### Post by merlinus on 2007-08-22
Good info here:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

-merlin

---

### Post by souldaddy on 2007-08-28
I tried a few things in the SGD and read all the documentation.  I specifically tried this.. [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#I_reinstalled_Windows_and_Linux_no](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#I_reinstalled_Windows_and_Linux_no)

It's not working.  Are there any other routes I can take?

Thanks for the help so far, I really appreciate it.

---

### Post by merlinus on 2007-08-28
You will have to boot from the live cd and manually mount your ubuntu partition.

```

sudo fdisk -l

```

will show which partition this is.

Then

```

sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda2 /media/ubuntu

```

(substitute the ubuntu partition from fdisk -l for sda2)

Then post results of:

```

cat /media/ubuntu/boot/grub/menu.lst

```

Also post output of sudo fdisk -l

-merlin

---

### Post by souldaddy on 2007-08-28
merlin..

forgive my noobyness here, but you want me to post the results of those commands to this forum?  like for further diagnostics?

also, how do you see what file system your ubuntu is in?

---

### Post by merlinus on 2007-08-28
Yes.  Results of sudo fdisk -l will show your ubuntu partition.  Then use that (e.g. sda1) in the mount command, as indicated

-merlin

---

### Post by souldaddy on 2007-08-28
i said in the previous post that i didn't know what file system my linux partition was in.  and i do not see that information with "sudo fdisk -l"

how do i find out the file system type?  

again, thanks for all your help merlin :D

---

### Post by merlinus on 2007-08-28
Post the output of the command here.

-merlin

---

### Post by souldaddy on 2007-08-28
```
ubuntu@ubuntu:~$ cat /media/ubuntu/boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=5fd1d0b3-4f0b-4b3d-a72b-2ee7c50da47d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=5fd1d0b3-4f0b-4b3d-a72b-2ee7c50da47d ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=5fd1d0b3-4f0b-4b3d-a72b-2ee7c50da47d ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=5fd1d0b3-4f0b-4b3d-a72b-2ee7c50da47d ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=5fd1d0b3-4f0b-4b3d-a72b-2ee7c50da47d ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows Vista/Longhorn (loader)
root            (hd0,1)
savedefault
chainloader     +1

```

hope that can help :D

---

### Post by merlinus on 2007-08-28
It looks like you have successfully mounted ubuntu, or you would not have been able to post this.

So now post:

```

cat /media/ubuntu/boot/grub/device.map

```

and

```

sudo fdisk -l

```

-merlin

---

### Post by souldaddy on 2007-08-28
```
ubuntu@ubuntu:~$ cat /media/ubuntu/boot/grub/device.map
(hd0)   /dev/sda
(hd1)   /dev/sdb

```

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6       19452   156207104    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1217     9775521   83  Linux
/dev/sdb2            1218        1448     1855507+   5  Extended
/dev/sdb3            1449       58816   460800000    7  HPFS/NTFS
/dev/sdb5            1218        1448     1855476   82  Linux swap / Solaris

```

again, much appreciated.

---

### Post by merlinus on 2007-08-28
Everything looks as it should.  I am surprised that SuperGrub would not boot ubuntu, however.

You might try again, following the directions at Herman's website.

If that does not work, we'll try reinstalling grub.  It will need to be installed to (hd0,1). not (hd0,0), from what I can see.

-merlin

---

### Post by souldaddy on 2007-08-28
I tried the Super Grub a few different times.  I was reading the doc quite a bit looking at a few different ways to actually accomplish what I wanted and it didn't work.  Then I just tried those step by step instructions.  

I think part of the reason it's not working is I don't understand what these commands and waht not are actually doing.  I'm not asking for an explanation, I can do that later.  I just need to get Linux up for a class I'm taking this semester.

So, if re-installing Grub isn't a huge issue, let's do that.

---

### Post by merlinus on 2007-08-28
OK, let's give it a go.

```

sudo grub
find /boot/grub/stage1
root (hdx,y)
setup (hdx)
quit

```Substitute results from find for (hdx,y) and setup (hdx).

For example, root (hd0,1) and setup (hd0).

-merlin

---

### Post by souldaddy on 2007-08-28
Seems to have worked.

```
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd1,0)
grub> root (hd1,0)
root (hd1,0)
grub> setup (hd1)
setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+17 p (hd1,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub> quit
quit
ubuntu@ubuntu:~$ 

```

i'm rebooting now.

---

### Post by souldaddy on 2007-08-28
hehe, i jumped the gun on that restart.  it tried to boot straight into XP again.  =/

---

### Post by merlinus on 2007-08-28
Try switching the boot order of your drives in BIOS and see if that helps.

-merlin

---

### Post by souldaddy on 2007-08-28
I'm on a dell, and unfortunately I can't.  The BIOS is pretty restrictive.  The only options for booting are device families, like the cd-roms, then hard drives, usb drives, floppies, etc.

---

### Post by merlinus on 2007-08-28
OK.  Try this:

[LIST=1]
[*]boot your SGD CD-ROM
[*]English Super [COLOR=#000000]Grub[/COLOR] Disk
[*]Gnu/Linux
[*]Boot Gnu/Linux Directly[/LIST]-merlin

---

### Post by souldaddy on 2007-08-28
I wrote it down just to be sure.  It didn't work.  When I got to the final menu, before it just rebooted my pc, I had 4 options to choose from.  I tried them all, none of them were listed as OS's but sort of strange text.

Although, one was clear and concise, Root file system.  

Anything else up your sleeve merlin?  

Again, thanks for all the help, it's definitely appreciated.

---

### Post by merlinus on 2007-08-28
At this point, other than prying open your computer case and swapping cables, I have reached the end of my ideas.

Perhaps someone else can chime in who has more experience.

This may offer some useful info:

[http://apcmag.com/dualboot](http://apcmag.com/dualboot)

If worst comes to worst, you can always reinstall ubuntu, but perhaps this time dual-booting from the same hdd as vista.

If you decide to go that route, there's lots of info on it, and I can point you in the right direction.

Good luck!

-merlin

---

### Post by souldaddy on 2007-08-28
Thanks merlin, I'll give it a read and hopefully something will speak to me :D

---

### Post by meierfra on 2007-08-29
I don't know whether it will work, but I would try

sudo grub
root (hd1,0)
setup (hd0)

---

### Post by souldaddy on 2007-08-29
> **meierfra said:**
> I don't know whether it will work, but I would try

sudo grub
root (hd1,0)
setup (hd0)

you sir, are a winner.  i actually did think of doing this myself, but it seemed too "simple."  thanks for the suggestion.  now, to ask an absolutely idiotic question... it's been quite awhile since i've been in ubuntu and i can't seem to remember my username/password.  i don't suppose there's anyway to rescue this information is there?

---

### Post by meierfra on 2007-08-29
You cannot retrieve your password but you can reset it.

At the grub menu choose recovery mode. This will log you into a terminal as root.

to find out your username:

```
ls /home
```


to   set a new password:

```
passwd your_username
```

then reboot via 

```
reboot
```

---

### Post by souldaddy on 2007-08-29
blah, silly question here... but is there a default root password?  when i try and go to the recovery mode it asks me to login as the root.  i don't recall ever setting up a root password though :o

---

### Post by meierfra on 2007-08-29
There is no default root password.  But I'm surprised that it asks for a password. It shouldn't. And I don't have any ideas what to do.

---

### Post by souldaddy on 2007-08-29
> **meierfra said:**
> There is no default root password.  But I'm surprised that it asks for a password. It shouldn't. And I don't have any ideas what to do.

sad face.  we've come so far team!  only to get shut down by my noobsicleness.  good effort though.  i looking around in hopes still though :D

---

### Post by meierfra on 2007-08-29
Checkout this  link:

[http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch08.html]("http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch08.html")

We tried the first method.  But maybe the  second one works.

---

### Post by souldaddy on 2007-08-29
got it to work.  there were 2 ways to do it actually, i goofed the first unknowingly, and the 2nd worked...

first was to create a tmp directory, mount it, then go to etc/shadow and go to the last line where it has..
                      username:passwordencryptedhere:MOREstuff:etc:etc

and just delete the password portion, and reboot into ubuntu and just log in with a username.

the 2nd was much easier and straight forward, but the pal helping me out didn't think it would work due to the root being silly in recovery mode.  make the tmp dir, mount, etc, then chroot into that directory and do "passwd username"

that ended up being the trick \o/

i feel like i've been on an epic journey getting this all going.  and i feel really satisfied that it's all done even though my hand was being held the entire way.

i have to thank gsus, who hangs out in #nesreca on irc.gamesurge.net for these methods to changing my password.

---

