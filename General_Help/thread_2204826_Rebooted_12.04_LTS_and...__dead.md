---
title: "Rebooted 12.04 LTS and...  *dead*"
date: 2014-02-10
forum: General Help
---

### Post by IPvFletch on 2014-02-10
I am at my whit's end here. I installed 12.04 and OpenStack and had everything all perfect. I rebooted 3-4 times without any problems whatsoever. I rebooted once more and ... nothing. It doesn't even show me a kernel panic. It goes through the BIOS and then shows a few lines move past with whitepsace and then half a line and then it stops. Nothing after this.

I have no idea if grub2 is loading or not, either. I put my Ubuntu 12.04 installer USB drive in and chose the Rescue instance. It boots up and lets me mount my drive (/dev/sdb 500GB SATA; /dev/sda is my 3GB USB HDD). I ran through grub-update and tried - still nothing. I even turned on the grub menu timeout to 20s and don't even see that load when I reboot. It's like grub2 isn't even getting invoked. fdisk -l /dev/sdb tells me sdb1 is * meaning it has mbr loaded onto it. I tried grub-install /dev/sdb and it works fine, but still nothing when I reboot. I also tried 'apt-get install --reinstall linux-image-generic linux-image' on my chrooted /dev/sdb1 mounted on /target, and it went through and rebuilt the boot files and re-ran grub-update for me. Still nothing when I reboot. Every time I get the same result.

FWIW, I'm using a serial console as input. BIOS and Grub both have redirected outputs to ttyS0. I also did this for my USB HDD Ubuntu installer image. Each time I see the boot msgs just fine. It's when I boot off my main SATA HD that I get nothing.

I switched the order of my drives and the SATA HDD boots first (and hangs), and it doesn't ever skip and go to my 2nd drive (USB HDD). I put the order back to USB HDD first so I can boot into Rescue some more.

I don't know what else to try..

A. I spent too much time on this system to just junk it and re-install (assuming that even works)
B. I don't want to spend more time rebuilding if this will just happen again!

All I did in the last boot (I was able to see my .bash_history on my mounted drive LOL!!) was edit some OpenStack files and restart nova-compute and such. I did restart memcached but I doubt seriously that had anything to do with this. For giggles, I tried turning off mem caching in the BIOS and still it won't boot up. I turned it back on now just in case.

Any ideas what else I can try?

I can get to all my files via Rescue disk but I can't seem to make it bootable again. I was thinking would re-installing grub when it's mounted as /dev/sdb cause a problem when it boots normally it is /dev/sda?  (Ubuntu Rescue USB HDD is making it sdb while USB HDD is sda, which seems to make sense). But when I yank the USB drive my SATA HDD should boot as /dev/sda1.

Any ideas are welcome...  Thanks!

---

### Post by Bashing-om on 2014-02-10
IPvFletch; Hi !

I'll take a stab at this.
One may only have one grub as the primary controlling boot directive.
What drive do you use as the "primary" operating system ? That is where you want the "control" grub installed to.

Show us what we are working with, post the output of terminal commands:
```

sudo fdisk -lu
sudo parted -l

```

I triple boot on my system, my primary is sda and often enough I do break grub. I have had to restore the boot order several times. 

oldfred's advise is to disable os-prober to prevent this, but fixing grub is no big deal.

[INDENT][INDENT]all things are doable
[/INDENT][/INDENT]

---

### Post by IPvFletch on 2014-02-10
I tried this script and output looks mostly ok... [[ATTACH]250252[/ATTACH]]("http://bootinfoscript.sourceforge.net/")

[URL="http://bootinfoscript.sourceforge.net/"]http://bootinfoscript.sourceforge.net/


[/URL]

---

### Post by IPvFletch on 2014-02-10
> **Bashing-om said:**
> IPvFletch; Hi !

I'll take a stab at this.
One may only have one grub as the primary controlling boot directive.
What drive do you use as the "primary" operating system ? That is where you want the "control" grub installed to.

Show us what we are working with, post the output of terminal commands:
```

sudo fdisk -lu
sudo parted -l

```

I triple boot on my system, my primary is sda and often enough I do break grub. I have had to restore the boot order several times. 

