---
title: "Root File System Not Detected"
date: 2008-05-22
forum: General Help
---

### Post by sykorunner on 2008-05-22
After installing with Wubi and booting Hardy, it checks the installation and says that there is no root file system detected. It also says that I need to change the settings with the partition editor. How do I get to the partition editor and is there anything else I should do?

---

### Post by Rjecina on 2008-05-23
> **sykorunner said:**
> After installing with Wubi and booting Hardy, it checks the installation and says that there is no root file system detected. It also says that I need to change the settings with the partition editor. How do I get to the partition editor and is there anything else I should do?

We are having similar problem .....

I have tried installation with Wubi to avoid using partition editor (afraid of partition editors) and after end of Wubi installation from Windows XP Ubuntu answer has been "there is no root file system detected"

It is important to notice that earlier Wubi has failed installation from Windows 98 SE. ...

My only option for using Ubuntu or any other linux is installation without partitions managers (editors and similar) and if this is not possible I will forget Linux.

My configuration is Windows 98SE / Windows XP with 3 partitions and processor Core 2 Duo.

---

### Post by ago on 2008-05-24
Uninstall, run chkdsk /r on the target partition, and install again

---

### Post by Chechuty on 2008-05-24
I have the same problem i run the chkdsk /r and it detects 0 errors i reinstall Wubi and the problem continues :(

Help please!:KS

---

### Post by Chechuty on 2008-05-25
Any idea?

---

### Post by ago on 2008-05-26
Press ctrl+alt+f2 and run

sudo /custom-installation/hooks/failure-command.sh

that will produce logs in C:\ubuntu\installation-logs.zip

post them here.

---

### Post by Chechuty on 2008-05-26
[http://www.sendspace.com/file/vh3bir](http://www.sendspace.com/file/vh3bir)

;)

Ago i send you a MP

---

### Post by ago on 2008-05-26
hmm strange error:

May 26 14:43:22 ubuntu partman-auto-loop: Error: Partition number 5 not found in /var/lib/partman/devices/=dev=sda

It does not find the fifth partition on disk 1.

Can you try to uninstall and reinstall but in verbose mode (press esc at boot after "ubuntu") and then send the logs again?

---

### Post by Chechuty on 2008-05-26
Ago the news logs in verbose mode ;)

