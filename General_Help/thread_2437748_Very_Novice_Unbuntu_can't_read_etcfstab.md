---
title: "Very Novice: Unbuntu can't read /etc/fstab"
date: 2020-02-28
forum: General Help
---

### Post by celkins on 2020-02-28
My server crashed and i don't know what to do. Any advice would be greatly appreciated 

Things i know:
File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/LVM/pierserv-root: unknown filesystem type ''

And

It says can't read /etc/stab

---

### Post by TheFu on 2020-02-28
Perhaps if you shared some of the things you know here, someone might be able to help?   Of course, I could be wrong.
* check the log files?  Any errors or warnings?
* can you boot from a "Try Ubuntu" environment?
* can you boot from a "Recovery console" environment?

The mount line above doesn't make sense.  What does bootinfo have to do with anything?  Hopefully, you aren't trying to run boot-repair.  That tool has been less-than-great since UEFI booting began.  From inside a Try Ubuntu boot, you can troubleshoot almost everything.  

Not booting could be almost anything.  You'll need to be much more specific to get help.  When booting, how far does the process get?  Back screens wth text?  Any prompts?  Any images?

---

### Post by celkins on 2020-02-28
I can boot in "Try Unbuntu"

I cannot from recovery console

I tried boot repair and got this, but honestly its a little over my head

