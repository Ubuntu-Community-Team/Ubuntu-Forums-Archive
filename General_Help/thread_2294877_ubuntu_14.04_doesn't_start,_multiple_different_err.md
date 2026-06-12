---
title: "ubuntu 14.04 doesn't start, multiple different error messages"
date: 2015-09-14
forum: General Help
---

### Post by Hanjonah on 2015-09-14
Hello, 

after not using my laptop for about 4 months, I now encounter a major problem since everytime I press the start bottom different error messages I cannot fully understand appear...

I do not recall all of them unfortunately but the first time it asked me to enter a Grub (?)( I dont recall ) password to enter. then 

off, on: boot menu. I wanted to run the memory test but there also appeared some error message. now the third time it just says:

error: font characters not in ascending order: 2330180294 < = 4288398843.
error: no suitable video mode found.
error: no video mode activated.
error: incompatible license.

( the incompatible license appeared before with the memory test as well as I recall and it doesn't sound good to me )

It would be great if someone could help me to find a way out of this. I wouldnt want to boot Ubuntu out of fear it would destroy all my data. As there is always some other error communicated to me once I switch the laptop on it woult be great if you could look into this poor information I could give you and help me out.

Thanks, 

Hanjonah

---

### Post by v3.xx on 2015-09-14
Try pressing

Ctrl + Alt + F1

See if you can login to console.  If you can; enter..

```
sudo apt-get -f install
```

---

### Post by Hanjonah on 2015-09-14
doesn't really work to press the keys.

 the error messages disappeared though, now I am just getting the gnu grub version 2.02 beta 9 ubuntu1 ... i have no clue of how it works, as ubuntu used to load automatically... if i just boot ubuntu with the gnu grub my data wont be harmed will it?

---

### Post by Bashing-om on 2015-09-14
Hanjonah; Hello;

@v3.xx :) Old friend, our threads cross once more .

Think if I were in this situation I would run a file system check/repair.
Do you have a liveDVD of 14.04 - the medium you installed 14.04 with -
As this check must be conducted with the target file system UN-mounted !

I do suggest to verify the file system's integrity, then look into the boot process failure.

[INDENT][INDENT][INDENT]just my thought
[/INDENT][/INDENT][/INDENT]

---

### Post by Hanjonah on 2015-09-14
hey, medium such as usb-stick I installed it with? I got the stick, yes, but it's not the boot stick anymore but in other use if you understand what I try to say?

> "As this check must be conducted with the **target file system UN-mounted !"**

what does this mean? and how do I conduct the check ( I really do have very little idea of ubuntu and usually try to find information in other posts but this time I d really like to do it all well because if I haven t used my lap in 4 months the last data back up unfortunately is even longer ago : S ) 


thanks mates

---

### Post by Bashing-om on 2015-09-14
Hanjonah; Hey ;

Running the file system check from the liveUSB is very simple.
Change the boot order in bios to USB as the 1st priority ;
Boot ubuntu in the "try ubuntu" mode to the desktop.
At the desktop, key combo ctl+alt+t will yield a terminal.
In this terminal - we want to KNOW what we are working with - execute terminal commands:
```

sudo fdisk -lu
sudo parted -l

```
Which will show your hard drive(s) and the partitioning; thus we know where ubuntu was installed to, and can give explicit direction to conduct the file system check.
Post back these results - Between Code Tags :
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Once the file system is verified, then we address booting up the install.
Depending on how you want to do this .. boot from grub and maybe fix grub from within, sometimes can not be done OR just (RE-)install grub from that liveUSB . If you want to learn the operating system, we 'fix', If time is of an essence then we (RE-)install grub.

[INDENT][INDENT]not at this time
[INDENT][INDENT][INDENT]a big thing
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Hanjonah on 2015-09-15
ok i ll try that once i have some time on my hand... just for the protocol today i started the lap and all that appeared was

```
GNU GRUB version 2.02 beta 2-9 ubuntu1

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub>

```

writing it down so I won't forget.

