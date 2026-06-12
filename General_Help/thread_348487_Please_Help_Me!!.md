---
title: "Please Help Me!!"
date: 2007-01-28
forum: General Help
---

### Post by condawg on 2007-01-28
Hi there, fellow strangers.
I just installed Ubuntu 5.10 on my PC.
I had Windows XP installed, and I told it to partition the disk so that Linux took up 20% of my hard drive, leaving windows with the other 80%.
But, whenever I start up my computer, the dual bootloader thing says it's loading, but then Linux just loads...

I'm pretty sure it should be partitioned to 20%, but I cannot load windows.
Please help me, strangers!

Thank you

---

### Post by yabbadabbadont on 2007-01-28
Please post the contents of your /boot/grub/menu.lst file and the output of the following command: "sudo fdisk -l"

---

### Post by condawg on 2007-01-28
> **yabbadabbadont said:**
> Please post the contents of your /boot/grub/menu.lst file and the output of the following command: "sudo fdisk -l"

How do I do that?
I don't know how to do anything with Linux... DAMMIT. I can't stand this!:( :(

---

### Post by etank on 2007-01-28
Click Applications->Accessories->terminal

then in the window that comes up type 
```
cat /boot/grub/menu.lst
```
copy the output and paste it in a reply here.

Then do the same with the "sudo fdisk -l" command.

---

### Post by condawg on 2007-01-28
> **etank said:**
> Click Applications->Accessories->terminal

then in the window that comes up type 
```
cat /boot/grub/menu.lst
```
copy the output and paste it in a reply here.

Then do the same with the "sudo fdisk -l" command.

Okay...
with the boot grub menu thing...


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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.12-9-386
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST






from the sudo fdisk -l thing...


Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1           15567       19457    31254457+  83  Linux

Disk /dev/sda: 1015 MB, 1015808000 bytes
5 heads, 4 sectors/track, 99200 cylinders
Units = cylinders of 20 * 512 = 10240 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              13       99200      991875+   6  FAT16

---

### Post by yabbadabbadont on 2007-01-28
I'm not positive, but it looks like the installer wiped out your windows installation...

Do you only have one harddrive in that machine?

---

### Post by Maestro23 on 2007-01-28
Yeah, looks like Ubuntu took over the whole drive.  Did you manually set up the partitions for Ubuntu?

---

### Post by condawg on 2007-01-28
Are you freakin serious!?!?!
Yeah, I had to manually do it...
It kept on running into a problem the other way...
GOD DAMMIT
Is there any way to get back my whole computer as of yesterday?
I had SO MUCH STUFF on there!
It will take me forever to completely restore my ****, and I had vital programs and files for my website...
AHHHH this SUCKS!

---

### Post by yabbadabbadont on 2007-01-28
Although you probably didn't notice it, I believe that the partitioning tool warned you to have full backups before proceeding...  not that it helps you now.  :(

To paraphrase an old Chicago saying: Backup early and often.


EDIT: Also, you didn't say, I assume that you only have that one 160GB drive installed.

---

### Post by Goober on 2007-01-28
I haven't used GRUB in awhile, but I recall, from when I last used it, that it automatically included a Windows installation on the GRUB Menu, and, when you start up, you can choose between Linux and Windows.  I also recall being able to add the Windows Option onto GRUB from Linux while in Linux, and then being able to restart and load into Linux.  I just have no idea how to do it.

Also, all is not lost.  You can Mount your Windows Partition onto Linux (Search these Forums, there've been a couple threads on how to do that), and then access your files.  I just had my Windows corrupt itself, and installed Ubuntu, and saved essentially all of my non-backed-up files.  All is NOT lost!

---

### Post by condawg on 2007-01-28
> **Goober said:**
> I haven't used GRUB in awhile, but I recall, from when I last used it, that it automatically included a Windows installation on the GRUB Menu, and, when you start up, you can choose between Linux and Windows.  I also recall being able to add the Windows Option onto GRUB from Linux while in Linux, and then being able to restart and load into Linux.  I just have no idea how to do it.

Also, all is not lost.  You can Mount your Windows Partition onto Linux (Search these Forums, there've been a couple threads on how to do that), and then access your files.  I just had my Windows corrupt itself, and installed Ubuntu, and saved essentially all of my non-backed-up files.  All is NOT lost!

Well, it's good to know that all may not be lost.
I might also want to add something that I forgot to mention in my first post....
After about 40 minutes or so, my screen just turns to an image of many coloured lines...
That's not normal.
Then I have to restart my computer.

---

### Post by yabbadabbadont on 2007-01-28
> **Goober said:**
> I haven't used GRUB in awhile, but I recall, from when I last used it, that it automatically included a Windows installation on the GRUB Menu, and, when you start up, you can choose between Linux and Windows.  I also recall being able to add the Windows Option onto GRUB from Linux while in Linux, and then being able to restart and load into Linux.  I just have no idea how to do it.

Also, all is not lost.  You can Mount your Windows Partition onto Linux (Search these Forums, there've been a couple threads on how to do that), and then access your files.  I just had my Windows corrupt itself, and installed Ubuntu, and saved essentially all of my non-backed-up files.  All is NOT lost!

You obviously didn't look at the output of his "sudo fdisk -l" command that he posted above.  His hda drive has only one partition on it, linux...  so unless he has more than one harddrive in that machine, his windows partition was removed, replaced by a single linux partition, formatted, and then ubuntu was installed on it.  I doubt that windows can be recovered at this point.

EDIT: Although I still think you didn't look at the fdisk output I, and the other poster, missed that his one partition doesn't start on the first cylinder of the drive...

---

### Post by condawg on 2007-01-28
> **yabbadabbadont said:**
> You obviously didn't look at the output of his "sudo fdisk -l" command that he posted above.  His hda drive has only one partition on it, linux...  so unless he has more than one harddrive in that machine, his windows partition was removed, replaced by a single linux partition, formatted, and then ubuntu was installed on it.  I doubt that windows can be recovered at this point.

Then all IS lost...
dammit!
Ahh, well...
I'll just reinstall windows and just start all over. :(

---

### Post by yabbadabbadont on 2007-01-28
DON'T DO THAT YET!

I just noticed that your one partition doesn't start at the first cylinder of the drive.  It may be possible to recover windows after all.

Take a look at these first:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
[http://trinityhome.org/Home/index.php?wpid=1&front_id=12](http://trinityhome.org/Home/index.php?wpid=1&front_id=12)
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by condawg on 2007-01-28
> **yabbadabbadont said:**
> DON'T DO THAT YET!

I just noticed that your one partition doesn't start at the first cylinder of the drive.  It may be possible to recover windows after all.

Take a look at these first:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
[http://trinityhome.org/Home/index.php?wpid=1&front_id=12](http://trinityhome.org/Home/index.php?wpid=1&front_id=12)
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

I love you.
Looks like it could work
:)
Thanks!

---

### Post by yabbadabbadont on 2007-01-28
> **condawg said:**
> I love you.
Looks like it could work
:)
Thanks!

I'm just sorry that I missed that in the first place and almost caused you to wipe the drive.  I'm really glad you read my reply before it was too late.  Hopefully, one of those programs will help you get your windows partition back.

---

### Post by condawg on 2007-01-28
> **yabbadabbadont said:**
> I'm just sorry that I missed that in the first place and almost caused you to wipe the drive.  I'm really glad you read my reply before it was too late.  Hopefully, one of those programs will help you get your windows partition back.

Well, testdisk looks like it could work.
I downloaded it, but I can't get it to run.
Can you tell me what file to run?
(Again, I'm new with Linux)

---

### Post by Goober on 2007-01-28
The way I run it is to open a Terminal and type in 

sudo testdisk

Then you press enter to Analyze, after it loads and such.  Take your time and read the instructions for testdisk carefully, I almost screwed everything up while using it.  When in doubt, take a screenshot and ask.

---

### Post by condawg on 2007-01-29
> **Goober said:**
> The way I run it is to open a Terminal and type in 

sudo testdisk


Whenever I try that, it says that it's not found...

---

### Post by condawg on 2007-01-29
Bump...
Sorry, but I'm not even on the first page, and I really need help!
I appreciate all that everyone has been doing to try and help.

---

### Post by condawg on 2007-01-29
bump again...
sorry guys, but I seriously  need help!

---

### Post by condawg on 2007-01-29
Come on guys, PLEASE help me as soon as you can!
I need to get stuff done that I can't get done because of this!

---

### Post by WinterWeaver on 2007-01-29
Where did you extract or install the TestDisk utility?

EDIT: I downloade the app myself to see if I can help. Did you read throught the Doc folder? Also it seems that you have to run the program by typing: sudo testdisk_static

I'm also fairly new to Linux, but I might be able to help, as I'm not a complete infant to Ubuntu.

---

### Post by condawg on 2007-01-29
It's on my desktop...
No, I've not read through t hat.
I tried the static thing you told me about, and it didn't work...

---

### Post by glabouni on 2007-01-29
as long as you didn't write any stuff over it, your old data should be recoverable.
so first thing is to be sure not to write anything to your hard drive.

best way to try to recover your files would be to get your hard drive in another computer and run the partition restoration utility of your choice.
if this fails, you can try to rebuild your MBR manually (if you only had one big partition this could be doable, search for guides on google)
if this fails too, you can give your favourite file restoration utilitiy a try.

success chances may vary depending on your previous filesystem, fat or ntfs.

if everything fails and you really badly need those files, you can send your disk to data recovery professional who will extract data from it for a fee (usually a prohibitive fee unless you are rich, have a vital need of those unaccessible files, or are an entreprise).

past this point, you can start to make list of the files you lost, where to get them if available, check for backups and archives. 
this kind of misadventure has happened to many of us at least once, usually once is enough to learn the importance of backuping.

---

### Post by WinterWeaver on 2007-01-29
kk.. gimme a couple of minutes. I'll install the package and see if I can get it to run

---

### Post by WinterWeaver on 2007-01-29
ok, I'm assuming you installed the latest version downloaded from the link provided earlier in the forums. If so you should have testdisk version 6.5.

I extracted the tar file to the desktop, and it created a folder, testdisk-6.5

Now do the following
Open a terminal again: Applications > Accessories > Terminal
Enlarge the default size of your terminal, as you would resize any other window. (The program requires a minimum of 25 lines to work properly).

Now type the following (or copy and paste the text):
```
sudo ~/Desktop/testdisk-6.5/linux/testdisk_static
```

That command should open the program if you have it extracted in the same location as me, on the desktop.

As for how the program works, I'm not able to really help you, as I've never done anything along those lines. I guess it's best to just read through the documentation they provide.

Wow...... you'll be comming out of this smarter than most others... lol... and that just because you chose to try another os.... O.o

Hope this helped :)

WW

---

### Post by condawg on 2007-01-29
It worked :D
Thanks.
Well, the PROGRAM works now...
I can't get it to do what I want.
I'll try a bit more, and if it doens't work, I'll take screenshots and ask.

---