oldfred's advise is to disable os-prober to prevent this, but fixing grub is no big deal.[INDENT][INDENT]all things are doable
[/INDENT]
[/INDENT]

I only have one drive (so I guess it's always /dev/sda). I put in a USB HDD (thumb drive) temporarily to boot into Rescue live CD (on my USB drive) hence the temp kernel is calling my USB drive /dev/sda and my SATA HD is called /dev/sdb but normally I just boot with the one SATA HDD in there. Here's the outputs you requested, thanks...

```
# fdisk -lu

Disk /dev/sda: 4090 MB, 4090494976 bytes
255 heads, 63 sectors/track, 497 cylinders, total 7989248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x80820dc6


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63     7164989     3582463+   b  W95 FAT32


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000226d0


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   968386559   484192256   83  Linux
/dev/sdb2       968388606   976771071     4191233    5  Extended
/dev/sdb5       968388608   976771071     4191232   82  Linux swap / Solaris



```

```


# parted -l
Model: CBM USB 2.0 (scsi)
Disk /dev/sda: 4090MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  3668MB  3668MB  primary  fat32        boot




Model: ATA External Disk 0 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size    Type      File system     Flags
 1      1049kB  496GB  496GB   primary   ext4            boot
 2      496GB   500GB  4292MB  extended
 5      496GB   500GB  4292MB  logical   linux-swap(v1)






```

---

### Post by Bashing-om on 2014-02-10
IPvFletch; Well, Well,

this:
> 
--class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='(hd1,msdos1)'
        search --no-floppy --fs-uuid --set=root d8f00bf3-5736-43bc-a4b3-e5fbb2cb
7191

"hd1,msdos1" is device #2 (counting starts at 0), 1st partition; that then is sdb, the internal hard drive in this case.

 All looks good until ->
The final line in the bootscript text file is cause for concern.

Let's try an easy approach to the situation//Maybe !

In small steps, so I know where we are.
1. Bios set to boot the USB as 1st boot priority;
Boot the liveUSB -> "try ubuntu"  -> activate a terminal
2. I want to know what the system now sees for that internal drive - at this time -
```

sudo fdisk -lu

```
3. Now. without rebooting from that live usb, when I have that above info, let's try and (RE-)install grub to the MBR of the internal drive.
All work will be done from the liveUSB environment, so do not reboot ! so the identifiers remain constant.

[INDENT][INDENT]all we can do is try
[/INDENT][/INDENT]

---

### Post by IPvFletch on 2014-02-10
Only when there is a USB thumbdrive in does it detect it as sda, otherwise I think my internal drive is sda usually (when no thumbdrive is present).

Here's what it looks like when I boot off the thumbdrive (top is thumbdrive, bottom is internal HD):

```
# fdisk -lu

Disk /dev/sda: 4090 MB, 4090494976 bytes
255 heads, 63 sectors/track, 497 cylinders, total 7989248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x80820dc6


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63     7164989     3582463+   b  W95 FAT32


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000226d0


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   968386559   484192256   83  Linux
/dev/sdb2       968388606   976771071     4191233    5  Extended
/dev/sdb5       968388608   976771071     4191232   82  Linux swap / Solaris

```

If I do a grub-install /dev/sda it kills my thumbdrive and I have to re-image it. Ask me how many times I did this late last night. :D

If I update-grub while chrooted to / (mounted as /dev/sdb1) then it still fails to boot when I yank the USB thumbdrive and reboot. I think the thumbdrive takes over sda when it is inserted but when it's not inserted my internal HD becomes sda.

I'm waiting for your reply before doing anything else..

If this helps:

```

# blkid
/dev/sda1: LABEL="3GB" UUID="CC6A-DDD7" TYPE="vfat"
/dev/sdb1: UUID="d8f00bf3-5736-43bc-a4b3-e5fbb2cb7191" TYPE="ext4"
/dev/sdb5: UUID="b31e90ab-948d-4661-835d-06198a77315f" TYPE="swap"

```
I read about setting the root drive to /dev/sda1 instead of the UUID. Maybe we can try that?

I'm wondering if the hd1,msdos1 should be hd0,msdos1 (msdos??) when I yank the USB drive cuz then my internal drive is the 1st...  ??  BTW I have just put this in my grub config just in case:  GRUB_PRELOAD_MODULES="part_msdos"

---

### Post by Bashing-om on 2014-02-10
IPvFletch; OK,

Not rebooted, so the system still sees that internal hard drive as "sdb":
And still in the liveUSB; Terminal commands:
```

sudo mkdir /mnt/work
sudo mount /dev/sdb1 /mnt/work
sudo grub-install /dev/sdb
sudo umount /mnt/work

```

Now reboot to bios, and reset the boot priority to the internal hard drive, continue the boot process.

Now exactly what results ? Fingers crossed, all is good now.

[INDENT][INDENT]hey it could happen
[/INDENT][/INDENT]

---

### Post by IPvFletch on 2014-02-10
You mean mount /dev/sdb_1_ /mnt/work?

Also don't I need to chroot /mnt/work first?

---

### Post by Bashing-om on 2014-02-10
IPvFletch; Me still scatter brained !

Yeah . Should be sdb1 ! - we want to mount a partition ! -
And a chroot not required at this time.. mounting the partition should be just fine!

Good catch !

[INDENT][INDENT]duh, to err is human
[/INDENT][/INDENT]

---

### Post by IPvFletch on 2014-02-10
Well I can't run grub-install unless I chroot into /mnt/work because it's not in the right place. Also /etc/default/grub is not in /etc it's in /mnt/work/etc/default/grub unless I chroot.... lmk.

---

### Post by oldfred on 2014-02-10
When flash drive is plugged in, your BIOS promotes that to sda. I see that sometimes or it may just be that you ddi not use the first port on motherboard and flash drive then becomes sda.

But the UUID and search by UUID is supposed to override the drive setting change so it finds the correct partition to boot from.
I might try changing to hd0.
Partitions are msdos (MBR) or gpt (GUID) , and that helps it know which you have. 

Some also at grub menu manually edit out search line and make sure hd0,1 setting is correct or remove set root and only use search line. Either should work if correct.

Grub does not use boot flag, that is for Windows. But a few BIOS only boot if you have a boot flag on a primary partition as Windows requires, so we still suggest a boot flag. Do not install grub to a partition as that will not let you boot unless you do a work around with a Windows boot loader. Grub2 does not really fit in partition anymore so it converts to blocklists or hard coded addresses which often require you to reinstall.

---

### Post by Bashing-om on 2014-02-10
IPvFletch : Hey,

see oldfred's last.

That sequence should work; else I will craft another, if that is still giving you trouble.

the path from the liveUSB is correct. And we are dealing only with the leagacy partioinging "msdos", so we want grub installed to "sdb".

[INDENT][INDENT]keep plugging away
[/INDENT][/INDENT]

---

### Post by IPvFletch on 2014-02-10
@Bashing-on I can't run grub-install unless I mount all the partitions and use --bind to bind /dev and /proc and /sys etc and then chroot to it. So I did that and I got grub-install /dev/sdb to run and it said it returned no errors. I'll try a reboot in a sec and report back..

@oldfred - I was thinking of making this change:
```

[COLOR=#000000][I]set root='(hd1,msdos1)'
to
[/I][/COLOR][COLOR=#000000]*set root='(hd0,msdos1)'*[/COLOR]
```I would make ^ that ^ change, but grub-update puts it into /boot/grub/grub.cfg but can I just modify that file by hand and then reboot?  This stuff isn't in /etc/default/grub...  ??

---

### Post by Bashing-om on 2014-02-10
IPvFletch; Great !

Do not know why you have to "--bind", maybe because the live environment is a USB - rather than a DVD ? .. maybe ?
A lot I just do not know.
To be honest, this is the 2nd time I have encountered that mounting the partiton attempting to install grub did not work.
This on that other time did:
```

sudo grub-install --boot-directory=/mnt/work /dev/sda

```

One MAY hand edit /grub.cfg, but the change will not persist a update-grub. If ya look at /etc/grub.d/10_linux you will find that is the source, and - maybe - changing the entry there will effect what you want. - But should not be necessary as the system "should" keep track of what is.

As you do know how to operate in a chroot environment, will not hurt to back up 10_linux and make the change and see what does result.

If you have now rebooted, be a good thing to :
```

sudo update-grub

```
at this time, prior to (re)booting again.

[INDENT][INDENT]We will get to the bottom of this.
[/INDENT][/INDENT]

---

### Post by oldfred on 2014-02-10
If editing grub boot stanza, best to test at grub menu. 
If only booting Ubuntu hold shift from BIOS until you get menu.

Then use e for edit, to experiment with changes to grub menu or to boot.

I think all of the boot stanza is built with the scripts, but if you can boot into system without flash drive, then drive should default to sda. And this will reset it correctly.
sudo update-grub

---

### Post by IPvFletch on 2014-02-10
Well, still no luck. It's like everything I do just has no effect. I even tried holding SHIFT from BIOS (all through BIOS POST too). It still does the same thing. Nothing. Just a line or two of whitespace then the cursor stops moving and nothing ever happens.

It's almost like the HDD driver isn't being loaded or something. But if that were the case, why is my Live CD (USB HDD) able to mount /dev/sdb1 no problem and read/write to it?

I wonder if it isn't lower-level than grub. Like something with the partitions or MBR..  ??

---

### Post by Bashing-om on 2014-02-10
IPvFletch; Strange to say the least.

Is this something that just happened after an update, or is this on a fresh install ?

As you can chroot into the system, does not make sense it is a file system issue (??).

Is bios handing off to the boot sector @ the internal drive ? - what boot options do you have in bios ?


[INDENT][INDENT]Think'n
[/INDENT][/INDENT]

---

### Post by IPvFletch on 2014-02-10
Only options in BIOS are choose which boot device order. It sees my 500GB drive. I just don't get it!   I'm fairly certain if I re-install it will fix it. But I don't want to do that!!! :(

---

### Post by Bashing-om on 2014-02-10
IPvFletch: well,

Let's poke at it a bit and see what happens.

Boot the liveusb; soon as the bios screen clears, depress and hold the left shift key -> language screen, escape key to accept the default; -> Boot options screen.

Try "boot from 1st hard disk" :

What now results ?

[INDENT][INDENT]look'n to find a reason
[/INDENT][/INDENT]

---

### Post by IPvFletch on 2014-02-10
OK, that booted the Live CD (which is the first HD technically).  :)  I need an option 'boot 2nd HD'.   :)   Can I pull the USB HD and stick it in my PC and modify the syscfg file to include a new option Boot from 2nd disk and just increment the disk by one letter/number?  I could try that...  thoughts before I do it?