thank you I ll post back what the system check said whenever I am done with it!!

---

### Post by Hanjonah on 2015-09-15
so... I ve tried, stick, switch on, boot menu, selecting the correct usb device... waiting... and what appears is again the GNU GRUB version 2.02 (same old same old) as before... ?! umm... i cant really see a way to get to the "try ubuntu"... ?

---

### Post by yancek on 2015-09-15
You need to get into the BIOS setup to set the flash drive to first boot priority.  The key you need to press generally shows at the bottom of the screen for a few seconds.  If you are still getting the Grub message, it is going to the hard drive where there is obviously a problem with the Grub bootloader.

---

### Post by Hanjonah on 2015-09-16
Yes I did set the flash drive as first boot priority and in my case I can even manually choose once I am in the menu which usb input from I want to boot ( name of my usb stick so there cant be a misunderstanding ) - so I choose this bootable stick and then all I get is the Grub again... so how can I fix this? how risky is it just to boot the system after these error messages? I dont really get what could have happened after being switched off for 4 months?!

---

### Post by Bashing-om on 2015-09-16
Hanjonah; Well ....

My thought process remains the same, to boot up from the liveUSB and run a file system check on the install.
As the current liveUSB does not boot in this machine, does it boot in another ? Might be best to burn a new 14,04 .iso file to USB.

But to answer the question of booting the install from the "grub >" prompt, sure, we can try . Wont hurt a thing to try as until grub completes the operating system is not loaded or started. None of the operating systems files are touched.

In our case, because we do not know where the operating system files are located , will be a slow process of discovery.
We start this process of discovery from the install grub prompt result of terminal commands:
```

ls -lh
ls -lh (hd0,msdos1)

```
Maybe the operating system is installed to the 1st hard drive - hd0 - and on it's 1st partition - msdos1 . We need to find out where grub's files are installed on the hard drive, and be able to tell grub where grub can tell the kernel where the kernel's initiate files are located. Then we can boot the operating system IF these files are intact .

In the event we can not boot the system from the "grub >" prompt, it is back to booting up from a liveDVD(USB) and restoring the boot code.

[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT]

---

### Post by Hanjonah on 2015-09-28
Sorry to reply so late. here are the results of the fdisk etc !

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0004b4a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   968646655   484322304   83  Linux
/dev/sda2       968648702   976771071     4061185    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5       968648704   976771071     4061184   82  Linux swap / Solaris

Disk /dev/sdb: 31.0 GB, 31029460992 bytes
255 heads, 63 sectors/track, 3772 cylinders, total 60604416 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x49464555

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    60604415    30301184    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA ST500LM000-1EJ16 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  496GB  496GB   primary   ext4            boot
 2      496GB   500GB  4159MB  extended
 5      496GB   500GB  4159MB  logical   linux-swap(v1)


Model: Verbatim STORE N GO (scsi)
Disk /dev/sdb: 31.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  31.0GB  31.0GB  primary  fat32        boot, lba



```

---

### Post by Hanjonah on 2015-09-28
not to forget this>

```
ubuntu@ubuntu:~$ ls -lh
total 0
drwxr-xr-x 2 ubuntu ubuntu 80 Sep 28 18:24 Desktop
drwxr-xr-x 2 ubuntu ubuntu 40 Sep 28 18:24 Documents
drwxr-xr-x 2 ubuntu ubuntu 40 Sep 28 18:24 Downloads
drwxr-xr-x 2 ubuntu ubuntu 40 Sep 28 18:24 Music
drwxr-xr-x 2 ubuntu ubuntu 40 Sep 28 18:24 Pictures
drwxr-xr-x 2 ubuntu ubuntu 40 Sep 28 18:24 Public
drwxr-xr-x 2 ubuntu ubuntu 40 Sep 28 18:24 Templates
drwxr-xr-x 2 ubuntu ubuntu 40 Sep 28 18:24 Videos
ubuntu@ubuntu:~$ ls -lh (hd0,msdos1)
bash: syntax error near unexpected token `('
ubuntu@ubuntu:~$ 


```

