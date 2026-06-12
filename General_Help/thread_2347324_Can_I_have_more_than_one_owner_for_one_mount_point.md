---
title: "Can I have more than one owner for one mount point?"
date: 2016-12-23
forum: General Help
---

### Post by javierdl on 2016-12-23
I am making a mount point for the Steam files of my daughter, so she can install games there from her Ubuntu account. The mount point is in a separate HD's partition. 
I already created the mount point, now I just need to declare the ownership. I did this before for myself, so naturally I made myself the owner of my own mount point. However, since I'm the one managing this, I thought I should make my daughter AND myself owners, not just her.
What do you think?

Thanks in advance guys :)

JDL

---

### Post by &amp;KyT$0P# on 2016-12-23
Have you tried using groups?

You would create a new group, and add both you and her to it.  Then, on the mountpoint, use appropriate [FONT=Courier New]sudo chgrp[/FONT] and [FONT=Courier New]chmod g+w[/FONT] commands.

Refer to [FONT=Courier New]man chgrp[/FONT] and [FONT=Courier New]man chmod[/FONT] for more info.

---

### Post by javierdl on 2016-12-23
Thanks halogen2 :)

I am trying it now. But every time I try to make a new group, it tells me that its ID already exists, and I have tried a few already. Is there a way to see all existing/taken IDs?

Thanks

---

### Post by javierdl on 2016-12-23
Never mind!
I found out with the "tail" command ;)

---

### Post by javierdl on 2016-12-23
Ok, so I created the group, and added ourselves to it. 
Now, am I supposed to use either chgrp or chmod (or both), instead of chown? Is this right?

JDL

---

### Post by SeijiSensei on 2016-12-23
```

cd /path/to/the/mount/point
sudo chown you:yourgroup . -R
sudo chmod 775 you:yourgroup -R

```
where "yourgroup" is the one you created that includes your daughter.  The -R switch tells these programs to "recurse" down the directory and apply the changes to all files and directories it finds.  775 permissions gives you and your group's members read, write and "execute" privileges, and grants read and execute privileges to everyone else.  "Execute" privileges when applied to a directory means you can list the directory's contents.  Obviously execute privileges applied to a program means you can run that program.

---

### Post by javierdl on 2016-12-23
That's great! Thank you so much SS :)

Apart from that, I have a game's folder in yet another partition. We were able to run it by running its .sh file before. I don't know it it's just a coincidence, but now that I had created that group (I'm just missing to assign ownership) we can no longer run the game. It opens, but right as soon as it's done loading, it quits/crashes :(
Do you think I'll have to claim ownership for it somehow?

---

### Post by &amp;KyT$0P# on 2016-12-23
There is a slight typo in the commands.  See if this works better.
```
cd /path/to/the/mount/point
sudo chown -c -R you:yourgroup .
sudo chmod -c -R 775 .
```

---

### Post by javierdl on 2016-12-23
Excellent!
It worked beautifully! Thank you so much halogen2 :)

And the other game (SuperTuxKart2) is working again!

JDL

---

### Post by javierdl on 2016-12-24
To gain a better grasp of how permissions work in a practical setting, I wanted ask: 
For Steam, since my daughter and I have different games installed, and so forth, I thougt it would be best to do 2 separate installations. And so I did.
But for, let's say a simpler program, like a word-processor. Let's say I have it in an ext4 partition in a separate drive (other than where Ubuntu is), then do as instructed above: create a group where I'd add the 3 of us. So I guess the question is: would Ubuntu be able to keep track of differences among us in a preference file for each of us? Or something similar? This is when I'm lost.
Thanks guys :)

---

### Post by SeijiSensei on 2016-12-25
In general you should let Ubuntu manage the location of all installed programs.  They will be available to all users that way without any extra effort on your part.  Don't put programs in idiosyncratic locations unless you only want to use them yourself.  Install everything from the repositories and let Ubuntu handle the location of files.  For instance, the best word processors are Abiword or Writer, part of the Libreoffice suite.  I suggest using the latter to begin with.  You can install it from the repositories with the graphical software manager or from the terminal with the command

```
sudo apt-get install libreoffice
```

Once you install it, you'll see its various component programs (Writer, Calc, etc.) in the main program menu.

Most standard programs that you install from the repositories keep individualized configurations in your /home directories.  Over the past few years these configurations have become more centralized in the directory called /home/username/.config.  Because the name starts with a dot, it is "hidden," that is, it does not appear in a normal directory listing.  However you can see hidden files in the terminal by using the command "ls -a" or in a graphical file manager with a command like Alt-Period.  (That works in KDE's Dolphin; I don't know about Nautilus.) 

If you look in the .config directory you should see a libreoffice directory there with your personalized settings.

