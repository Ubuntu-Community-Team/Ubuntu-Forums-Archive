---
title: "can't format a flash drive."
date: 2015-02-22
forum: General Help
---

### Post by matthew74 on 2015-02-22
i can't format a sandisk 32gb flash drive. both windows and ubuntu. it says write protected in windows or read-only in ubuntu

---

### Post by sammiev on 2015-02-22
> **matthew74 said:**
> i can't format a sandisk 32gb flash drive. both windows and ubuntu. it says write protected in windows or read-only in ubuntu

Have you tried to unmount it first? Just a thought..

---

### Post by matthew74 on 2015-02-22
yes

---

### Post by sammiev on 2015-02-22
I ran into this with gparted but was always able to get around it using More Actions in Disks from Ubuntu.

---

### Post by matthew74 on 2015-02-22
tried both gpart and disk utility., tried diskpart in windows, trying to remembered what else i have tried, nothing is working

---

### Post by matthew74 on 2015-02-22
it my brother in laws. he is going to take it to my brother as he works at geek squad to see what he can do. but at the moment i am trying to figure it out

---

### Post by matthew74 on 2015-02-22
i can still view what on it but can't format, write, copy

---

### Post by matthew74 on 2015-02-22
just tried fdisk

---

### Post by coldraven on 2015-02-23
I had this problem last week. Solved it by getting mkusb and using the "Delete the first megabyte" option.
mkusb is just a safety conscious front end for dd. It makes it very difficult to erase the wrong drive using mkusb. You have to click OK several times to get to final screen!
See here for my thread:
[http://ubuntuforums.org/showthread.php?t=2264882](http://ubuntuforums.org/showthread.php?t=2264882)

or direct link
[URL="https://help.ubuntu.com/community/mkusb#Wipe_the_first_megabyte_or_the_whole_device"]https://help.ubuntu.com/community/mkusb#Wipe_the_first_megabyte_or_the_whole_device

[/URL]

---

### Post by sammiev on 2015-02-23
> **coldraven said:**
> I had this problem last week. Solved it by getting mkusb and using the "Delete the first megabyte" option.
mkusb is just a safety conscious front end for dd. It makes it very difficult to erase the wrong drive using mkusb. You have to click OK several times to get to final screen!
See here for my thread:
[http://ubuntuforums.org/showthread.php?t=2264882](http://ubuntuforums.org/showthread.php?t=2264882)

or direct link
[URL="https://help.ubuntu.com/community/mkusb#Wipe_the_first_megabyte_or_the_whole_device"]https://help.ubuntu.com/community/mkusb#Wipe_the_first_megabyte_or_the_whole_device

[/URL]

+1 just make sure it sees the usb stick. Mkusb replaced unetbootin and gparted sometime ago here for all my usb devices.

---

### Post by matthew74 on 2015-02-23
mkusb didn't work

---

### Post by haplorrhine on 2015-02-23
my noob advice :P

If you're formatting it anyway, then you might try shredding it first.  Something like...

sudo shred -n1 /dev/sdb

-n1 means only 1 pass, making the job faster.  Caution:  Since this will destroy the data, first check that the problem is the flashdrive and not your system.  

edit:
Another caution, if you have two harddrives, /dev/sdb might be one of your harddrives and /dev/sdc your flashdrive.

---

### Post by matthew74 on 2015-02-23
shreding it didn't work,it says failed to open for writing: Read-only file system

---

### Post by haplorrhine on 2015-02-23
I'm assuming you already tried chmod to change the privileges.  A tool called chattr can also be used to deny access.  For example, chattr +i or -i adds or removes the "immutable flag", a flag which to my knowledge cannot be overridden with chmod.  Enter command-line "info chattr" for more information.

---

### Post by haplorrhine on 2015-02-23
Wait, duh...

Check the /etc/mtab oand /proc/mounts file.  In these files, the device will be succeeded by a list of flags.  "ro" is the read-only flag.  "rw" is what you probably want.  Maybe there's an indirect fix, but if you're going to operate on the files, then BE CAREFUL!!!  This is definitely beyond my abilities.

Here is the entry that was appended to /proc/mounts when I plugged in a sandisk of my own.
/dev/sdb1 /media/haplorrhine/drive-name ext4 rw,nosuid,nodev,relatime,data=ordered 0 0

---

### Post by matthew74 on 2015-02-23
i am not familiar with ubuntu or linux. how do i edit the files?

---

### Post by sudodus on 2015-02-23
If you cannot make your pendrive writeable after all this effort, I'm afraid that it is gridlocked. See this link

[Pendrive lifetime]("http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297")

---

### Post by matthew74 on 2015-02-23
i am going to try it on a mac

---

### Post by haplorrhine on 2015-02-23
Why give up if they haven't checked the mount flags yet?

Plug in the flashdrive, open a terminal, then enter the command-line:
```
ls -l /dev | grep sdb
```
You'll probably see two entries and two entries only, one containing "sdb" and one containing "sdb1".
/dev/sdb1 is your flashdrive.
With the flashdrive still connected, enter the command-line:
```
cat /proc/mounts | grep sdb1
```

You should see something like in my previous post.
[FONT=arial black]/dev/sdb1 /media/<username>/<drive-name> <file-system-type> rw,nosuid,nodev,relatime,data=ordered 0 0[/FONT]
If it contains "ro" instead of "rw", then it's mounting as read-only for some reason.

---

### Post by matthew74 on 2015-02-23
nothing showing up when i do [COLOR=#000000][FONT=Ubuntu Mono]cat /proc/mounts | grep sdb1[/FONT][/COLOR]

---

### Post by matthew74 on 2015-02-23
mac didn't work.

---

### Post by coldraven on 2015-02-24
> mkusb didn't work
After running mkusb you have to re-create the partition and format it.
Using gparted the drive should show up as "Unallocated space". Right click on it and select "New>Primary partition>Format FAT32". OK
To complete the actions click the green tick "Apply" at the top of the screen.

---

### Post by matthew74 on 2015-02-24
> **coldraven said:**
> After running mkusb you have to re-create the partition and format it.
Using gparted the drive should show up as "Unallocated space". Right click on it and select "New>Primary partition>Format FAT32". OK
To complete the actions click the green tick "Apply" at the top of the screen.
mkusb is saying [COLOR=#000000][FONT=arial]Wiping the first megabyte (MibiByte) of /dev/sdb ... :[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]... Failed :-([/FONT][/COLOR]

---

### Post by haplorrhine on 2015-02-24
Wouldn't it not be unallocated until he clears the old partition table?

> **matthew74 said:**
> nothing showing up when i do [COLOR=#000000][FONT=Ubuntu Mono]cat /proc/mounts | grep sdb1[/FONT][/COLOR]

Okay, try this.

without the flashdrive connected
 [FONT=courier new]cat /proc/mounts >proc1[/FONT]

Then, after plugging it in
 [FONT=courier new]cat /proc/mounts >proc2[/FONT]

[FONT=courier new]diff proc1 proc2[/FONT]
Show us the output.  That is your flashdrive.

Aside from /proc/mounts, there are also files [/etc/mtab]("http://en.wikipedia.org/wiki/Mtab") and [/etc/fstab]("http://en.wikipedia.org/wiki/Fstab").  You can edit these with the command line [FONT=courier new]sudo gedit /etc/*tab[/FONT].  You could try editing the flags in those files, but for all I know this could just irreversably mess up your system. :p

---

### Post by matthew74 on 2015-02-24
> **haplorrhine said:**
> Wouldn't it not be unallocated until he clears the old partition table?



Okay, try this.

```
[INDENT=2][without the flashdrive plugged in]
[/INDENT]
 cat /proc/mounts >proc1[INDENT=2][now plug in the flashdrive]
[/INDENT]
 cat /proc/mounts >proc2
diff proc1 proc2

```

Show us what the line says.

Aside from /proc/mounts, there are also files [/etc/mtab]("http://en.wikipedia.org/wiki/Mtab") and [/etc/fstab]("http://en.wikipedia.org/wiki/Fstab").  You can edit these with the command line [FONT=courier new]sudo gedit /etc/*tab[/FONT].  You could try editing the flags in those files, but for all I know this could just irreversably mess up your system. :p 
do i type those in the terminal?

---

### Post by haplorrhine on 2015-02-24
Yes, edited it.  "sudo gedit" just opens the file with gedit.

---

### Post by matthew74 on 2015-02-24
nothing is showing up for   
cat /proc/mounts >proc1[now plug in the flashdrive]
 cat /proc/mounts >proc2

am i doing something wrong?

---

### Post by haplorrhine on 2015-02-24
That's okay.  It is reading the entire contents of the /proc/mounts file, and making copies called "proc1" and "proc2"&#8212;the output is going into those files.  The line [FONT=courier new]diff proc1 proc2[/FONT] should give you output&#8212;it compares the files, showing you what was added to /proc/mounts.  It will show you the entry that corresponds to your flashdrive.  You should see this same entry in the other files mentioned:  /etc/mtab and /etc/fstab.
You could try editing the flashdrive entry in these files, changing the "ro" to "rw" (if there is an "ro" flag), but this might just muck everything up, I have no clue.

Here are some examples of normal flashdrive entries: fat32 and ext4 filesystem types.
[FONT=courier new]/dev/sdb1 /media/haplorrhine/drivename vfat rw,nosuid,nodev,relatime,uid=1000,gid=1000,ftf8,flush,errors=remount-ro 0 0
/dev/sdb2 /media/haplorrhine/drivename ext4 rw,nosuid,nodev,relatime,data=ordered 0 0[/FONT]

Note to mods:  there should be no whitespace in [FONT=courier new]flush[/FONT] above.

---

### Post by matthew74 on 2015-02-24
i also tried hdman

---

### Post by haplorrhine on 2015-02-24
That [FONT=courier new]errors=remount-ro[/FONT] flag looks like something you might want to remove or change.

---

### Post by haplorrhine on 2015-02-24
Here's something else to try.  Now, if you couldn't shred it, you probably can't repair it either, but it's worth a shot.
According to the info page ([FONT=courier new]info dosfsck[/FONT]), dosfsck repairs broken file systems, and I'm assuming yours is mounting as ro because it's broken.  Where I found it, they recommended using the [FONT=courier new]dosfsck -a -v[/FONT] options.  So [FONT=courier new]dosfsck -a -v /dev/sdb[/FONT] for example.

Another thought.  If you have two harddrives for some reason, your flashdrive might be /dev/sdc instead.

> **coldraven said:**
> After running mkusb you have to re-create the partition and format it.
Using gparted the drive should show up as "Unallocated space". Right  click on it and select "New>Primary partition>Format FAT32". OK
To complete the actions click the green tick "Apply" at the top of the screen.

A newbie mistake with GParted is that they will leave it pointed at their harddrive rather than selecting the flashdrive from the drop-down menu.  Maybe GParted can get past this read-only flag.

---

### Post by matthew74 on 2015-02-24
the flash drive is sdb, if i remembered right i already tried dosfsck but i will try it again

---

### Post by matthew74 on 2015-02-24
it came back as 
fsck.fat 3.0.26 (2014-03-07)fsck.fat 3.0.26 (2014-03-07)
open: Read-only file system

---

### Post by haplorrhine on 2015-02-25
I'm afraid I can't help you. If this problem is surmountable, changing the mount options is probably what you have to do.  I don't know how to do it, and for removeable media it might be especially tricky.

[http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221)[QUOTE=Sutekh]You plug your USB drive in, and use fdisk to find the device node and  then mount it.  Sometimes the USB appears as /dev/sda1, sometimes  /dev/sdb1.  It can depend on what order you plug in your USB devices,  and where you plug them in.  This is a real pain if you mount devices  manually or if you are trying to customise your /etc/fstab.[/QUOTE]

Adding to sudodus, here's a possibility that I spotted in [Bodhi Zazen's fstab guide]("http://ubuntuforums.org/showthread.php?t=283131").
[http://readlist.com/lists/vger.kernel.org/linux-kernel/22/111748.html](http://readlist.com/lists/vger.kernel.org/linux-kernel/22/111748.html)
Apparently writing to a vfat drive with this "sync" option can ruin it.

---

### Post by SuperFreak on 2015-02-25
You could try a low level format at the USB manufacturerers site. That rescued a USB that I thought I was going to throw away. Here is an example for Patriot USBs [http://www.patriotmemory.com/forums/showthread.php?897-Low-Level-Format-Tool-Write-Protected-USB-%28Read-First-Post-on-Pg1-before-replying!%29]("http://www.patriotmemory.com/forums/showthread.php?897-Low-Level-Format-Tool-Write-Protected-USB-%28Read-First-Post-on-Pg1-before-replying!%29"). Just find your USB manufacturer

[http://www.tomshardware.com/forum/297523-32-flash-drive-permanently-stuck-write-protected]("http://www.tomshardware.com/forum/297523-32-flash-drive-permanently-stuck-write-protected")

[http://www.myusbtools.com/2013/06/silicon-power-low-level-formatter-v3700.html](http://www.myusbtools.com/2013/06/silicon-power-low-level-formatter-v3700.html)

---

### Post by sudodus on 2015-02-25
> **haplorrhine said:**
> I'm afraid I can't help you. If this problem is surmountable, changing the mount options is probably what you have to do.  I don't know how to do it, and for removeable media it might be especially tricky.

[http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221)

Adding to sudodus, here's a possibility that I spotted in [Bodhi Zazen's fstab guide]("http://ubuntuforums.org/showthread.php?t=283131").
[http://readlist.com/lists/vger.kernel.org/linux-kernel/22/111748.html](http://readlist.com/lists/vger.kernel.org/linux-kernel/22/111748.html)
Apparently writing to a vfat drive with this "sync" option can ruin it.

Thanks for this link :-) It is ten years old, but who knows, this sync option might still be activated.

---

### Post by detached2 on 2015-02-26
There is an actual physical switch to some pendrives locking and preventing  them from having data removed from them. See if this is the case to yours.

---

### Post by carl4926 on 2015-02-26
If you have access to windows
diskpart may be able to do it

---

### Post by Hazzabin on 2015-02-26
This link I used and was successful on 3 of my usb sticks that GParted would not could not do, hope it helps

[http://www.unixmen.com/how-to-format-usb-drive-in-the-terminal/](http://www.unixmen.com/how-to-format-usb-drive-in-the-terminal/)

---

### Post by matthew74 on 2015-02-27
i believe it gridlock, he going to ask my brother if he can fix it. i told him if it gridlock there nothing my brother can do

---

### Post by SuperFreak on 2015-02-27
Did you try the low level format I suggested?


[http://www.patriotmemory.com/forums/showthread.php?897-Low-Level-Format-Tool-Write-Protected-USB-%28Read-First-Post-on-Pg1-before-replying!%29](http://www.patriotmemory.com/forums/showthread.php?897-Low-Level-Format-Tool-Write-Protected-USB-%28Read-First-Post-on-Pg1-before-replying!%29)

[http://www.myusbtools.com/2013/06/silicon-power-low-level-formatter-v3700.html](http://www.myusbtools.com/2013/06/silicon-power-low-level-formatter-v3700.html)

you need to find the right tool for the manufacturer of the USB

---

### Post by matthew74 on 2015-02-28
ok i will try it later this week, been busy

---