---

### Post by Bashing-om on 2015-09-28
Hanjonah; Hey hey :

Keeping in mind, running a file system check would be a great thing to do; But, we can see what results when we boot the system up from the "grub >" prompt.

At the dismaying "grub >" prompt,
enter terminal commands:
```

set prefix=(hd0,msdos1)/boot/grub
set root=(hd0,msdos1)
insmod linux
linux (hd0,msdos1)/vmlinuz root=/dev/sda1 ro
initrd (hd0,msdos1)/initrd.img
boot

```
As we know now that linux is the only operating system installed and that our only concern is a single hard drive (sda) and we also know that the operating system is installed to that 1st partition.

So, with the above, do you boot to the GUI login screen ? A good possibility then that we can (RE-)install grub from this install.

[INDENT][INDENT]it could happen
[/INDENT][/INDENT]

---

### Post by Hanjonah on 2015-09-28
ok i tried. the screen was blank and i waited for about.. 10 minutes. now i got this: 

```
uncompression error

-- system halted
```

any opinions?

---

### Post by Bashing-om on 2015-09-28
Hanjonah' Ouch !

Is that " uncompression error " from when you actually attempt to boot up the install ?
IF that is from the install OS and NOT booting the live environment .. then
I guess we are going to have to boot up a liveDVD(USB), CHange Root into the install; and rebuild the initramfs image .

Might be better troubleshooting technique to attempt to (RE-)install grub from that live environment .

Let's make sure we are on the same page here and that you are attempting to boot the install, and in this attempt you are getting only as far as the grub > prompt . Where we are and where we are looking to, sure makes a difference in what we do .

[INDENT][INDENT]what does it take to make
[INDENT][INDENT][INDENT]grub
[INDENT][INDENT][INDENT][INDENT]satisfied
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Hanjonah on 2015-09-28
I was in the grub and pressed the Boot ubuntu - option. I am sorry but I thought thats what you meant when saying boot the install? ( my technical english is not that good unfortunately )

---

### Post by Bashing-om on 2015-09-28
Hanjonah; Hey;

English is my first and only language, and I am not too well versed in it . I will try and exercise greater care .

To be the more exact in what we are doing;
Boot the install to the grub boot menu. with ubuntu selected to boot, press the 'c' key for a command line ->
you should now be at the grub > prompt.
- IF this is not the case, you do not get the normal grub boot menu, stop, we try another means to get to the grub boot menu - 

At this point enter the commands in this grub > prompt environment :
```

set prefix=(hd0,msdos1)/boot/grub
set root=(hd0,msdos1)
insmod linux
linux (hd0,msdos1)/vmlinuz root=/dev/sda1 ro
initrd (hd0,msdos1)/initrd.img
boot

```

If at any time you get errors, again stop and advise on what the error is .
The magic sys request key sequence will reboot the system gracefully:
 [http://unix.stackexchange.com/questions/31818/what-to-do-when-a-linux-desktop-freezes](http://unix.stackexchange.com/questions/31818/what-to-do-when-a-linux-desktop-freezes)

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by Hanjonah on 2015-09-28
hey, 

thank you. I understand perfectly well the words you use but in this context they sometimes dont make much sense to me ; ) 

anyways, we keep learning always...

there was no problem until I entered

```
initrd (hd0,msdos1)/initrd.img 
```

then I got:

```
error: such partition doesnt exist 
```

so I didn-t enter the "boot" command.

what does this mean?

---

### Post by Bashing-om on 2015-09-28
Hanjonah; Well ..

Looks like if there were a problem with " initrd (hd0,msdos1)/initrd.img" it would have been uncovered in the afore command for 'linux' . Maybe just a typo try again ?

Else; well .... 
let's look and see what the system reports for that location:
At the grub > prompt:
```

search -f /vmlinuz
search -f /initrd.img
ls -lh (hd0,msdos1)/
ls -lh (hd0,msdos1)/vmlinuz
ls -lh (hd0,msdos1)/boot

```