You should always save documents (and just about anything else) in your home directory where you have full privileges.  On Ubuntu machines these files will be visible and readable by everyone by default.  Other distributions like RedHat and its derivatives (CentOS, Scientific Linux, etc.) have more restricted privileges and limit access to home directories to just their users.

If your system has limited disk space for the main directory tree under /, but you have another device available, you can create a partition on that device, format it as ext4, and mount it as /home.  If you've been using the system for a while, chances are that you already have stuff saved in the original /home that you'll want to move.  Take a look at this post of mine: [https://ubuntuforums.org/showthread.php?t=2343317&p=13570363&viewfull=1#post13570363](https://ubuntuforums.org/showthread.php?t=2343317&p=13570363&viewfull=1#post13570363) starting with the paragraph that begins "You would do the same thing to mount the filesystem as /home."  That describes how to preserve the current home directory and mount a new filesystem as /home.  You can then copy the files you need from the old location to the new one.

---

### Post by javierdl on 2016-12-25
I'm so glad I asked :)
Thank you so much for the complete feedback SS :)

---

### Post by javierdl on 2016-12-26
SS,
I read the other thread. It sounds very interesting and useful what TheFu was saying about using LVMs. I guess I'll leave that for sometime in the future.
From what I understood in your instructions, in the end we have the option to either use this type of identification: "[COLOR=#000000][FONT=&amp]/dev/sdb1[/FONT][/COLOR]", or the actual partition's ID. But I also understood that it's probably best to go with the latter, is that right?

And btw, just to be sure we're on the same page, once I have moved my home out of my SSD into a (larger) partition in my HD, then every time I install a program it'll be placed in the latter one, right?

JDL

---

### Post by SeijiSensei on 2016-12-26
1)  UUIDs are a better choice if you use devices like USB thumbdrives and the like.  It's sometimes possible for devices to end up with different /dev/sdX designations depending on the order they are activated by the BIOS.  UUID are impervious to that, so that has become the recommended method.

2) No, your programs will still be installed under /.  Most programs reside in /usr/bin with supporting files in places like /usr/lib, /usr/share and /etc.  It's possible to mount each of /usr, /var and /home on separate partitions.  None of these partitions are used during boot up when the machine is running in "single-user" mode.  During that time the root user is in charge, and programs needed in that mode reside in /bin and /sbin.  During the boot sequence the machine switches to "multi-user" mode and mounts /usr, /var and /home if they are on separate devices.  I recommend reading [https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview) for a quick overview of how files in Ubuntu are organized.  For a more in-depth discussion see [https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

I have a basic Kubuntu 16.04 installation set up for testing in a VirtualBox virtual machine.  It uses about 7 GB of disk space for everything including programs and libraries.  Even if I installed a lot of additional software I doubt it would be using more than about 10 GB total.  Most *nix programs are pretty small in comparison to Windows software, and much much smaller than games.  Just last night I noticed that Steam wanted to use over 30 GB to install the Final Fantasy X/X-2 combo pack!  

For the time being I'd suggest only migrating /home to another device if you're short on disk space.  I don't know how much space you allocated to Ubuntu for starters, but if we're talking 100 GB or more, it will take a long time to fill that.

---

### Post by javierdl on 2016-12-27
Boy! Am I glad I asked again! ;)
Thank you ever so much SS :)
I'll do as you suggested then, I'll just migrate my /home. And take it from there.

Happy New Year! (if it applies) :)

---

