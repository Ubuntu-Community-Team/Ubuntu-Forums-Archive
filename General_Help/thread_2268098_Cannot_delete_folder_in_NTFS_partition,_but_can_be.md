---
title: "Cannot delete folder in NTFS partition, but can be moved"
date: 2015-03-06
forum: General Help
---

### Post by pendechosen on 2015-03-06
Basically when I 'ls' the folder it shows 'Input/output error', when I 'rm - rf' the folder, it says 'Directory not empty'.
The following pic is more illustrative. I don't know what error is it, although it indicates an I/O error, the folder 'YGOPRO' can still be moved to a different path.
[ATTACH=CONFIG]260485[/ATTACH]

This is the story:
I downloaded the YGOPRO game in a .rar archive about 624MB. 
The archive contains about 20k files and I used archive manager to unrar the main files to a folder named 'YGOPRO' in an NTFS partition.
I then used an Windows XP guest OS in VMware Workstation to mount the whole NTFS as a shared folder, browsing the folder 'YGOPRO' was successful, both in Ubuntu and XP. 
Then I played the game for awhile.
I irresistibly slept, left unnoticed the battery power, the laptop force shutdown-ed.
When I reopened the folder in the Windows XP guest OS in VMware Workstation, the system showed a warning of 'Access Denied'.

I used Nautilus in Ubuntu to browse the folder under my non-root account, it took like 20 secs, during the operation other programs could not even run, 
for example, Chrome could not load a new web page nor opening a new tab, but scrolling a current web page is possible. 
And after operation no files were shown in the folder, the folder could not be deleted, too.

Then I discovered that the folder can be moved, however, I think this is unlikely a Disk problem.. but something to do with VMware or NTFS file system etc...
Worth mentioning I have no backup of my partition at the moment..it is about 900GB = = and 90% of the space is used. 

Now I just want to eliminate the folder, if anyone can offer some ideas, thx~

-----------------------------------Updated Texts-----------------------------------------------

Thanks @matt_symes @Mark Phelps , running chkdsk really helped lol, it was sort of problem in NTFS indexing..

After some googling I finally had an idea to run chkdsk in linux and that is using VirtualBox.
[COLOR=#141823][FONT=Helvetica]1. Unmount the NTFS partition
2. Create a virtual disk linking an NTFS partition under root, like:[/FONT][/COLOR]
[COLOR=#141823][FONT=Helvetica]sudo VBoxManage internalcommands createrawvmdk -filename "/var/OS.vmdk" -rawdisk /dev/sda2#
3. Run virtualbox under root: sudo virtualbox
4. Put the virtual primary master hard disk file with windows copy somewhere other than in the NTFS partition...
5. In virtualbox, create a new virtual machine, append the .vmdk, the one with windows copy as IDE primary master, one with the NTFS partition as IDE primary slave.
6. Run the virtual machine..
[/FONT][/COLOR]

Results:
[ATTACH=CONFIG]260500[/ATTACH][ATTACH=CONFIG]260501[/ATTACH]

The folder can be read again, thx so much guys, without your advice I would not force myself to run chkdsk because my windows OS can neither enter startup in normal nor recovery mode :(

---

### Post by matt_symes on 2015-03-06
Hi

Sounds like file system corruption as you said. That can cause these I/O errors.

Can you run chkdsk on the partition from windows ?

Kind regards

---

### Post by Mark Phelps on 2015-03-06
Taking a very long time to browse a folder is often an indication of hard disk problems, as the sectors in use get read over and over until either the read is successful, or the OS times out.

You need to run CHKDSK from inside XP to fix the filesystem corruption.  And, before you ask, NO, there is no equivalent you can run from Linux.

---

### Post by pendechosen on 2015-03-07
> **matt_symes said:**
> Hi

Sounds like file system corruption as you said. That can cause these I/O errors.

Can you run chkdsk on the partition from windows ?

Kind regards
> **Mark Phelps said:**
> Taking a very long time to browse a folder is often an indication of hard disk problems, as the sectors in use get read over and over until either the read is successful, or the OS times out.

You need to run CHKDSK from inside XP to fix the filesystem corruption. And, before you ask, NO, there is no equivalent you can run from Linux.
[COLOR=#000000]Thanks @matt_symes @Mark Phelps , running chkdsk really helped lol, it was sort of problem in NTFS indexing..[/COLOR]

[COLOR=#000000]After some googling I finally had an idea to run chkdsk in linux and that is using VirtualBox.[/COLOR]
[COLOR=#141823][FONT=Helvetica]1. Unmount the NTFS partition
2. Create a virtual disk linking an NTFS partition under root, like:[/FONT][/COLOR]
[COLOR=#141823][FONT=Helvetica]sudo VBoxManage internalcommands createrawvmdk -filename "/var/OS.vmdk" -rawdisk /dev/sda2#
3. Run virtualbox under root: sudo virtualbox
[/FONT][/COLOR][COLOR=#141823][FONT=Helvetica]4. Put the virtual primary master hard disk file with windows copy somewhere other than in the NTFS partition...[/FONT][/COLOR][COLOR=#141823][FONT=Helvetica]
5. In virtualbox, create a new virtual machine, append the .vmdk, the one with windows copy as IDE primary master, one with the NTFS partition as IDE primary slave.
6. Run the virtual machine..
[/FONT][/COLOR]

[COLOR=#000000]Results:
[/COLOR][ATTACH=CONFIG]260503[/ATTACH][ATTACH=CONFIG]260502[/ATTACH]

[COLOR=#000000]The folder can be read again, thx so much guys, without your advice I would not force myself to run chkdsk because my windows OS can neither enter startup in normal nor recovery mode [/COLOR]:sad:

---

