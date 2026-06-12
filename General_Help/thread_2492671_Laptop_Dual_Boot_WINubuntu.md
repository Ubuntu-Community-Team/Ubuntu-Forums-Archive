---
title: "Laptop Dual Boot WIN/ubuntu"
date: 2023-11-19
forum: General Help
---

### Post by box02-0 on 2023-11-19
Hi.

I have an old WINdows laptop that I want to become a dual boot WIN/Ubuntu.

My desktop is a  dual boot WIN/Ubuntu 22.04.1 LTS, with ubuntu in its own 85gb partition.

I would like to copy my desktop ubuntu onto the laptop.

I need help in determining what is the best way to go about this.

I'm thinking that I might try this:
1. Create an 85gb partition on the laptop
2. Download and install ubuntu desktop from the ubuntu website

This should give me a fresh dual boot WIN/ubuntu 22.04.
I now want the laptop ubuntu to be a copy of my desktop ubuntu. Can I just gparted copy/paste my desktop/ubuntu ---> laptop/ubuntu ??

Questions
1. Will the laptop still boot WIN/ununtu ??
2. Will the laptop ubuntu be able to accommodate the different hardware configuration ?
3. Is there a better way to do this ?

Thanks for listening. Any help would be greatly appreciated.
M....

---

### Post by oldfred on 2023-11-19
I would do new install.
Then restore backup from desktop. You do have good backup for desktop?

Backup should be /home which has all your user settings & data. If you have additional data partitions or separate /home partition that should also be backed up. You may want to backup some settings in /etc if you have edited any system settings. I edit grub, but just make a copy into /home so then backed up. If you installed any server apps like database or web apps, those would be in / and also need backup. You should also export list of installed apps, to make it easy to reinstall.
No need to backup / (root), normally, as that can easily be installed. 
Its not like Windows where its difficult to separate system, system settings & data, so full image backup often is better.

Restore from backup then is a good test that your backup is complete so when (not if) you have major issue, you know you can easily restore system.
And currently you still have original install to find anything not in backup.

---

### Post by box02-0 on 2023-11-19
Hi good oldfred.

You have been answering many of my posts for a long time - and thanks for helping with this one.