---

### Post by Bashing-om on 2014-02-10
IPvFletch; Yuk !

I am presently stuck with what to do.
My ignorance is showing, as I have never had the experience of using a liveUSB.
Recon what would happen if we were to make a new grub.cfg file ?
Something along the lines:
```

sudo grub-mkconfig -o /boot/grub/grub.cfg

```
If one were in the install, or maybe in the chroot environment ?
Probably still pick up the USB as the default drive to install on (??) .

[INDENT][INDENT]still thinn'n
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-02-10
IPvFletch; Maybe ?

```

sudo grub-install grub-pc

``` Will bring up a install wizard, where space-bar to select drive, tab to OK, enter to accept ->

That will give greater control and visibility on installing grub.

[INDENT][INDENT]worth a shot
[/INDENT][/INDENT]

---

### Post by IPvFletch on 2014-02-10
```
# grub-install grub-pc
/usr/sbin/grub-probe: error: cannot stat `grub-pc'.
```

Yet 'grub-install /dev/sdb' and 'update-grub' work fine.  *shrug*

BTW, I did manually change /boot/grub/grub.cfg 'hd1,msdos1' to 'hd0,msdos1' and rebooted. Still nothing.

UGH!!!!!!!!!

---

### Post by Bashing-om on 2014-02-10
IPvFletch; Yuk !

This is a first for me in that we are unable to effect a change in the boot sector's code.
It is back to the drawing board for me and see what I can come up with.

Consider purging grub and (RE-)install ?? BUT, "/usr/sbin/grub-probe: error: cannot stat `grub-pc'." Causes me deep concern.
Maybe best to (RE-)install grub in pieces - (2) the best I recall !