IF it turns out the files are not present. will have to boot up a liveDVD and install grub.

[INDENT][INDENT]if at 1st you do not succeed
[INDENT][INDENT][INDENT]try something else
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Hanjonah on 2015-09-29
thank you. these are the results:

```
   [CODE]
 search -f /vmlinuz hd0, msdos1 

search -f /initrd.img 

hd0, msdos1 

ls -lh (hd0,msdos1) ORDN 2015-01-21 18:29:04 Wednesday lost+found/ 
ORDN 2015-06-10 18:37:32 Wednesday etc/ 
ORDN 2015-05-08 18:21:40 Friday media/ 
ORDN 2015-04-12 17:15:54 Sunday bin/ 
ORDN 2015-05-06 14:55:43 Wednesday boot/ 
ORDN 2014-07-22 22:23:56 Tuesday dev/ 
ORDN 2015-01-21 18:33:26 Wednesday home/
 ORDN 2015-03-05 10:38:38 Thursday lib/ 
ORDN 2015-03-05 10:38:39 Thursday lib64/ 
ORDN 2014-04-10 22:12:14 Thursday mnt/ 
ORDN 2015-03-05 20:27:21 Sunday opt/ 
ORDN 2014-04-10 22:12:14 Thursday proc/ 
ORDN 2015-05-12 05:51:25 Tuesday root/ 
ORDN 2014-07-22 22:25:59 Tuesday run/ 
ORDN 2015-05-04 14:56:01 Monday sbin/ 
ORDN 2014-07-22 21:57:18 Tuesday srv/ 
ORDN 2014-03-12 01:41:52 Thursday sys/
 ORDN 2015-06-10 18:37:32 Wednesday tmp/ 
ORDN 2014-07-22 21:57:18 Tuesday usr/ 
ORDN 2014-07-22 22:28:08 Tuesday var/ 
5.55M 2015-05-06 14:55:25 Wednesday vmlinuz
 18.32M 2015-05-06 14:55:25 Wednesday initrd.img 
ORDN 2015-01-21 18:31:35 Wednesday cdrom/ 
18.32M 2015-04-12 17:15:56 Sunday initrd.img.old 
5.55M 2015-04-12 17:15:56 Sunday vmlinuz.old 



ls -lh
(hd0,msdos1)/vmlinuz 


ls -lh
(hd0,msdos1)/boot 





ORDN 2015-05-05 14:55:45 Wednesday grub/ 
3.22M 2014-07-15 04:29:01 Tuesday System.map-3.13.0-32-generic 
1.11M 2014-07-15 04:29:01 Tuesday abi-3.13.0-32-generic 
161.86 2014-12-16 01:17:05 Tuesday config-3.13.0-44-generic 
5.54M 2015-01-13 20:12:53 Tuesday vmlinuz-3.13.0-45-generic 
161.86K 2015-01-13 20:12:53 Tuesday config-3.13.0-45-generic 
1.11M 2015-03-10 20:43:00 Tuesday abi-3.13.0-45-generic 
3.23M 2015-01-13 20:12:53 Tuesday System.map-3.12.0-45-generic 
18.32M 2015-01-31 11:32:41 Saturday initrd.img-3.13.0-45generic 
18.32M 2015-02-19 16:14:47 Thursday initrd.img-3.13.0-45generic 
5.55M 2015-03-10 20:43:00 Tuesday vmlinuz-3.13.0-46-generic 
161.86K 2015-03-10 20:43:00 Tuesday config-3.13.0-46-generic 
1.11M 2015-03-12 11:52:18 Thursday abi-3.13.0-46-generic
 3.23M 2015-03-10 20:43:00 Tuesday System.map-3.13.0-48-generic 
18.32M 2015-03-17 16:44:45 Tuesday initrd.img-3.13.0-46-generic 
161.89K 2015-03-12 11:52:18 Thursday config-3.13.0-48-generic
 3.23M  2015-03-12 11:52:18 Thursday System.map-3.13.0-48-generic
 5.55M 2015-04-10 21:05:00 Friday vmlinuz-3.13.0-49-generic 
5.55M 2015-03-12 11:52:18 Thursday vmlinuz-3.13.0-48-generic
 18.32M 2015-04-05 22:26:23 Sunday initrd.img-3.13.0-48-generic 
161.89K 2015-04-10 21:05:00 Friday config-3.13.0-49-generic 
1.11M 2015-04-05 22:26:23 Sunday abi-3.13.0-49-generic 
3.23M 2015-04-29 17:38:21 Wednesday System.map-3.13.0-52-generic
 3.23M 2015-04-10 21:05:00 Friday System.map-3.13.0-49-generic 
18.32M 2015-04-20 11:23:40 Monday initrd.img-3.13.0-49-generic 
161.88K 2015-04-29 17:38:21 Wednesday config-3.13.0-52-generic 
1.11M 2015-04-29 17:38:21 Wednesday abi-3.13.0-52-generic 
5.55M 2015-04-29 17:38:21 Wednesday vmlinuz-3.13.0-52-generic 
18.32M 2015-05-06 14:55:43 Wednesday initrd.img-3.13.0-52-generic 


```