[COLOR=#8b4513]I would do new install.[/COLOR]
Will do.

[COLOR=#8b4513]Then restore backup from desktop. You do have good backup for desktop?
[/COLOR]Yes I backup my desktop, partition by partition, every 2 - 3 weeks, using gparted copy/paste (booting off of a gparted USB). So I assume you mean restore my desktop/ubuntu partition using gparted ??

(By the way after each backup, I BIOS disable the live drive, enable the backed up destination drive, and boot from it as a test.)

[COLOR=#8b4513]Backup should be /home which has all your user settings & data. f you have additional data partitions or separate /home partition that should also be backed up. You may want to backup some settings in /etc if you have edited any system settings.[/COLOR]

So here is where I get a little lost. Wouldn't my gparted desktop/ubuntu partition backup contain /home user data & settings and any additional data partitions ??
And  wouldn't my gparted desktop/ubuntu backup contain /etc system settings ??

[COLOR=#8b4513]I edit grub, but just make a copy into /home so then backed up.[/COLOR]
And wouldn't my gparted desktop/ubuntu backup contain grub  ?? But since the Location of the laptop ubuntu partition is different than the desktop ubuntu partition, wouldn't this be a problem ??

Is this where the UEFI boot install & repair comes into play ?? Will I need to run this on the laptop in order to properly boot ??

[COLOR=#8b4513]You should also export list of installed apps, to make it easy to reinstall.[/COLOR]

If I have the full ubuntu partition backed up (multiple generations), why would I need to do this ?

Thanks for your input and anxiously awaiting your reply,
M....

---

### Post by tea for one on 2023-11-19
Your old laptop and current desktop - are they both UEFI mode with GPT?

---

### Post by oldfred on 2023-11-19
Never used gparted for backup. I think that is more an image backup. So then restore of / if separate partition would wipe out new install's /. And then you get into mis-match of UUIDs & GUIDs.
Some seem to like image type backups, but as soon as you use system, it is obsolete.
Using rsync or rdiff only backs up changes & takes less space. Also much quicker so easier to run more often.

I use rsync and do not copy any / folders or / partition. 
I use a bash file that documents install, backs up /home, backs up my data partition and does a few other things.
I do not follow TheFu's recommendations, exactly. But his recommendations (and a few others) are the best info on this site. I use rsync and copy to various external & internal drives.

rdiff Here's a simple script for backing up HOME directories: post #2 by TheFu
[https://ubuntuforums.org/showthread.php?t=2447368](https://ubuntuforums.org/showthread.php?t=2447368)
[https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006)
What to backup TheFu
[https://ubuntuforums.org/showthread.php?t=2456011](https://ubuntuforums.org/showthread.php?t=2456011)
[https://ubuntuforums.org/showthread.php?t=2462752&p=14040507#post14040507](https://ubuntuforums.org/showthread.php?t=2462752&p=14040507#post14040507)
Best practice for Backups - theFu
Change to exclude line:
[https://ubuntuforums.org/showthread.php?t=2484708](https://ubuntuforums.org/showthread.php?t=2484708)
[https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006) &
[https://ubuntuforums.org/showthread.php?t=2368992](https://ubuntuforums.org/showthread.php?t=2368992) & 
Simple manual rsync & rdiff theFu
[https://ubuntuforums.org/showthread.php?t=2471454&p=14078689#post14078689](https://ubuntuforums.org/showthread.php?t=2471454&p=14078689#post14078689)
Restore process TheFu
[https://ubuntuforums.org/showthread.php?t=2474107&p=14091927#post14091927](https://ubuntuforums.org/showthread.php?t=2474107&p=14091927#post14091927)

Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

### Post by box02-0 on 2023-11-20
Hi Tea for one.

Good question.
 
Current desktop YES UEFI with GPT.

Old laptop is being given to me by a friend - I should have it in a week or so. No clue how old it is.
I know the  'gdisk -l' command on linux, but how would I determine if GPT is being used on Windows ? My guess it's mbr.

So how does the fact that it is mbr affect how to convert the old laptop to dual boot ? I know mbr has a 2tb limit, but I'm looking at gigabyte partitions, not terabytes.

Thanks,
M....

---

### Post by yancek on 2023-11-20
In all likelihood, a computer which came with windows 7 pre-installed will be an MBR.  If you want Ubuntu on that computer and on the same drive, it will also need to be an MBR/Legacy install or they both won't boot from the same bootloader.

> but how would I determine if GPT is being used on Windows ?  

You can get that infor from either fdisk or gdisk, when you get the machine and boot a Linux usb on it.  What do you intend to copy from Ubuntu on the Desktop to the laptop.  The entire system or just personal data?/

---

### Post by SeijiSensei on 2023-11-20
Here's a sample from running "sudo fdisk /dev/sda":

```

Disk /dev/sda: 238.47 GiB, 256060514304 bytes, 500118192 sectors
Disk model: kimtigo SSD 256G
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
**Disklabel type: gpt**

```

---

### Post by tea for one on 2023-11-20
> **box02-0 said:**
> I determine if GPT is being used on Windows ? My guess it's mbr.
Windows 10 > Check via Disk Management > Right Click (C) > Properties > Volume > Partition Style
It may be the same for Windows 7 (I have no way to double-check)
> So how does the fact that it is mbr affect how to convert the old laptop to dual boot ? I know mbr has a 2tb limit, but I'm looking at gigabyte partitions, not terabytes.
In your first post, I assumed that you wanted to copy the system via Gparted.
A copy of a UEFI installation will not boot without an ESP, therefore I asked the question.

All in all, I've probably (inadvertently) overcomplicated everything for you - this was not my intention, I'll get my coat ;)

---

### Post by grahammechanical on 2023-11-20
> I'm thinking that I might try this:
1. Create an 85gb partition on the laptop
2. Download and install ubuntu desktop from the ubuntu website

This should give me a fresh dual boot WIN/ubuntu 22.04.

All that is fine. To recreate what you have on the desktop machine on the laptop - you install the same applications that you have installed on the desktop machine. You copy your data from the desktop machine on to a USB memory stick. Then you plug it into a USB port of the laptop and use the file manager to transfer/copy the files/documents on to the laptop.

A couple of years ago my desktop machine stopped working. I purchased a laptop with Ubuntu pre-installed. Later I purchased a hard drive enclosure that was powered by mains electricity but with a USB cable that I plugged into a USB port in the laptop. I then put the hard drive (SATA) from the desktop machine into the hard drive enclosure. I then  booted Ubuntu on the laptop and I was able to use the file manager to transfer all my data files and documents on to the laptop storage drives.

Your desktop is still working. So, you should be able to transfer files from the desktop to a USB memory stick and then transfer the files from the USB memory stick to the drive in the laptop. Restrict your self to transferring data file and documents and not system files.

Regards

---

### Post by box02-0 on 2023-11-20
I have an ubuntu (operating system only) partition on my desktop that I wish to copy on a separate partition on the laptop.

No need to copy data and other 'stuff', including the window partition. 

I do agree - no doubt win7 and MBR.

M...

---

### Post by box02-02 on 2023-11-25
I'm back :)

Okay a small change in plan. While I'm waiting for my friend's old laptop, my wife has just purchased a WIN 11 Pro laptop. Guess what ? I would like to make it a dual boot system, with its  ubuntu partition to be a clone of my desktop ubuntu partition. Both systems are uefi and gpt and both ubuntu partitions will be 85gb.

Here is a snapshot of my desktop windows and 85gb ubuntu partition:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293114&stc=1[/IMG]

First part is easy - install a fresh ubuntu 22.04 onto an 85 gb partition onto the laptop, and make it a dual boot.

Rather than copy my /home directory and re-install all apps (many), what is the reason why I can't just copy my 85gb ubuntu desktop partition and paste it into the 85gb ubuntu laptop partition ?? 

Is there machine specific (hardware) code in the ubuntu partitions ?? If both machines were identical, would this work ?? 

Thanks for any advice.

M...

---

### Post by box02-02 on 2023-11-25
posted twice.

---

### Post by oldfred on 2023-11-25
You cannot easily copy one gpt partition. 
With gpt, you have a primary partition table, backup partition table & the partitions. The GUIDs must all match.
There may be ways to re-sync, but probably easier just to export list of apps & reimport/install them.
You can rsync /home over so settings are all the same.

This is where I almost always suggest new clean install & restore from backup. That proves your backup is complete, so when (not if) system needs reinstall you know you have everything & how to easily do it.

---

### Post by yancek on 2023-11-26
> Rather than copy my /home directory and re-install all apps (many), what  is the reason why I can't just copy my 85gb ubuntu desktop partition  and paste it into the 85gb ubuntu laptop partition ?? 

Because it won't boot.  If it were an EFI install, you would need Ubuntu boot/grub files on an EFI partition on the new drive also and create an entry on the system board which would probably requiring installing Grub.  If your old system is a Legacy install with boot code in the MBR, you could install Ubuntu in Legacy mode and boot code in the MBR which would allow you to boot Ubuntu as long as you create a bios_boot partition if the new windows system has a GPT drive.  If Grub is installed in Legacy mode, it won't boot windows in EFI mode.  You will be much better off following the instructions above doing a new install.

---

### Post by dragonfly41 on 2023-11-26
Be aware that with spanking new Windows 11 laptop you have another card to play.

It is named WSL and allows Ubuntu to run within Windows 11.

[https://learn.microsoft.com/en-us/windows/wsl/tutorials/gui-apps](https://learn.microsoft.com/en-us/windows/wsl/tutorials/gui-apps)

My personal choice would be to keep the two worlds apart and dual boot as you suggest. But you could in theory have a hybrid option of both:
WSL native
Ubuntu in dual boot SSD

---

### Post by box02-02 on 2023-11-26
Thanks for all the really quick and informative replies. 

So just to clarify, it is the gpt portion of the ubuntu partition that would be my problem if I tried cut/paste my desktop ubuntu partition ? Is that the only problem ?
 
And this would explain why I can backup my desktop using the gparted cut/paste and end up with a bootable functioning backup - because the **entire** ssd (all partitions) is **identical** partition wise as the live system. 

I'm just trying to simplify the procedure . Imagine that I was in charge of 73 various computers (desktops, laptops of different sizes and makes), and my task was to make them all dual bootable and make ALL of the ubuntu partitions identical to my desktop. I would have thought there would have been a simpler method, perhaps like the old remastersys.

Is there a way to copy just the entire ubuntu data portion and not the gpt? Maybe an rsync command ? Maybe filezilla or clonezilla ?

Sorry if I'm sounding stubborn or stupid. I'm just asking.

I have to say this forum is very helpful and amazingly fast in response times.

Thanks for all your help,
M...

---

### Post by dragonfly41 on 2023-11-26
[COLOR=#000000]> Imagine that I was in charge of 73 various computers (desktops, laptops of different sizes and makes), and my task was to make them all dual bootable and make ALL of the ubuntu partitions identical to my desktop. 
Personally if I had that task I would create a Ubuntu Virtual desktop in the cloud and give a user licence to each party using different devices. If it was simply an educational desktop (nothing sensitive) perhaps linked to eLearning, you could try virtual desktop account such as RollApp.com. Context needs to be explained further. Security in particular.[/COLOR]

---

### Post by oldfred on 2023-11-26
I have a full install on a ssk external SSD.
So I run this command.
rsync -aurvP --delete --exclude-from=backup_excludes.lst /home /media/fred/root1-ssk

The excludes.lst is so I do not copy a lot of temporary or archive type files.
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders) & 

i use latest LTS as main working install, but like to install every version to see differences, so change to new LTS is a bit more understood. So I now have a script with most of my apps to install which I use for the temporary installs. But I do backup list of all installed apps, and use it for new LTS install.

If upgrading, you may want to edit it to remove obsolete, old kernels or others. It will not re-install anything already installed.
[https://help.ubuntu.com/community/ReinstallingSamePackages](https://help.ubuntu.com/community/ReinstallingSamePackages)
from lovinglinux - use dpkg to list installed apps
[https://ubuntuforums.org/showpost.php?p=7157175&postcount=5](https://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

---

### Post by box02-02 on 2023-11-26
I need to learn more about rsync, but it would seem that it may be the solution for me. Use it to backup "/" from my desktop ubuntu partition and restore to "/" to the laptop ubuntu partition ??

How about something like this in its simplest format ('excludes' and other options omitted for simplicity):

sudo rsync -aAXv --delete /desktopubuntu /laptopubuntu

I don't know if I got all the switches right, but would this copy my desktop ubuntu partition (without the gpt - just pure data) to the laptop which would originally contain the fresh installed ubuntu ?

Thanks for your patience,
M...

---

### Post by oldfred on 2023-11-26
You are copying from /home to a /home, but they cannot be both mounted as /home.
Are you copying to a flash drive or external SSD? 
Or using network and need SSH type configuration? 
Others know those commands better, as I use NFS which takes a bit of setup, but once done it easy to use.

---

### Post by dragonfly41 on 2023-11-26
Why do you ignore the "73 users" question?

---

### Post by box02-02 on 2023-11-26
[COLOR=#8b4513][SIZE=2][/SIZE][SIZE=2]*Are you copying to a flash drive or external SSD? *[/SIZE][/COLOR][COLOR=#afeeee][SIZE=2]
[/SIZE][/COLOR]On first thought, I would transfer the desktop/ubuntu partition to the laptop as follows:

Boot the Desktop from of a bootable ubuntu USB which would "see" a backup of my desktop/ubuntu partition.
Mount a usb which would have an empty 85gb ext4 partition. 
rsync the **Entire** desktop/ubuntu partition to the usb.

Then

The laptop would have a freshly built (from .iso) ubuntu partition.
Boot the Laptop from a bootable ubuntu USB which would "see" the freshly built laptop/ubuntu partition. 
Mount the "rsync **Entire** desktop/ubuntu partition" usb from above, and use rsync to restore the data to the laptop/ubuntu partition.

Then

 boot boot & pray.

[COLOR=#8b4513][SIZE=2]*You are copying from /home to a /home, but they cannot be both mounted as /home.*[/SIZE][/COLOR]
I'm confused here. I want to copy from desktop ubuntu  **"/"** (root - the top of the heap - the entire ubuntu partition) to laptop ubuntu **"/"**. Can rsync do this ?? why are you talking about "/home" ?

You must ne patient with me :).

Thanks,
M...

---

### Post by oldfred on 2023-11-27
If doing a new install, you do not need to copy / (root). Each user has a /home with his own configuration files most often in hidden (.) files and data. Only if you change some system settings, may you want to copy those from /etc. I change grub, but just copy that file into /home so backup of /home includes it also. Then the only additional thing you need is the list of installed apps. I export that on a regular basis so also in my data. I have a data partition separate from /home so have to backup both.

If booted into your old system, the command I posted on rsync is what you need. But you have to set mount point and give yourself ownership and permissions to write into an ext4 partition.  I always label partitions (gparted or command iine), particularly those I only use sometimes, so the get mounted by label not some very long UUID that is difficult to type and understand if more than one partition is mounted. Then mount is /media/fred/{label} by the file browser. Otherwise I manually mount.
Another example of rsync.
[https://ubuntuforums.org/showthread.php?t=2487333](https://ubuntuforums.org/showthread.php?t=2487333)

If both systems are on same network, you can directly copy using SSH.
Backup should be from unmounted partitions, so files are not open. 

Trailing slashes matter - I fall into the occasional user and have to review each time I create a new rsync command.
[https://wiki.archlinux.org/title/Rsync#Trailing_slash_caveat](https://wiki.archlinux.org/title/Rsync#Trailing_slash_caveat)
When using "/" at the end of source, rsync will copy the content of the last folder.
When not using "/" at the end of source, rsync will copy the last folder and the content of the folder.
Note: The trailing slash (/) on the source directory modifies the behavior of the rsync command.

---

### Post by box02-02 on 2023-11-27
Okay - thanks for all the responses. I will "play" and make it work. I will get back to you when I'm done.

In the meantime I will mark this thread as "solved".

Thanks for all your help,
M...

---

### Post by box02-02 on 2023-11-27
Through a series of events when trying to change my email address, my username has been changed and I no longer "own" the first post so I cannot mark it as solved. 

I will report this and see if the problem can be repaired.
Thank,
M..

---

