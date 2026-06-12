---
title: "Stuck at BusyBox at Hardy Heron Boot."
date: 2008-05-01
forum: General Help
---

### Post by Danish989 on 2008-05-01
I installed Hardy Heron inside Windows XP using WUBI around 2 days ago, and I installed NVIDIA drivers and some software on it, and everything was working perfectly fine. But yesterday, when I restarted my computer from Windows XP to work in Hardy Heron, I chose Ubuntu from the OS Choice Screen, and Ubuntu started to load, but immediately after that, it took me to the BusyBox screen which said:

BusyBox v1.3.1 Debian inbuilt shell (ash).
(initramf)

I have no idea what to do, I restarted a couple of times, tried using different kernels to boot (by pressing escape when ubuntu was loading, pressing e and choosing a different kernel) but it keeps bringing me to that screen. 

I've also seen threads by other people, that have had or are having the same busybox problems, some even before Ubuntu has been installed or started working, but I can't find any solution anywhere ..

Can anyone help?

---

### Post by avtolle on 2008-05-01
[http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234) is a link to the Wubi forum. It seems there are a few threads there about your problem (from scanning the titles).

---

### Post by Danish989 on 2008-05-01
I installed Hardy Heron inside Windows XP using WUBI around 2 days ago, and I installed NVIDIA drivers and some software on it, and everything was working perfectly fine. But yesterday, when I restarted my computer from Windows XP to work in Hardy Heron, I chose Ubuntu from the OS Choice Screen, and Ubuntu started to load, but immediately after that, it took me to the BusyBox screen which said:

BusyBox v1.3.1 Debian inbuilt shell (ash).
(initramf)

I have no idea what to do, I restarted a couple of times, tried using different kernels to boot (by pressing escape when ubuntu was loading, pressing e and choosing a different kernel) but it keeps bringing me to that screen.

I've also seen threads by other people, that have had or are having the same busybox problems, some even before Ubuntu has been installed or started working, but I can't find any solution anywhere ..

Can anyone help?

---

### Post by Danish989 on 2008-05-01
Nope, still couldn't find a solution.

---

### Post by Danish989 on 2008-05-03
Bump!

Still don't know what to do! :(

---

### Post by Danish989 on 2008-05-03
Bump!

Still don't know what to do! :(

---

### Post by Danish989 on 2008-05-06
I was running Hardy Heron for 2 days, installed on Xp using Wubi, when out of nowhere, I was greeted with BusyBox at bootup after choosing Ubuntu from the OS choice menu.

The ubuntu progress bar starts going back after reaching the end, and the screen changes to the command line BusyBox screen, that says:

> 
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (Ash)
Enter 'help' for a list of commands

(initramfs)


I restarted, chose Ubuntu, and pressed esc to get to the Grub menu. 

I pressed 'e' at the second option (Kernel /boot/vmlinuz-2.6.24-16-generic root=...) and removed the 'quiet splash' at the end to get a more detailed boot.

After the process stopped, I scrolled up to see the errors, and there were 3 in total:

> usb 1-2: device not accepting address 2, error -71

and

> mount: mounting /dev/disk/by-uuid/3233-10F5 on /root failed: no such device

mount: mount /root on /host failed: invalid arguement

ALERT! /host/ubuntu/disks/root.disk does not exist. Dropping to a shell!

And I was once again brought back to the same BusyBox screen. 

Now, I do see the errors, but I do not know what to do to get rid of them and a little help would be really appreciated!

---

### Post by Danish989 on 2008-05-06
I was running Hardy Heron for 2 days, installed on Xp using Wubi, when out of nowhere, I was greeted with BusyBox at bootup after choosing Ubuntu from the OS choice menu.

The ubuntu progress bar starts going back after reaching the end, and the screen changes to the command line BusyBox screen, that says:

> 
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (Ash)
Enter 'help' for a list of commands

(initramfs)


I restarted, chose Ubuntu, and pressed esc to get to the Grub menu. 

I pressed 'e' at the second option (Kernel /boot/vmlinuz-2.6.24-16-generic root=...) and removed the 'quiet splash' at the end to get a more detailed boot.

After the process stopped, I scrolled up to see the errors, and there were 3 in total:

> usb 1-2: device not accepting address 2, error -71

and