---

### Post by Bashing-om on 2015-09-29
Hanjonah; Yikes !

I have never seen such an output !
What is " ORDN " ?

I am going to copy off that output to my system and boot grub and compare my outputs to what you have provided before we go any further.
Will be some time later before I reboot.

Now it has
[INDENT][INDENT][INDENT]really got me quessing
[/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-09-29
Hanjonah; OK;

A bit of homework on my part done, I wish I could provide the grub command outputs, but I do not have access to a digital camera.

However, thus far it seems that the files we need to boot are inplace.
What also rerurns:
At that grub > prompt :
```

ls (hd0,msdos1)/boot/grub/

```
in the output do you see " grub.cfg " of some significant size ?.

And we try again to boot this install.

[INDENT][INDENT][INDENT]it could happen
[/INDENT][/INDENT][/INDENT]

---

### Post by Hanjonah on 2015-09-30
all I get is: 

```
gfxblacklist.txt i386-pc/ locale /fonts/ grubenv grub.cfg
```

Is there no way to access the data on the hard drive other than fixing these issues?

---

### Post by Bashing-om on 2015-09-30
Hanjonah; Morning ;

Well, again the files we need are present :
```

sysop@1404mini:~$ ls -al /boot/grub/
total 2464
drwxr-xr-x 5 root root    4096 Sep 28 11:55 .
drwxr-xr-x 4 root root    4096 Sep 28 11:55 ..
drwxr-xr-x 2 root root    4096 Jun  9  2014 fonts
-rw-r--r-- 1 root root     699 Jun  9  2014 gfxblacklist.txt
-r--r--r-- 1 root root   44734 Sep 28 11:55 grub.cfg
-r--r--r-- 1 root root   30941 Oct 14  2014 grub.cfg-broke.lubie
-rw-r--r-- 1 root root    1024 Sep 30 09:49 grubenv
drwxr-xr-x 2 root root   12288 Jul  8 11:10 i386-pc
drwxr-xr-x 2 root root    4096 Jul  8 11:10 locale
-rw-r--r-- 1 root root 2405285 Jul  8 11:10 unicode.pf2
sysop@1404mini:~$

```

And yes:
> 
Is there no way to access the data on the hard drive other than fixing these issues?

One can boot up a liveDVD(USB), mount the install's root partition and copy off the desired data. No big deal.

As the boot files on your install all appear to be present, how about we attempt to boot with as few grub directives as possible and see if the install boots ?
From that grub prompt :
```

linux (hd0,msdos1)/vmlinuz root=/dev/sda1 ro
initrd (hd0,msdos1)/initrd.img
boot

```
Where we are telling grub where it's config files are - hard drive zero, partition type msdos and the 1st partition; and grub is telling the kernel where it's config files are located (/dev/sda1 so the kernel knows the inititiating files are located at grub speak (hd0,msdos1).

We do have several options:
Boot the install as is .. and repair the boot files;
Boot a liveDVD(USB) and (RE-)install the boot code ;
Boot a liveDVD(USB) copy off the desired files and (RE-)install the operating system - IF/when your frustration gets the better of you.

By far I prefer to find the fault and correct it, but it is your call on how we proceed.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Hanjonah on 2015-10-06
okay, again sorry for interrupting this question and help flow but i couldnt handle carrying two laptops for the past days. again i don*t exactly get what you mean but I would love to copy all the data first on my harddrive because i need it available and then continue to fix the problem. data saving is first, problem solving afterwards sounds good to me.

um.... so what should i do again? how can i copy the desired files with the live usb?? i tried to access my data from the -try ubuntu- version but i couldnt, the folder was empty : S

best, hanjonah

---

### Post by Bashing-om on 2015-10-06
Hanjonah; Yikes !

Are we fanning at ghosts ?
> 
 i tried to access my data from the -try ubuntu- version but i couldnt, the folder was empty : S

Scary thought ! Let's get a direct look at things from the liveUSB.
I work best from terminal .
Boot the liveUSB to try ubuntu mode and activate a terminal:
post back the results of terminal commands:
```

sudo fdisk -lu
sudo parted -l

```
to get the partitions locations to allow us to know the mount points.
Once these are known we can certainly mount the file system(s) from the liveUSB and have a look at what is there; then copy the data off - IF it exists.

[INDENT][INDENT]terminal is our best friend
[/INDENT][/INDENT]

---

### Post by Hanjonah on 2015-10-07
ok bashing-om, I have no clue why, but one week ago I couldnt find my data, now I just gave it a shot again and it was all there?! I am not asking how and why it is just awesome. So.... right now I am backing up everything and super happy ;  )  now if you like we can proceed to solve the problem : )