[http://www.sendspace.com/file/vwm18u](http://www.sendspace.com/file/vwm18u)

Thanks 4 all!

---

### Post by zyreg on 2008-05-27
the same problem here :(

---

### Post by ago on 2008-05-27
@zyreg can you send the logs too?
@chechuty will have a look later on today

---

### Post by zyreg on 2008-05-27
I doesn' matter, i will install it from live cd.

Bb

---

### Post by Chechuty on 2008-05-27
:(

Ago &#65279;if you discover something post it

******* error :mad:

---

### Post by ago on 2008-05-27
Chechuty, how many partitions do you have? and what is the partition where you installed wubi?

---

### Post by Chechuty on 2008-05-28
I have one HDD and i have a 3 partitions

       -Recovery partition(LAPTOP)
       -Windows XP
       -Files and data

I probe that on Windows XP and files and data and the same error

---

### Post by ago on 2008-05-28
What is the output of

cat /proc/partitions

Press ctrl+alt+f2 to get a console

---

### Post by Chechuty on 2008-05-28
I don't understand :S

---

### Post by ago on 2008-05-28
Type the above command in a terminal and post the results

---

### Post by catonano on 2008-05-28
Hello people,

same problem here, I have a wubi installation and it does not find the root any more; but I have a hint, I think.

This happened when I updated to kernel 2.6.24-17

The previous version, the 2.6.24-16, is still there and if I choose that one from the Grub menu it still boots and works great.

I'm afraid the they forgot to put in some module required for wubi installations only.

They have to be so used to vanilla installations ! 

Bye  ):P
Cato

---

### Post by ago on 2008-05-28
Interesting can anyone else please confirm the above, I will run some tests tonight

---

### Post by Chechuty on 2008-05-28
[IMG]http://img147.imageshack.us/img147/6363/imagen002kf8.jpg[/IMG]

---

### Post by ago on 2008-05-28
Cato can you post any log about the exact error? You might have to add debug as a boot parameter and look under /tmp

---

### Post by Chechuty on 2008-05-28
If you want something tell me ago ;)

---

### Post by ago on 2008-05-28
what is the output of 

cat /proc/mounts

and then try to manually mount sda5

mkdir /tmp/x
sudo mount /dev/sda5 /tmp/x

---

### Post by Chechuty on 2008-05-28
cat /proc/mounts = A lot of text


mkdir /tmp/x
sudo mount /dev/sda5 /tmp/x

And when i create the mkdir /tmp/x no problem but when then i write sudo mount /dev/sda5 /tmp/x the output is an error not found

PD: I don't post screen of the cat /proc/mounts because i more big than my monitor :P

---

### Post by ago on 2008-05-28
Chechuty, try this

1. uninstall, run chkdsk /r and run wubi again
2. BEFORE rebooting edit c:\ubuntu\install\custom-installation\preseed.cfg and replace

```
d-i partman/choose_partition \
       select Finish partitioning and write changes to disk
```

with

```
d-i partman/choose_partition select finish
```

3. save and reboot and proceed with the installation
4. let me know if it works or not

---

### Post by catonano on 2008-05-28
> **ago said:**
> Cato can you post any log about the exact error? You might have to add debug as a boot parameter and look under /tmp

I added the debug parameter to the menu.lst file and I took a peek at /tmp

There was a file but it was too long. I also tried

cat /tmp/thatFile | more

and took photos of every screenshot but they were too many and I got sick.

Also, now, I can't connect my camera and I won't take care of this too.

I managed to do a 

cat /proc/mounts     and I got:

rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
udev /dev tmpfs rw,relatime 0 0
fusectl /sys/fs/fuse/connections fusectl rw,relatime 0 0


and also

mkdir /tmp/x
mount /dev/sda5 /tmp/x

and got an "invelid argument" error.

Anyhow, yesterday, when I first run into this problem I managed to copy the stuff down on a bloc notes

Here it is:

# chain to real filesystem
maybe_break init
exec run-init ${rootmnt} ${init} "$0" <${rootmnt}/dev/console  > ${rootmnt}/dev/console 2>&1

(initramfs)

at that point I just tried to issue a ./init command and that was:



(initramfs) ./init
Loading, please wait...
Mount: Mounting none on /sys failed: device or resource busy
Mount: Mounting none on /proc failed: device or resource busy
udedv[2952]: Main: error initializing udevd socket
                   check boot_bootarg  cat /proc/cmdline
                   or missing modules, devices  cat /proc/modules  ls /dev
ALERT ! /dev/disks/by-uuid/3073-1408 does not exist. Dropping to a shell !

BusyBox v1.1.3 (Debian 1:1.1.3-5Ubuntu12) built-in shell (ash)
Enter 'help' for a list

Hope this helps
Bye
Cato

---

### Post by ago on 2008-05-28
catonano, your problem is different from the previous one

anyway you can filter the log file using grep

e.g.


grep mount /tmp/* -A4 -B4
grep err /tmp/* -A4 -B4

There is no need to post all of the log, I only need the mount errors (if any)

Make sure you know what is the device where you installed wubi, and try to mount that one manually, you might want to add the filesystem manually

#assuming sda5
mount -t ntfs /dev/sda5 /tmp/x

---

### Post by Chechuty on 2008-05-28
I changed 
[B]d-i partman/choose_partition \
       select Finish partitioning and write changes to disk[/B]

for

**d-i partman/choose_partition select finish**

And the same error :S

---

### Post by cjwatson on 2008-05-28
> **Chechuty said:**
> I changed 
[B]d-i partman/choose_partition \
       select Finish partitioning and write changes to disk[/B]

for

**d-i partman/choose_partition select finish**

And the same error :S

You may get the same red-screen error, but that's not very informative by itself. Could you please extract and post the syslog?

---

### Post by catonano on 2008-05-28
> **ago said:**
> catonano, your problem is different from the previous one

What do you mean ? It still claims it can't mount the root filesystem !

> **ago said:**
> anyway you can filter the log file using grep

e.g.


grep mount /tmp/* -A4 -B4
grep err /tmp/* -A4 -B4

There is no need to post all of the log, I only need the mount errors (if any)

Make sure you know what is the device where you installed wubi, and try to mount that one manually, you might want to add the filesystem manually

#assuming sda5t
mount -t ntfs /dev/sda5 /tmp/x

Ok, I'll try.

In the meantime, I tried to do:

cat /tmp/logFile | grep mount

and I quote the last 4 lines:

mount-w -t vfat /dev/disk/by-uuid/3073-1408  /root
Mount: mounting /dev/disk/by-uuid/3073-1408 on /root failed: no such device

mount -o move /root /host
Mount: mounting /root on /host failed: invalid argument

Now, as far as I know, "/dev/disk/by-uuid/3073-1408" is actually a file that's mounted in loop mode and bound to that path

So, if it' not there maybe it's the loop mounting that failed in the first place.

Anyhow, I'll reboot for the last time and I'll try to write down the output of the lines you suggested. Ugh :(

Thanks
Cato

---

### Post by ago on 2008-05-28
/dev/disk/by-uuid/3073-1408 is a device that should point to the fat32 partition where you installed wubi

you can use 

ls -l /dev/disk/by-uuid/*

to list the available devices by-uuid and where they point to

---

### Post by Chechuty on 2008-05-28
:(

:S is very strange this :confused:

Waiting instructions ago ;)

---

### Post by catonano on 2008-05-28
> **ago said:**
> /dev/disk/by-uuid/3073-1408 is a device that should point to the fat32 partition where you installed wubi

you can use 

ls -l /dev/disk/by-uuid/*

to list the available devices by-uuid and where they point to

Oh, I didn't think about it.

Anyhow, I issued the command

cat /tmp/logFile | grep mount /tmp/* -A4 -B4

as you suggested, but it still is a whole lot of lines, they're simply too much for me to copy on a copybook.

ANyhow, I tried to issue:

modporbe -v vfat

and I got a 

Fatal: no vfat module or something like that

As I reported a few posts ago, The last 4 lines of the log are like this:

mount -w -t vfat /dev/disk/by-uuid/3073-1408 /root
...

So, that's why it doesn't mount that, because it has no vfat module.

And I think that's it for today, I'm getting tired.

I'll stick to the previous kernel until something new arises.

Thanks for your help
Bye
Cato

---

### Post by catonano on 2008-05-28
Ago,

here I am ;-)

> **ago said:**
> /dev/disk/by-uuid/3073-1408 is a device that should point to the fat32 partition where you installed wubi

you can use 

ls -l /dev/disk/by-uuid/*

to list the available devices by-uuid and where they point to

yes, I did and found that /dev/disk/b-uuid/3073-1408   is actually there and it points to ../../sda5

STILL the last lines of the log are

mount -w -t vfat /dev/disk/by-uuid/3073-1408 /root
Mount: mounting /dev/disk/by-uuid/3073-1408 failed: no such device

So I assume it's /dev/sda5 the one who isn't there. 

My best guess is because that's a FAT32 partition and there's NO vfat module available

Thanks, anyhow, for all your help
Bye
Cato

---

### Post by ago on 2008-05-28
try to install the vfat module, and mount /dev/sda5 to avoid typos

modprobe vfat
mount -t vfat /dev/sda5 /root

some other module might be required though. Also try modprobe nls_cp437

use vol_id to gather more info on /dev/sda5

---

### Post by Chechuty on 2008-05-28
news? :(

---

### Post by ago on 2008-05-28
> **Chechuty said:**
> news? :(

as mentioned by cjwatson can you please post the logs after editing the preseed.cfg file and installing in verbose mode?

---

### Post by Chechuty on 2008-05-28
[http://www.sendspace.com/file/i8oyeb](http://www.sendspace.com/file/i8oyeb)

;)

---

### Post by Chechuty on 2008-05-29
up!

---

### Post by cjwatson on 2008-05-29
> **Chechuty said:**
> [http://www.sendspace.com/file/i8oyeb](http://www.sendspace.com/file/i8oyeb)

;)

This is happening because libparted is failing to detect any partitions whatsoever on your disk. I should be able to fix this given a hex dump of your boot sector (which includes the partition table). Could you please run the following command in a terminal window in Linux and post the output?

  sudo od -tx1 -Ax -N512 /dev/sda

(This requires root privileges to read from the raw device, but it doesn't write to it in any way.)

---

### Post by Chechuty on 2008-05-30
I get privileges(sudo -s)and i write sudo od -tx1 -Ax -N512 /dev/sda  and it shown me an error that says unknow command :S

---

### Post by cjwatson on 2008-05-30
Could I see the **exact** error message, please? Ideally copy and paste the command you typed, so something like:

  ubuntu@machine:~$ sudo od -tx1 -Ax -N512 /dev/sda
  <output>

You don't need to use 'sudo -s' first ('sudo' in front of the command is enough), though it shouldn't matter.

---

### Post by catonano on 2008-05-30
Ago,

> **ago said:**
> try to install the vfat module, and mount /dev/sda5 to avoid typos

modprobe vfat
mount -t vfat /dev/sda5 /root

some other module might be required though. Also try modprobe nls_cp437
the pr
use vol_id to gather more info on /dev/sda5

I think the problem is inside the initramfs image, so typing

modprobe vfat

could be not enough, I'm afraid.

I should manage to use the initramfs tools to add the vfat module to the initramfs image and see what happens. But that's a bit scary, because I have 2 initramfs images, now, one belonging to the previous (and working) kernel, the other one belonging to the new (and not working) kernel. I don't know how to instruct the initramfs-tools to work with the right image.

If I get it wrong and mess up around with the working image, I won't be able to boot the system any longer and that would be a shame.

Too bad, I tried to edit the menu.lst file in order try to boot the new kernel with the old initramfs image, hoping it would have worked, since the old initram actually boots the old kernel.

Well, that does something different and shows different symptoms, but still doesn't boot the system :-( Maybe the mismatch between versions is a problem ?

Anyway, I'd LOVE to be able to take the error log file from inside the initramfs to the outside world, but since that image does NOT mount the disk I don't know where to save it. Maybe I could mount a USB pen ? I'm afraid to remember that the vfat is required for USB pens too...

Or I could try to reach some machine on the local network and put the file there ?

How the hell I collect the log file ? :-(

Could you suggest me any idea ?

Or could you instruct me on how to add the vfat module to the RIGHT initramfs image so I could see what happens ?

Thanks for any further help
Bye
Cato

---

### Post by ago on 2008-05-30
Chechuty, I opened this bug [https://bugs.launchpad.net/ubuntu/+source/parted/+bug/235998](https://bugs.launchpad.net/ubuntu/+source/parted/+bug/235998)

Please follow up in there, myself and colin are subscibed and it is easier to follow via a bug report.

---

### Post by ago on 2008-05-30
cato, I doubt that the vfat module is not in the initrd. Do you have any error when you run "modprobe vfat"?

It might be that some other module is required.

In fact trying mounting a USB key with fat would be a useful exercise which would help to narrow down the issue.

As for logs it should be enough if you can get the relevant error messages. See also dmesg

---

### Post by catonano on 2008-05-30
Ago,

glad to see you're there even on friday ;-)

> **ago said:**
> cato, I doubt that the vfat module is not in the initrd. Do you have any error when you run "modprobe vfat"?

Yes, I have. I typed 

modprobe -v vfat

and got

Fatal: module vfat... well I don't remember exactly the wording, the fact is the vfat module was not there. I could check again, though...

> **ago said:**
> 
As for logs it should be enough if you can get the relevant error messages. See also dmesg

ok, I'll try to take a peek at the dmesg.

Some guys suggest to use yaird to repair the initramfs image. But I read it does not support loopbak devices. Is that true or is it just old info ? Do you know ?

Thanks
Bye
Cato

---

### Post by ago on 2008-05-30
Well I would like to understand what the problem is first before trying to fix it :)

To list the available modules, you can use

modprobe -l vfat
ls /lib/modules/2.6.24-17-generic/kernel/fs/

Also check /etc/initramfs-tools/initramfs.conf 

You can regenerate the initrd with the command:

sudo update-initramfs -c -k 2.6.24-17-generic

---

### Post by catonano on 2008-05-30
Ago,

> **ago said:**
> cato, I doubt that the vfat module is not in the initrd. Do you have any error when you run "modprobe vfat"?

I checked again. There's NO vfat module in the initramfs image.

modprobe -v vfat
FATAL: vfat module not found

> **ago said:**
> As for logs it should be enough if you can get the relevant error messages. See also dmesg

the output of dmesg is quite large too but I tailed it and saw that sda is there with its partitions, even the extended one, with the same layout I saw with GParted. So I'd say it's not a hardware issue with the disk.

I think I could open a bug, at this point, couldn't I ?

Bye
Cato

---

### Post by ago on 2008-05-30
Yes please, give title "There is no vfat module in the 2.6.24-17 initrd"
Can you test if other filesystems are available? e.g. modprobe -l ntfs

---

### Post by catonano on 2008-05-30
Ago,

> **ago said:**
> Yes please, give title "There is no vfat module in the 2.6.24-17 initrd"

Ok, thanks.

> **ago said:**
> Can you test if other filesystems are available? e.g. modprobe -l ntfs

I did. ntfs is not there either. Since I was there I even checked again for vfat, you know, sometimes you misspell. It's not there, definitively.u 

Ok, so now I open the bug and then let you know. 

Bye
Cato

---

### Post by catonano on 2008-05-30
Ago,

> **ago said:**
> Yes please, give title "There is no vfat module in the 2.6.24-17 initrd"
Can you test if other filesystems are available? e.g. modprobe -l ntfs

it should be this one: [https://bugs.launchpad.net/ubuntu/+bug/236021](https://bugs.launchpad.net/ubuntu/+bug/236021)

Let me know what you think

Thanks
Bye
Cato

---

### Post by catonano on 2008-05-30
Ago,

> **ago said:**
> Well I would like to understand what the problem is first before trying to fix it :)

To list the available modules, you can use

modprobe -l vfat
ls /lib/modules/2.6.24-17-generic/kernel/fs/

Also check /etc/initramfs-tools/initramfs.conf 

You can regenerate the initrd with the command:

sudo update-initramfs -c -k 2.6.24-17-generic

Thank you, I'll take a note of this.

In the /etc/initramfs-tools/initramfs.conf file I saw a row like this:

MODULES=most

which should imply the presence of filesystem related modules, as I read in the comments

So, before trying to mess up with the init image, I'll wait for some news to pop up in the bug report I opened

Thanks
Bye
Cato

---

### Post by ago on 2008-05-30
catonano ntfs is in fact a userspace driver, my bad. Anyway I assigned myself to the bug. I did a quick scan of initramfs-tools code, but there does not seem to be any relevant change with respect to vfat.

---

### Post by ago on 2008-05-30
Catone, 

In fact I start to think that this was an old bug never discovered rather than a regression (now that I think of it I did see other people in the past unable to mount from vfat). The initrd in the live cd explicitly add vfat via casper hooks, but the same does not hold for regular initramfs-tools. good news is that the fix should be simple

---

### Post by Chechuty on 2008-05-30
How I capture my boot sector? With a program in Windows?

I need to send it

---

### Post by ago on 2008-05-30
Chechuty

You run the program mentioned by cjwatson in a terminal within Ubuntu. If you pick the last option in the boot menu (press esc at boot), you should be able to run into LiveCD desktop mode (otherwise boot using a Live CD). From there applications > accessories > terminal. 

Then save the output in a file and upload it to the bug report.

---

### Post by Chechuty on 2008-05-30
I post it just now. 

[https://bugs.launchpad.net/ubuntu/+source/parted/+bug/235998](https://bugs.launchpad.net/ubuntu/+source/parted/+bug/235998)

:KS

---

### Post by ago on 2008-05-30
> **Chechuty said:**
> I post it just now. 

[https://bugs.launchpad.net/ubuntu/+source/parted/+bug/235998](https://bugs.launchpad.net/ubuntu/+source/parted/+bug/235998)

:KS

Thanks, would it be possible to paste text also? I would assume that it would be easier for colin to have text as opposed to an image. You can select the text with the mouse and right click and copy it. Then paste it into the bug report.

---

### Post by Chechuty on 2008-05-30
Corrected!

---

### Post by catonano on 2008-06-01
Agostino,

> **ago said:**
> Well I would like to understand what the problem is first before trying to fix it :)

To list the available modules, you can use

modprobe -l vfat
ls /lib/modules/2.6.24-17-generic/kernel/fs/

Also check /etc/initramfs-tools/initramfs.conf 

You can regenerate the initrd with the command:

sudo update-initramfs -c -k 2.6.24-17-generic

I followed the evolution of my bug opening and I tried to apply to the /usr/share/initramfs-tools/hook-functions file the same edit proposed as a patch.

It works. I was able to boot with the new kernel right now !

So, thanks SO much for your help

Hear you soon
Bye
Cato

---