### Post by javierdl on 2016-12-30
I understand we probably have digressed somewhat from the original thread. But let's just say that my efforts to start a new one with a clearer goal got halted in a rather sudden way :(
Hence I'm back. My present purpose is to make more space in the main drive
> [COLOR=#000000]*device fs_type label mount point UUID*[/COLOR]
[COLOR=#000000]*-------------------------------------------------------------------------------*[/COLOR]
[COLOR=#000000]*/dev/sda1 vfat (not mounted) D45B-1044*[/COLOR]
[COLOR=#000000]*/dev/sda2 vfat (not mounted) 5968-2E1F*[/COLOR]
[COLOR=#000000]*/dev/sda3 ext4 Partition_377 /media/nelly/Partition_377 1cc33a38-c617-4e9e-acf4-19c79415609e*[/COLOR]
[COLOR=#000000]*/dev/sda4 swap (not mounted) e863d0f6-0ab2-4f1f-9fa3-55a652b02283*[/COLOR]
[COLOR=#000000]*/dev/sda5 ext4 /mnt/steam-nelly 3ff8f52b-26d0-415f-b890-9ed186c00c5b*[/COLOR]
[COLOR=#000000]*/dev/sdb1 vfat /boot/efi A023-0678*[/COLOR]
[COLOR=#000000]*/dev/sdb2 ext4 (not mounted) fb4b6aab-3aa9-4f22-ac08-957d3765f525*[/COLOR]
[COLOR=#000000]*/dev/sdb3 ntfs (not mounted) 01D21F5BB33EFBA0*[/COLOR]
[COLOR=#000000]*/dev/sdb4 ntfs Win10 (not mounted) 7B637EED5EAE730B*[/COLOR]
[COLOR=#000000]*/dev/sdb6 ext4 / 649ff9fc-1a34-4427-9ca4-9310bff5963a*[/COLOR]
[COLOR=#000000]*/dev/sdb7 swap [SWAP] db1e3a9e-cd9d-48de-8e42-e674b4fdb699*[/COLOR]
[COLOR=#000000]*/dev/sdb8 ext4 /home 1c6d2b39-7de5-4e00-a7d4-7e237fb789f8*[/COLOR]
[COLOR=#000000][I]/dev/sdc1 ntfs TOSHIBA /media/javier/TOSHIBA A46CE4BB6CE488FE


[/I][/COLOR]

[COLOR=#000000]sdb - This is where I have Ubuntu, home, most programs. Except for Steam games.[/COLOR]

[IMG]https://sites.google.com/site/javierwebfolio/temp/home_location.png[/IMG]

[COLOR=#000000]sda - This is where I have more space. I thought of moving things to sda3 (Partition_377).[/COLOR]

[IMG]https://sites.google.com/site/javierwebfolio/temp/new_home.png[/IMG]

[COLOR=#000000]One concern I have about moving /home to sda3, is that presently if I was the last user accessing sda3, then the next user won't have access to it, unless he/she unmounts it first, then mounts it. So my concern is: once home is there, will we be denied access, then we'll have to unmount it and mount it back? That would be a drag...[/COLOR]

[COLOR=#000000]Assuming that won't be a problem, then as I recall, the next step will be to boot up from a Live USB, so that no system files will be open/running, then I'll be able to rsync home with this commands:[/COLOR]
[COLOR=#000000][I]cd /
sudo rsync home oldhome
sudo mkdir home
sudo mount /dev/sdb1 home

[/I]I did try the above before, except the Terminal told me that it couldn't perform the commands while some system files where open/running.
[/COLOR]
[COLOR=#000000]Am I in the right path so far?[/COLOR]

[COLOR=#000000]Thanks guys [/COLOR]:smile:

---

### Post by Keith_Helms on 2016-12-30
> [COLOR=#000000]One concern I have about moving /home to sda3, is  that presently if I was the last user accessing sda3, then the next user  won't have access to it, unless he/she unmounts it first, then mounts  it. So my concern is: once home is there, will we be denied access, then  we'll have to unmount it and mount it back? That would be a drag...[/COLOR]

Each user should have a subdirectory under /home. (/home/javier and /home/nelly for example)  The partitition you mount to use for /home should be permanently mounted using fstab and whoever signs in should not have to do any mounting or unmounting for that partition.

Example excerpt from /etc/fstab
```
# /home was on /dev/sda3 during installation
UUID=[COLOR=#000000]1cc33a38-c617-4e9e-acf4-19c79415609e[/COLOR] /home     ext4    defaults        0       2
```

---

### Post by javierdl on 2016-12-31
I see. Great!
Thanks KH :)

JDL

P.S. Since I have not set to do this (moving home elsewhere yet), therefore, most likely more questions will pop up later, I'll leave this thread as unresolved for now. If this is ok...

---

### Post by SeijiSensei on 2016-12-31
Your current /home should have separate directories for each user already.  When you copy it to the new device, those directories and files will be transferred intact.

/home should have root:root as its owner:group, and 755 privileges.  That is the way it should look now, too.

---

### Post by javierdl on 2017-01-06
halogen2,

I had meant to ask, the chmod command line does not use "you:yourgroup", is this due to the fact that you were located at the mount point already?
```
cd /path/to/the/mount/point
sudo chown -c -R you:yourgroup .
sudo chmod -c -R 775 .
```

---

### Post by &amp;KyT$0P# on 2017-01-06
> **javierdl said:**
> halogen2,

I had meant to ask, the chmod command line does not use "you:yourgroup"...
... because [FONT=Courier New]chmod[/FONT] is not [FONT=Courier New]chown[/FONT]. :)

[FONT=Courier New]chown[/FONT] is for **ch**anging **own**ership.  [FONT=Courier New]chmod[/FONT] is for **ch**anging **mod**e (aka permissions).  Again, refer to [FONT=Courier New]man chmod[/FONT] and [FONT=Courier New]man chown[/FONT] for more info.

---