---

### Post by Hanjonah on 2015-10-07
oh and just for the record:

```
[FONT=Verdana] ubuntu@ubuntu:~$ sudo fdisk -lu
  Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0004b4a2
     Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   968646655   484322304   83  Linux
/dev/sda2       968648702   976771071     4061185    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5       968648704   976771071     4061184   82  Linux swap / Solaris
  Disk /dev/sdb: 31.0 GB, 31029460992 bytes
255 heads, 63 sectors/track, 3772 cylinders, total 60604416 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x49464555
     Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    60604415    30301184    c  W95 FAT32 (LBA)
   
   ubuntu@ubuntu:~$ sudo parted -l
Model: ATA ST500LM000-1EJ16 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
  Number  Start   End    Size    Type      File system     Flags
 1      1049kB  496GB  496GB   primary   ext4            boot
 2      496GB   500GB  4159MB  extended
 5      496GB   500GB  4159MB  logical   linux-swap(v1)
  
Model: Verbatim STORE N GO (scsi)
Disk /dev/sdb: 31.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
  Number  Start   End     Size    Type     File system  Flags
 1      1049kB  31.0GB  31.0GB  primary  fat32        boot, lba
  
Model: WD My Passport 0820 (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
  Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ntfs
   
 
   

 
 
[/FONT]

```

---

### Post by Bashing-om on 2015-10-07
Hanjonah; Hey ...

Good news that the data is all there !

OK, we want to know why the system is not booting. And then fix it !
To that end let's try a 'simple' boot from grub.
Boot the install to the grub boot menu;
In this menu of kernel boot options with the latest kernel selected, press the 'c' key for a command line interface -> 
You now have a 'grub >' prompt.
enter terminal commands:
```

linux (hd0,msdos1)/vmlinuz root=/dev/sda1 ro
initrd (hd0,msdos1)/initrd.img
boot

```Where we tell grub where it's config files are and grub can tell the kernel where it's files are located.
Do you boot to the GUI login ? No, what errors does the system report  ( what else do we have to tell grub ) ?