Back as soon as I have news.

Now ->
[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-02-10
IPvFletch; OK,

Let's say that the boot sector is corrupted, as several indicators do indicate. I do propose to purge grub and try and (re-)install:

Chroot environment:
```

sudo fdisk -lu ##To make sure of the Hard drive's identity
sudo apt-get remove --purge grub grub-pc grub-common
sudo apt-get install grub-pc
sudo grub-mkconfig
sudo update-grub
sudo grub-install /dev/sdb

```
I would not be surprised if "apt-get install grub-pc" complains about dependency issues, if so we will try and cope with it.

Now I have reached the limits of sure thinkability for this session. Will pick this up once more in my AM.

[INDENT][INDENT]Just what I think
[/INDENT][/INDENT]

---

### Post by IPvFletch on 2014-02-10
OK so I did the remove/purge and that went OK. I did the install grub-pc and it gave me that text-based wizard, and that went OK, but here's the output:
```
Installation finished. No error reported.Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.2.0-58-generic
Found initrd image: /boot/initrd.img-3.2.0-58-generic
Found memtest86+ image: /boot/memtest86+.bin
  /var/lock/lvm: mkdir failed: No such file or directory
  File-based locking initialisation failed.
done
Setting up grub-gfxpayload-lists (0.6) ...
```
Then I did grub-mkconfig and it just spit out a config to STDOUT. Should I have done -o /boot/grub/grub.cfg?

Then I did update-grub and it looks like it did the same thing as grub-pc in the end:
```
# update-grub
Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.2.0-58-generic
Found initrd image: /boot/initrd.img-3.2.0-58-generic
Found memtest86+ image: /boot/memtest86+.bin
  /var/lock/lvm: mkdir failed: No such file or directory
  File-based locking initialisation failed.
```

grub-install says no errors reported..

OK so before I reboot... a) what about the above weird output from install grub-pc and update-grub?   And what about the mkconfig output?  And lastly, I need to add console=ttyS0 or else I won't ever get any output displayed, how should I add that - to my /etc/default/grub at the end of my append statements (like usual)?