> mount: mounting /dev/disk/by-uuid/3233-10F5 on /root failed: no such device

mount: mount /root on /host failed: invalid arguement

ALERT! /host/ubuntu/disks/root.disk does not exist. Dropping to a shell!

And I was once again brought back to the same BusyBox screen. 

Now, I do see the errors, but I do not know what to do to get rid of them and a little help would be really appreciated!

---

### Post by Seks on 2008-05-06
I get that occasionally with wubi, just power off and let your comp rest a little bit. Maybe just a reboot will do.

If you can boot windows, then it's not a hardware issue I don't think. Try checking for dust and the like.

---

### Post by Danish989 on 2008-05-06
I have rebooted, shut down my computer, as well as run "Chkdsk /r" on all the drives, and that didn't help. Windows XP is working perfectly btw.

---

### Post by ago on 2008-05-06
check /proc/partitions 
and try to mount your windows partition manually

mount /dev/??? /root

replacing ??? with the appropriate partition.

---

### Post by Danish989 on 2008-05-07
Where do I enter these commands?

How do I check what the address of the partition is, where wubi is installed? 

mount /dev/???/root ... what format should the address be in? hd (0,4) or just (0,4) or 0,4 without the brackets?

---

### Post by ago on 2008-05-07
You enter the commands at the busybox prompt

#this will list all your visible partitions
cat /proc/partitions 

#this will list all partitions already mounted
cat /proc/mounts | grep /dev/

#example of a mount (watch the spaces!)
mount /dev/sda2 /root

#list contents of /dev/sda2
ls /dev/sda2

#unmount before trying another partition
umount /dev/sda2

---

### Post by Danish989 on 2008-05-07
List of partitions include:
sda, sda1, sda2, sda5
sdb, sdb1, sdc, and sdc1

After entering cat /proc/mounts | grep /dev/ nothing happened and I was returned to the next line to enter another command, which I guess means that no partition is mounted.