[INDENT][INDENT]it is all in the process
[/INDENT][/INDENT]

---

### Post by Hanjonah on 2015-10-08
uhm.... so i tried... first it was all moving letters and i read a lot of error and failings - then it turned all black. after a while i tried to switch it off and it appeared again, a series of trials as it appeared to me. then the laptop suddenly switched off. i turned it on again and ran the same commands. now i am sitting in front of a not moving something. seems like it checked usb devices? there is also something saying

```


busy box v1.21.1 (ubuntu 1:1.21.1.0-1ubuntu1) built-in shell (ash)

enter help for a list of built-in commands.

(initramfs) [5.379754] usb ...... 
```

and then it just lists the usb inputs... in the end it says: switched to clocksource tsc.

then i just clicked enter and now I could enter anything after "initramfs"

.... uhm

---

### Post by Bashing-om on 2015-10-08
Hanjonah; UnGood !

Indicates to me that grub is not happy with it's config files. Now we could futz around and try and identify the file(s) that are bad OR we can just rebuild them IF you have on hand the liveDVD(USB) of what is installed to the hard drive. Best done with a Wired internet connection . Booting into the install may be a long long process .

In respect to the reported errors about a USB device .... did you try and boot the install with a USB drive connected ? Have you at some point edited the file /etc/fstab ?

Depends on what you want to do .. find the fault and fix it - and we both learn a lot - ... or take the easy way out and just replace the files. Even replacing the files will be a learning experience for you .. Booting the live environment and Changing the Root into that of the install .. and once CHrooted, rebuild grub .

[INDENT][INDENT]It is your time
[INDENT][INDENT][INDENT]your effort
[INDENT][INDENT][INDENT][INDENT]your call
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Hanjonah on 2015-10-08
okay, well unfortunatey i m running out of patience with my other old device and it would be marvelous to do the not that time intensive operation which means to rebuild or replace the files? i mean how much time do you think the learning and understanding process might take? i ll be on the road again unfortunately but i d try to do something tonight or tomorrow morning before i leave or after the weekend or so?

---

### Post by Bashing-om on 2015-10-08
Hanjonah; Hey !

IF you have on hand a LiveDVD(USB) and are on a wired internet connection. Will only take a few minutes to replace grub on the install . The more familiar you are with the terminal, and the more confident you are with the commands, the quicker it will be.

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by Hanjonah on 2015-10-08
all here. so what would i have to do exactly ; ) ?

---

### Post by Bashing-om on 2015-10-08
Hanjonah; K ...
Nothing to it .. 
Boot the liveUSB to terminal and execute (copy and paste !):
```

sudo mount /dev/sda1 /mnt
for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done
sudo chroot /mnt
ping -c3 ubuntu.com

```
IF and only if you get a postive response from the ping command:
> 
3 packets transmitted, 3 received, 0% packet loss, time 2000ms


Rebuild grub .. we will invoke a wizard to do this:
```

dpkg-reconfigure grub-pc

```
In this wizard you will be presented with a choice of where to install grub. Install to 'sda' ... I say again you want to install to the MBR of the drive that contains ubuntu .. it is 'sda' -
Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions - in your use case choose 'sda' !

OK... once done with rebuilding grub exit all out:
```

exit
sudo umount /mnt/run 
sudo umount /mnt/dev/pts
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt/dev
sudo umount /mnt

```

OK.. so far so good .. reboot and set in bios to boot the hard drive ..
Boot the install on the hard drive
in the install execute:
```

sudo update-grub
sudo apt update
sudo apt full-upgrade
sudo update-grub ##yeah, cheap insurance##

```

Reboot once more and tell me

[INDENT][INDENT]all is finer than a frog's hair
[/INDENT][/INDENT]

---

### Post by Hanjonah on 2015-10-16
hey! thank you so much. i did as you told me and now everything just works perfectly fine! :D

---

### Post by Bashing-om on 2015-10-16
Hanjonah; Great !

You do good work;

Now that " all is finer than a frog's hair " :
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

---