Waiting (to hear back and ensure my settings before I reboot)...

---

### Post by Bashing-om on 2014-02-11
IPvFletch; Strange and stranger !

"Setting GRUB_TIMEOUT to a non-zero" -> will not effect booting, can resolve at any time , no biggy

"/var/lock/lvm: mkdir failed: No such file or directory" -> I have no idea ! lvm == logical volume management (generally), have you done some fancy partitioning with this disk some time in the past ? Or have you encrypted your home directory or the swap directory ?
I have never encountered this creature .

"Then I did grub-mkconfig and it just spit out a config to STDOUT. Should I have done -o /boot/grub/grub.cfg" -> I would expect it to write the file, and generate text to stdout .. but, sure needs to be checked. What is the time stamp on the file ?
```

ls -la  /boot/grub/grub.cfg

```
else yeah ( did a boo boo), and need to run it with the explicit output destination "-o /boot/grub/grub.cfg"
----------------
IF "console=ttyS0" is defined as your display (xorg.conf or other) then sure you can direct console output in the /etc/default/grub control file. @ this line -> GRUB_TERMINAL=console .

Shucks ->
[INDENT][INDENT]This too is not going well
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-02-11
IPvFletch;; I am done for this session.
Can not go more. 
Rest and relaxation time .. exercise that bed.

I will check in my AM, and take this back up at that time,

[INDENT][INDENT]cheers your way
[/INDENT][/INDENT]

---

### Post by IPvFletch on 2014-02-11
Ok I guess it did update /boot/grub/grub.cfg cuz it's missing the serial stuff I had in there previously. So I edited /etc/default/grub and re-ran update-grub to get the console stuff sorted, as you said. Are you sure that GRUB_TERMINAL means output to ttyS0?
 
I think the /var/lock/lvm is due to chrooted environment and mounted disk. I'm not worried about. I never did anything with fdisk and used the default Ubuntu partitioning from the get-go. I did a mkdir /run/lock  (symlinked from /var/run) and re-ran update-grub, this time no error.