[http://paste.ubuntu.com/p/3ZVNYGxp4b/](http://paste.ubuntu.com/p/3ZVNYGxp4b/)

---

### Post by rsteinmetz70112 on 2020-02-29
Perhaps if you posted th results of 

```
ls -l /etc/fstab

cat /etc/fstab
```

---

### Post by TheFu on 2020-02-29
This is what is important from all that output.  It shows  an 80G HDD, with MBR partitioning, using LVM.  LVM is an advanced storage management technique not usually selected by non-experts.

```
Disk /dev/sda: 74.5 GiB, 80026361856 bytes, 156301488 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0001af86

Device     Boot  Start       End   Sectors  Size Id Type
/dev/sda1  *      2048    499711    497664  243M 83 Linux
/dev/sda2       501758 156301311 155799554 74.3G  5 Extended
/dev/sda5       501760 156301311 155799552 74.3G 8e Linux LVM
```

There are 4 different storage devices connected.   2 appear to be some flash media.  Unplug both of those and see if the system boots.  The BIOS might be set to boot from USB devices first.  Report the result.

If that doesn't solve it, unplug the 1TB disk.  Either removing the power or the SATA cable should be sufficient.  Try booting with just a single HDD connected.   Report the result.

Now, with just the 1 HDD connected, using a new 18.04 flash "Try Ubuntu", boot into the try ubuntu environment.  When that comes up, run 
```
lsblk -o name,size,type,fstype,mountpoint
```
and show the results.  We may need to install a few packages into the try ubuntu environment to get good results. IDK. If that output works, we can reinstall grub onto sda, then tell grub to update there.

If none of those things work, time to look at the log file for HW errors.  An 80G HDD could have faults that should show in the logs. But we aren't at a point where I'm worried about data loss.

---

### Post by celkins on 2020-03-02
First of all you both are so kind to answer, thank you so much. I didn't set this up I just inherited this.

There was two jump drives because I used one to boot up through the "Try Unbuntu" just so i could use the other jump drive to get some files off.

Without the boot jump drive, the machine will only boot to the busy box 

```
ls-l etc/fstab

reads

-rw-r--r-- 1 root root 59 Feb 28 20:09 /etc/fstab (this is with the stick plugged in, not sure if that matters)

cat /etc/fstab

overlay / overlay rw 0 0
tmpfs / tmp tmpfs nosuid, nodev 0 0
```

---

### Post by celkins on 2020-03-02
[https://i.imgur.com/NQyh2o5.jpg](https://i.imgur.com/NQyh2o5.jpg)

This is with the one 80 gb only hooked up

---

### Post by celkins on 2020-03-02
[https://i.imgur.com/FlyIFhi.jpg](https://i.imgur.com/FlyIFhi.jpg)

---

### Post by TheFu on 2020-03-02
```
-rw-r--r-- 1 root root 59 Feb 28 20:09 /etc/fstab
```

Is for the Try Ubuntu stick environment. You'll need to mount the correct partition somewhere (perhaps /mnt/ ?) , then move down to the directory into /etc/ and show the **ls -l for /mnt/etc/fstab**.
Please.

Also, please don't post images. Definitely, NOT inline. For blind people, they aren't helpful. Some people are paying by the byte to visit these forums. Copy/paste the text or use redirection to put the text into a file  if you need to use a different system to post here.

Plus, we can't copy/paste lines from an image to point out stuff.

 Thanks.

I'm looking for result comments for each of the other things requested.  Have you tried those first?  Did they work or not?  The order for each attempt mattered.

---

### Post by celkins on 2020-03-02
I'm so sorry, thanks for telling me. 

Is there a way to know what i should try to mount (sorry if that is a silly question)

---

### Post by TheFu on 2020-03-02
> **celkins said:**
> I'm so sorry, thanks for telling me. 

Is there a way to know what i should try to mount (sorry if that is a silly question)

You should mount the root LV.  Because the setup is using non-standard names, I can't tell you exactly what to type.
Here's one of my systems with uninteresting lines removed.

```
$ lsblk ..... (I have an alias for all the options)
NAME                                SIZE TYPE FSTYPE      MOUNTPOINT
sdb                                 477G disk             
&#9500;&#9472;sdb2                                1K part             
&#9500;&#9472;sdb5                            476.2G part LVM2_member 
&#9474; &#9500;&#9472;hadar--vg-swap_1                4.3G lvm  swap        [SWAP]  
&#9474; &#9500;&#9472;hadar--vg-root                 22.3G lvm  ext4        /
&#9492;&#9472;sdb1                              731M part ext2        /boot

```

And here's my fstab:
```
/dev/mapper/hadar--vg-root        /     ext4    noatime,errors=remount-ro 0  1
UUID=2471d686-fde5-4680-a75a-46c99c8a5550 /boot    ext2  defaults 0     2
/dev/mapper/hadar--vg-swap_1 none          swap  sw       0     0

```
So, the mount command that gets run at boot on this system is:
```
/bin/mount      -t ext4     -o noatime,errors=remount-ro      /dev/mapper/hadar--vg-root      / 
```

If I needed to use a "Try Ubuntu" flash boot, then I'd mount it to /mnt/ temporarily.
/bin/mount      -t ext4   /dev/mapper/hadar--vg-root      /mnt

If that failed, the error message should provide a hint.  Perhaps no LVM tools were loaded by the "Try Ubuntu" environment.  
**sudo apt install lvm**
**sudo vgchange -ay**
That should get the "mapper" working so /dev/mapper/hadar--vg-root is there and working.

You'll need to do the same for your box.  After looking at the permissions on /mnt/etc/fstab and the contents of that file, we'll know more.

Did you do the other 5-ish things requested?  Please tell us, clearly, about each.

**We can't read your mind.**

And please edit the 2 posts above to move the in-line images to be attachments.

---

### Post by celkins on 2020-03-02
Also I'm sorry what other info did you need, i got a little lost in the thread

---

### Post by celkins on 2020-03-02
Never mind sorry didn't realize it went to page 2, let me check that

---

### Post by celkins on 2020-03-02
it returned /sbin/mount: No such file or directory


but when I ls under dev/mapper the directory is there

---

### Post by DuckHook on 2020-03-02
Please don't post large graphics to the forums. This is very problematic for helpers with low speeds, who are on limited data plans, or are viewing from smartphones or small screens. It is also unnecessary to post whole screenshots in most cases. Terminal output can be highlighted with the mouse, copied with a right click and pasted into the posting box between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the button in the *Adv Reply* toolbar.

If you must post resource-intensive images, please post them as attachments using the paperclip icon in the *Adv Reply* toolbar.

---

### Post by TheFu on 2020-03-02
> **celkins said:**
> it returned /sbin/mount: No such file or directory


but when I ls under dev/mapper the directory is there

Sorry, /sbin/mount is wrong. Admin tools like mount usually go into /sbin/.

Should be **/bin/mount** - but the PATH should have it, so "**mount**" alone ought to work.

---

### Post by celkins on 2020-03-02
....

---

### Post by celkins on 2020-03-02
I messed up:

mount: /dev/mapper/pierserv-root/: can't find in /etc/fstab

---

### Post by celkins on 2020-03-02
Also not sure if this is helpful but i saw the blkid command

i ran it and pierserv-swap shows up, but the pierserv-root does not

---

### Post by celkins on 2020-03-02
@duckhood


Thank you for fixing it, sorry

---

### Post by celkins on 2020-03-03
ubuntu@ubuntu:/dev/mapper$ sudo lvscan
  ACTIVE            '/dev/pierserv/root' [<72.29 GiB] inherit
  ACTIVE            '/dev/pierserv/swap_1' [2.00 GiB] inherit
ubuntu@ubuntu:/dev/mapper$ sudo mount /dev/pierserv/root /mnt
mount: /mnt: wrong fs type, bad option, bad superblock on /dev/mapper/pierserv-root, missing codepage or helper program, or other error.
ubuntu@ubuntu:/dev/mapper$ 

I got my root to pull up now but it won't recognize it as mountable, thoughts?

I really appreciate how much help I have received, i feel like i am close

---

### Post by TheFu on 2020-03-03
Post #11 has an example mount command with options.  Try that.  But it appears something is wrong with the file system header.  How good are your backups?

---

### Post by celkins on 2020-03-03
> **TheFu said:**
> Post #11 has an example mount command with options.  Try that.  But it appears something is wrong with the file system header.  How good are your backups?

ubuntu@ubuntu:/dev/mapper$ sudo mount  -t ext4 -o noatime,errors=remount -ro /dev/mapper/pierserv-root /
mount: /: special device overlay does not exist.



Unfortunately i think the TB Hard Drive is where the issue started, the back up was there and the folder appears empty. Fingers crossed i can salvage what's happening here

---

### Post by TheFu on 2020-03-03
```
sudo mount -t ext4 -o noatime,errors=remount-ro /dev/mapper/pierserv-root /
```

WATCH SPACES.   THEY MATTER.   *-o noatime,errors=remount -ro *is NOT the same as **-o noatime,errors=remount-ro**

 You cannot use / as the target for the mount - called the 'mount point'.  I showed an example from my fstab, but just below it is how to mount that device to /mnt as the mount point.

The target location for the mount needs to be an empty directory.  If /mnt already has something, anything, mounted there, pick or create another directory and use that in the command.

---

### Post by celkins on 2020-03-03
> **TheFu said:**
> ```
sudo mount -t ext4 -o noatime,errors=remount -ro /dev/mapper/pierserv-root /
```

 You cannot use / as the target for the mount - called the 'mount point'

the target location for the mount needs to be an empty directory.  If /mnt already has something, anything, mounted there, pick or create another directory and use that in the command.

mnt appears empty

ubuntu@ubuntu:/mnt$ ls
ubuntu@ubuntu:/mnt$ sudo mount  -t ext4 -o noatime,errors=remount -ro /dev/mapper/pierserv/root /mnt
mount: /mnt: can't find in /etc/fstab.

---

### Post by TheFu on 2020-03-03
Options cannot have spaces - no spaces - between any of them.  

Try 

```
sudo mount        -t ext4        /dev/mapper/pierserv/root        /mnt
```

And why dd you change the location of the device from
**/dev/pierserv/root**
to 
**/dev/mapper/pierserv-root**

Why?  I'm curious.  Don't think it matters.  Some little things like that matter greatly. As long as those symbolic links point to the same dm-[0-9] devices, it shouldn't matter.  'dm' stands for "device mapper".

For example, 
```
$ ls -l    /dev/ubuntu-vg/
total 0
lrwxrwxrwx  1 root root    7 Mar  1 10:40 home-lv -> ../dm-3
lrwxrwxrwx  1 root root    7 Mar  1 10:40 root -> ../dm-1
lrwxrwxrwx  1 root root    7 Mar  1 10:40 stuff -> ../dm-4
lrwxrwxrwx  1 root root    7 Mar  1 10:40 swap_1 -> ../dm-2

```

---

### Post by celkins on 2020-03-03
It was completely unintentional, i tried it with pierserv-root and got the same error. 

Sorry I am stressing about this and got careless

---

### Post by celkins on 2020-03-03
ubuntu@ubuntu:~$ sudo mount        -t ext4        /dev/mapper/pierserv/root        /mnt
mount: /mnt: special device /dev/mapper/pierserv/root does not exist.

sudo mount        -t ext4        /dev/mapper/pierserv-root        /mnt
mount: /mnt: wrong fs type, bad option, bad superblock on /dev/mapper/pierserv-root, missing codepage or helper program, or other error.

---

### Post by TheFu on 2020-03-03
> **TheFu said:**
>  * check the log files?  Any errors or warnings? 

Besides that, I'm out of ideas.
The mount should have worked for ext4.  Any chance you chose some funky file system?  Not that I can help, but it could be an issue.  All of this is so we can see the /etc/fstab on the HDD - which would show the options needed to mount.

Normally, 
**sudo mount /dev/sdaX  /path/to/mount/point**
would figure out the type of file system used automatically.   I'd added the **-t ext4**, since that should be the default on Ubuntu. Other distros use different defaults.

Also, I provided a **vgchange** command, but you used **lvscan** instead.  Why? Don't know that it matters, but I've never used lvscan.  Do what you feel is best and good luck.

---

### Post by celkins on 2020-03-03
ubuntu@ubuntu:~$ sudo apt install lvm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package lvm


Could you tell me how to check the logs, i would appreciate it

---

### Post by celkins on 2020-03-03
sudo vgchange -ay
  2 logical volume(s) in volume group "pierserv" now active

---

### Post by celkins on 2020-03-03
I did find some errors in the log

fsck failed with error code 4

and

failed to start File system check on root device

not sure if that tells anything.

If you are out of ideas, i just wanted to say i have greatly appreciated the help

---

### Post by TheFu on 2020-03-03
Sorry,  LVM is really LVMv2 and has been for about 20 yrs.  We just say "lvm" these days.
sudo apt install **lvm2**

Logs are in /var/log/  There are many different techniques used to monitor, scan, review log files.  
[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)   <---- help.ubuntu.com is full of in depth guides which address all sorts of things.
My method: [https://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files](https://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files)
> sudo vgchange -ay
2 logical volume(s) in volume group "pierserv" now active 
Was the VG active before?  If not, then mounts won't work, but I don't think the mapper links would be there either.  _Tab-completion_ would make that clear.  Try doing the mount stuff again not that the VG is ACTIVE.

Be careful randomly using google to get commands to throw at the system.  Yes, use google, but be selective about the URL followed. My general rule is to use *.ubuntu.com results first, then use *ubuntu* domain name results next.  For LVM stuff, the version of Ubuntu doesn't really matter.  LVM has been the same for 15+ yrs across all Linux types.  But for other things, being specific about the Ubuntu release is very important.  Instructions for 18.04 are completely different than for 16.04.  I don't do non-LTS releases. Those are all beta code, IMHO.

Let's step back a little.
The box won't boot. 
Some issue is reported w/ the fstab file.  
The last 25+ posts have been trying to see that file on the correct disk.   There are many tiny details being missed from the helper perspective that are confusing.  Those tiny issues are noticed quickly when we use the commands, so we don't really notice that each inaccurate command turns into 4 hrs on your side.  That's where experience comes into play.  
You are doing pretty great, and not showing frustration. I wouldn't be so calm.  Fortunately, my job sent me to Unix training and my daily work had me surrounded by experts.  I didn't have to deal with any system admin work the first year.  Most of my co-workers would answer questions by saying RTFM.  It wouldn't hurt, but nothing we are doing here really needs the manpages.
Using LVM means there are a few extra complexities normally avoided by people really new to Linux.  LVM adds storage flexibility for a price, complexity.

Out of curiosity, are you using _tab-completion_ to fill in all filenames?  It makes getting things wrong almost impossible, at least for directories and filenames.   If not, please go and find a youtube video that explains it.  Unix, Linux, whatever all support it when bash is the shell used. Basically, if you are typing more than 3 characters at a time for a command, then you are probably doing it wrong.

---

### Post by celkins on 2020-03-03
Ha ha, that is very kind, I try to be patient

I got it to mount!! 

ubuntu@ubuntu:/dev/mapper$ sudo mount /dev/mapper/pierserv-root /mnt
mount: /mnt: /dev/mapper/pierserv-root already mounted on /mnt.


Now what? (sorry to be so dumb)

and yes i was "googling" too much, i got a little panicked

---

### Post by celkins on 2020-03-03
Also now that i got it mounted it appears everything is still there. (thank goodness)

But I can still only boot with the "Try Unbuntu" and I don't have access to open the directory

Sooooo close

---

### Post by TheFu on 2020-03-03
> **celkins said:**
> Ha ha, that is very kind, I try to be patient

I got it to mount!! 

ubuntu@ubuntu:/dev/mapper$ sudo mount /dev/mapper/pierserv-root /mnt
mount: /mnt: /dev/mapper/pierserv-root already mounted on /mnt.


Now what? (sorry to be so dumb)

and yes i was "googling" too much, i got a little panicked

What are the permission and contents of the /mnt/etc/fstab file?  That's how all this started, right?

---

### Post by celkins on 2020-03-03
> **TheFu said:**
> What are the permission and contents of the /mnt/etc/fstab file?  That's how all this started, right?

That was my original error that its was missing

verlay / overlay rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

---

### Post by celkins on 2020-03-03
After looking at some example did i possible do something wrong, other fstabs look like they have a much different structure?

---

### Post by celkins on 2020-03-03
Also now the boot message is 

Target file system doesn't have requested /sbin/init
No int found. Try passing init=bootarg

---

### Post by celkins on 2020-03-03
also sorry took me a little while to figure out who to get the permissions of the /etc/stab

-rw-r--r--  1 root root     725 Aug 20  2012 fstab

---

### Post by celkins on 2020-03-04
I had a thought last night what if now that it is mounted I re-installed the grub like

[B]sudo grub-install /dev/mapper/pierserv-root


[/B]Does that make sense? Would that mess anything up?

---

### Post by TheFu on 2020-03-04
I'm still waiting to see the fstab.  We cannot read your mind.  If you don't show what we ask to see, we cannot help. Too dangerous otherwise.

---

### Post by celkins on 2020-03-04
I'm so sorry i legit thought i posted it

 /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/pierserv-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=05d04125-e13a-4706-83d6-3007a4f2af81 /boot           ext2    defaults        0       2
/dev/mapper/pierserv-swap_1 none            swap    sw              0       0

/dev/sdb        /home/data      ext4    defaults        0       0

---

### Post by TheFu on 2020-03-04
1st, please use code tags whenever posting files, commands + command output. Note how I posted my fstab above?

About the fstab, yours:
```
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
/dev/mapper/pierserv-root / ext4 errors=remount-ro 0 1
# /boot was on /dev/sda1 during installation
UUID=05d04125-e13a-4706-83d6-3007a4f2af81 /boot ext2 defaults 0 2
/dev/mapper/pierserv-swap_1 none swap sw 0 0

/dev/sdb /home/data ext4 defaults 0 0
```

I would reformat it to prevent mistakes:
```
# <file system> <mount point> <type> <options> <dump> <pass>
# /boot was on /dev/sda1 during installation
UUID=05d04125-e13a-4706-83d6-3007a4f2af81 /boot ext2 defaults            0 2
/dev/mapper/pierserv-root     /     ext4 errors=remount-ro   0 1
/dev/mapper/pierserv-swap_1   none  swap sw                  0 0         
/dev/sdb                      /home/data ext4 defaults       0 0

```
Columns matter to the fstab, but any number of whitespace separates a column.
/dev/sdb seems wrong.  Almost always, a disk should have a partition.  [B]Are you certain the sdb line is correct?
[/B]sdb is the entire disk device.
sdb1 is the first partition on the disk.
sdb2 is the second partition on the disk.
sdb99 is the 99th partition on the disk.

Using a UUID instead of the path to a device **is** a best practice.  So, the sdb UUID really should be used, since it can change at boot.  Use **blkid** command to find it, then replace the 1st column sdb stuff to be similar to the /boot line that has a UUID.
LVM LVs don't change at every boot, so those don't need to be changed to something that hides useful information.

As for grub, it probably needs to be installed to /dev/sda.  Grub goes into the boot sector, not any LVM object. You cannot install it to sdb, since you don't have a partition table there (because someone decided to format the whole disk, not a partition.  That is almost always a big mistake - not having a partition table. If there isn't much data on it already, it would be worth fixing.

When in the "Try Ubuntu" mode, the real OS isn't being used, configs aren't available, boot data isn't where it should be. We can make everything be where it needs, do the grub-install, update-grub process. 
 [https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)  has a section about this. Boot-repair hasn't been so great for a few years, so please don't use that method. The section is _via the LiveCD terminal_ is what I'd recommend.  Step 5 say:
```
sudo mount /dev/sda6 /mnt/boot 
```
You'll want to do these commands:
```
sudo mount     /dev/mapper/pierserv-root     /mnt
sudo mkdir /mnt/boot
sudo mount UUID=05d04125-e13a-4706-83d6-3007a4f2af81 /mnt/boot
sudo grub-install --boot-directory=/mnt/boot /dev/sda

```
They don't say to do a chroot or update-grub.  Hummmm.  At least not in that section.  IDK.  In theory, if those instructions are correct, just reboot into the normal disk.  If that doesn't work, perhaps the HDD has bad sectors?

BTW, the /proc line in your fstab is probably redundant and not needed. Some old security types wanted to lock down all storage mount options as much as possible.  I've never done that.  You can just comment the line out for now. See how it goes for a few weeks and if nothing bad happens, remove the line forever.

---

### Post by celkins on 2020-03-04
```
ubuntu@ubuntu:/mnt/etc$ sudo mount UUID=05d04125-e13a-4706-83d6-3007a4f2af81 /mnt/boot
ubuntu@ubuntu:/mnt/etc$ sudo grub-install --boot-directory=/mnt/boot /dev/sda
Installing for i386-pc platform.
Installation finished. No error reported.
ubuntu@ubuntu:/mnt/etc$
```


Also it says I don't have permission to edit the fstab.

---

### Post by celkins on 2020-03-04
Result:

Target file system doesn't have /sbin/init
No init found. Try passing init= bootarg

Busybox v1.21.3 (Ubuntu 1:1.21.0-1ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands
(initramfs) 


I almost cried :( I thought that was going to be it

---

### Post by celkins on 2020-03-04
found this error too

> Checksum errors in superblock!  Retrying...
/dev/sda: Bad magic number in super-block while opening filesystem
Found a dos partition table in /dev/sda

---

### Post by TheFu on 2020-03-04
> **TheFu said:**
>  If that doesn't work, perhaps the HDD has bad sectors?

Files typically don't just disappear.  Probably usually mean some sort of hardware issue which would show up in the system logs and, for disks, in the SMART data for the disk.

[https://help.ubuntu.com/community/Grub2/Troubleshooting#grub.3E-1](https://help.ubuntu.com/community/Grub2/Troubleshooting#grub.3E-1) has some ideas.  Notice some of the bugs with LVM.

That superblock error is probably because a partition number is missing in the fstab.  Details matter.  I'm not great at initramfs stuff.  Whenever stuff like that happens, I've caught it before a reboot and repaired the issue. Worst case, or after spending more than a few hours on any issue, I'd wipe the system, do a fresh minimal install, then restore my data and settings from backups.  We are passed that point with this issue, IMHO.

Use **sudoedit** to edit system files.  anyone saying to use **sudo gedit**  (or any other GUI editor) is trying to mess up your system permissions.  You'll need to learn and understand basic unix file permission PDQ.  There must be thousands of tutorials about that.

As a general Linux reference, [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is fine. It has a chapter on permissions.

---

### Post by celkins on 2020-03-04
Thank you for all your help, you seriously have been great.

I guess i am going to start with a new HDD and go from there.

---

### Post by celkins on 2020-03-04
I do have one quick question if you have time, should i hook the new hard drive up and do a clean install and then hook up the other hard drive to get the files and configurations I need?

Is that the most efficient way to do that?

Thanks

---

### Post by TheFu on 2020-03-04
There are many different techniques. These forums have lots of people seeking a similar solution.  My standard answer is to test your backup and restore methodology onto the new HDD.  There will never be a better time.

Did you find anything in the log files or the SMART data for HDD?

---