After using ls /dev/*partition names here* nothing happened at all, except /dev/*partition name here* showing up under the line with no file or folder names, and the cursor returning to another line, waiting for another command.

After tring to mount /dev/*partition name here* /root (using all partitions) the same error was met:
"failed: invalid arguement."

What do I do now? =(

---

### Post by rememberme2016 on 2008-05-08
I'm having the same problem. 

I've been using Ubuntu 8.04 under the Wubi installer for about 2 weeks now, and am suddenly struck with this BusyBox nonsense. Have tried following these instructions, to no avail. 

Please help.

---

### Post by ago on 2008-05-08
Boot into Windows and run chkdsk /r on the same drive.
Check that \ubuntu\disks\root.disk is visible.
Then shutdown cleanly.
Then try again to boot Ubuntu.

---

### Post by Danish989 on 2008-05-08
I've already run chkdsk /r on all the drives, and root.disk is visible in windows. I've shutdown and/or restarted, but still get the busybox screen... 
Mounting always leads to "invalid arguement"

Can you help me figure out what to do?

---

### Post by ago on 2008-05-08
Boot in verbose mode and provide more info about any error.

Logs are under /tmp

---

### Post by Danish989 on 2008-05-09
Here is the complete boot process:

[IMG]http://i70.photobucket.com/albums/i106/Danish989/09052008811-1.jpg[/IMG]
[IMG]http://i70.photobucket.com/albums/i106/Danish989/09052008812.jpg[/IMG]
[IMG]http://i70.photobucket.com/albums/i106/Danish989/09052008813.jpg[/IMG]
[IMG]http://i70.photobucket.com/albums/i106/Danish989/09052008815.jpg[/IMG]
[IMG]http://i70.photobucket.com/albums/i106/Danish989/09052008817.jpg[/IMG]
[IMG]http://i70.photobucket.com/albums/i106/Danish989/09052008818.jpg[/IMG]
[IMG]http://i70.photobucket.com/albums/i106/Danish989/09052008820.jpg[/IMG]
[IMG]http://i70.photobucket.com/albums/i106/Danish989/09052008821.jpg[/IMG]

---

### Post by ago on 2008-05-09
What is the output of:

ls -al /dev/disk/by-uuid

---

### Post by bullwong on 2008-05-09
I had this happen to me to when upgrading from 7 to 8 from inside Ubuntu. It installed 2 kernel versions, and the older one worked for me when the newest one it defaults to kept hanging. I don't have access to that computer right now or I'd be more specific.

---

### Post by Danish989 on 2008-05-10
The output of 
ls -al /dev/disk/by-uuid

is:

[IMG]http://i70.photobucket.com/albums/i106/Danish989/10052008838.jpg[/IMG]

---

### Post by ahmedh on 2008-05-12
Hi, I am having the same problem. I did the chkdisk thing, everything seemed okay (it fixed index 25 or something? I'm sorry, if that was crucial, I wasn't really paying attention since it took a long time to run).

But I don't see /ubuntu/disks/root.disk, only swap.disk. Any suggestions?

---

### Post by ago on 2008-05-14
Danish989, try to mount manually /dev/sda5

mkdir /trash
mount /dev/sda5 /trash
ls /trash/ubuntu

If it works replace UUID=3233-10F5 with /dev/sda5 in menu.lst 

@ahmedh:

Try to run chkdsk /r from windows on the same partition where you have Wubi first. If it does not work use ls -al /dev/disk/by-uuid to find out the right /dev/sd?? partition then try the commands above.

---

### Post by Danish989 on 2008-05-14
Failed: Invalid Arguement

[IMG]http://i70.photobucket.com/albums/i106/Danish989/15052008852.jpg[/IMG]

---

### Post by Yondergod22 on 2008-05-15
[https://wiki.ubuntu.com/WubiGuide#head-9fe000fa2e31a632fdcf384438b2aee35076c623](https://wiki.ubuntu.com/WubiGuide#head-9fe000fa2e31a632fdcf384438b2aee35076c623)
try that... it didn't work for me though. now the orange loading bar thing just stops.
let me know if it works for you though.
good luck

edit: I don't think the link goes to the right part of the page, if not just search for busybox

---

### Post by ahmedh on 2008-05-15
How do I tell which is the right partition (ie how did you know sda5 was correct for Danish judging from his output)?

---

### Post by ahmedh on 2008-05-15
This was the first thing I tried; there was no difference in my boot process.

---

### Post by jualin on 2008-05-21
My friend was having the same problem in Ubuntu Heron after an update and he followed the instructions from [http://www.techsupportforum.com/alternative-computing/linux-support/207451-ubuntu-busybox-v1-1-3-debian-1-1-1-3-5ubuntu7-built-shell-ash.html]("http://www.techsupportforum.com/alternative-computing/linux-support/207451-ubuntu-busybox-v1-1-3-debian-1-1-1-3-5ubuntu7-built-shell-ash.html") by ubli. In summary the instructions said to start your computer and when you reach the Grub Menu (Boot menu) press "e" to edit the boot commands and then select the second line which says "Kernel..." and remove the line "quiet splash" and add the line "all_generic_ide" to the end. The press return and "b" to boot. Hope this helps!

---

### Post by She's My Man on 2008-05-22
I have this problem too, except that this is a fresh install I did, not an update... And that I didn't get most of the answers here!

---

### Post by jualin on 2008-05-22
"She's my man" Did you try what I suggested?

---

### Post by She's My Man on 2008-05-23
Yes. But I reinstalled anyway and now it works!!

---

### Post by ahmedh on 2008-06-01
> **jualin said:**
> \ remove the line "quiet splash" and add the line "all_generic_ide" to the end. The press return and "b" to boot. Hope this helps!
Why, good sir, it appears you have saved my Wubi installation. I owe the use of my computer to you. Thank you many times over. I have tried all other proposed solutions, but yours is the only one that worked, and like a charm at that.

---

### Post by jualin on 2008-06-02
well ahmedh I am glad that the solution worked. My friend the other day pointed me to something called the wubi guide and we found something about the mysterious BusyBox issue. Apparently the issue is produced by so some problem with the virtual partition that Wubi uses. This is the link [https://wiki.ubuntu.com/WubiGuide#head-9fe000fa2e31a632fdcf384438b2aee35076c623]("https://wiki.ubuntu.com/WubiGuide#head-9fe000fa2e31a632fdcf384438b2aee35076c623"). The entire guide is pretty handy and addresses many problems that people had faced in a Wubi installation.

---

### Post by vanitor on 2008-12-18
how to i run /r chkdisk soz computeer noob here, i am having the same problem befiore its even installed.

---