I'll reboot.. crossing fingers...

[B]eta: Holy... oh my gawd!  It booted!!  It's funny, I rebooted and was half-paying-attention and did NOT cross my fingers like I said I would (doh!) and then I saw it go to the whitespace and then nothing again. NO boot msgs... just blank nothing. Although this time I noticed it was more whitespace that scrolled by initially after BIOS post, like an extra line or two's worth. Anyways I looked away for a min or so and when I looked back it said "buntu 12.04 LTS...."  (no U!) and on the next line  '<hostname> login:"   I can't believe it!! I'm in disbelief still!!
:) [/B]**:) ****:) ****:) ****:) **[B]:) 
[/B][B]
So I have to wonder if it wasn't grub this whole time - because nothing else has changed (other than my stress levels - and yours!!).

I hope you sleep easy tonight. You deserve it, for all the horsepower you put into this for me!!! THANKS!!

Let's sync up tomorrow via this thread in case I have more updates or in case you want to see something else.. I'll reboot this bad boy like 20 times (w/out making pertinent changes) in between now and then and see if it still boots.

One thing I noticed is all of /boot/grub was rebuilt (tonight's timestamps) but nothing in /boot was touched (dates of Dec 3 which was probably latest files from apt-get update) except initrd which was changed this morning when I did the --reinstall on linux-image-generic. So the kernel was not the problem, it was indeed grub!   *grumble*  Thinking back to how I got into this mess, no way I touched grub. I hadn't touched grub since I installed this thing, and surely not right between the last deadly reboot and the reboot 1 hour before that one... so who knows!

FYI, GRUB_TERMINAL=console gets me a login on ttyS0 but not boot msgs. I had to add GRUB_CMDLINE_LINUX="tty0 console=ttyS0,9600" and re-run update-grub to get boot msgs..  BTW first line item on boot is fsck /dev/sda so I wonder if problems before were caused by fsck/disk errors???  doubtful but you never know... ??[/B]

---

### Post by IPvFletch on 2014-02-11
To summarize, this is what I did which ultimately fixed it (not sure if one of these in particular. My money is on the remove/purge/reinstall of grub though...
```
mount /dev/sdb1 /mntmount -t proc proc /mnt/proc
mount -t sysfs sys /mnt/sys
mount -o bind /dev /mnt/dev
chroot /mnt
fdisk -lu
apt-get remove --purge grub grub-pc grub-common
    grub-pc choose: /dev/sdb
grub-mkconfig
mkdir /run/lock        # due to chroot env
vi /etc/default/grub    # serial console and/or GRUB_TERMINAL
update-grub
grub-install /dev/sdb
reboot
```

Also, as expected, the internal HDD only does boot up as /dev/sda(1) so it was only showing up as sdb because of the USB HDD being plugged in and higher in the boot order..

---

### Post by Bashing-om on 2014-02-11
IPvFletch; Well ! Outstanding and great !

Wonders never cease, I too think somehow grub got corrupted, and the fix was to Purge grub and re-install. I will say I lost sleep over worrying over how to look at that boot sector. Will save that exercise for the next time. Put it on my to-look list ! That will be an exercise in learning.
Very good of you to have itemized the solution, others will appreciate it greatly.

Pleased it is all sorted out and we can move on.

[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

### Post by IPvFletch on 2014-02-11
Yes, and thanks again for your outstanding diligence and follow-through. Just when I was going to give up, your suggestion to do the full purge/re-install did the trick!  I have documented it here as something to try, just in case I ever run into anything like this again. Since fixing I have updated grub once more to include the console boot msgs, and have rebooted maybe 10 times. I'm sure to run 'sync' more often now as well, esp. before rebooting.. just in case. Thanks again, take care and hope to see you around! Also thanks go out to oldfred for his great ideas and attention to this issue..

---

### Post by IPvFletch on 2014-02-11
FWIW, I noticed one more hang (due to modprobe?), but otherwise it continues to boot OK: [http://ubuntuforums.org/showthread.php?t=2205034&p=12926651#post12926651](http://ubuntuforums.org/showthread.php?t=2205034&p=12926651#post12926651)

---

