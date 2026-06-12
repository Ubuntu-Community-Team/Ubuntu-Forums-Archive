---
title: "Storing files on secondary drive by default"
date: 2021-02-22
forum: General Help
---

### Post by jgwphd on 2021-02-22
I am using Ubuntu 20.10. I have an SSD for boot up and it is where the OS lives. I have second, but mechanical, hard drive drive. Is their some "general way" to distribute my storage usage among the two drives. For example; can I configure the system so that I use the mechanical drive as the default for all my application and non-OS activities and use the SSD for system or OS activities? As an example, I use Timeshift but I have to configure it to send the data to an external USB connected drive. Is there some default setting or way to avoid using the SSD as the first choice, or eliminate presenting the SSD as a choice, whenever I install or use an application or store a file (add music, do a download, edit a document...etc.)? Thanks for any advice or pointers.

---

### Post by oldfred on 2021-02-22
I used to keep system (and /home) on SSD and all data folders like Documents, Music, etc on HDD. 
But now have larger SSD, so data on SSD, but still in separate partition. Now HDD is mostly backup and test installs.

[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198) &
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by CatKiller on 2021-02-22
Linux doesn't deal in drives. Linux deals in filesystems and mount points. You can essentially mount any filesystem anywhere, for any purpose.

The quick and easy method is to, at install time, mount (a partition of) your SSD as / and (a partition of) your hard drive as /home. That way you get your OS and applications on your SSD, and your settings and personal data on the hard drive. Lots of people do that, and it's pretty straightforward being just the one step.

You can also get creative, and have a bunch of partitions mounted a bunch of places. Or mount them to one place and then symlink them to another place. 

The OS doesn't care: it will just follow the path to wherever. You get to choose the underlying storage that a particular path ends up on.

---

### Post by jgwphd on 2021-02-22
I am past "install time" but I see what you are getting at. Thanks! Now my question is there a way to change my "existing system" so I can "mount (a partition of) your SSD as / and (a partition of) your hard drive as /home." (or maybe just move some of the other directories to the HD such as music or downloads...etc. to start with    ... possibly just move one of them to learn and see how it works). Do you have any command suggestions. Please be explicit with commands because I finally got my system working exactly the way I want it :-)  BTW this machine is dual booted with windows, so I don't want to screw up windows even though I only use it 1% of the time. Again thank-you to everyone!

---

### Post by oldfred on 2021-02-22
This has all the instrucitions to move /home to another partition.
To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) & 
[https://ubuntuforums.org/showthread.php?t=2455822&p=14010437#post14010437](https://ubuntuforums.org/showthread.php?t=2455822&p=14010437#post14010437)

The links I posted above have details for copying all /home data from your data folders (or just one) and then mount a data partition or more if desired, give yourself ownership & permissions and link folder(s) in that data partition back into /home. Make sure you have good backups of data before making any changes. You should have regular backups anyway.

I now find my data partition does not grow very fast, but with grand-kids my photos grow a lot. I am now re configuring to have a data partition for most data, and a separate larger photo partition.

---

### Post by CatKiller on 2021-02-23
> **jgwphd said:**
> Do you have any command suggestions. Please be explicit with commands because I finally got my system working exactly the way I want it :-)  

No commands. Even if you'd described your setup enough so that we could give them to you, which you haven't. There are two computer tasks where just the idea of them gives me chills: letting Windows write to UEFI, and disk partitioning without a visual representation of what you're doing.

So, some general information to help you navigate the information oldfred has provided.

The way you control which filesystems are mounted where is just a text file - /etc/fstab (for filesystem table). The other thing you'll find useful is symbolic links (symlinks) that make one location point to a different location.

As an example, I have a NAS which gets mounted on my desktop machine to various locations under /mnt. Particular directories from there are symlinked to my ~/Downloads and ~/Music directories, so that none of the applications that use those locations have to have any idea that those places are actually on a completely different machine. 

The command to make a link is ln, and to make a symbolic link it's ln -s. Or most file browsers will have the option to make a link as a drag-and-drop operation.  

You should use Windows formats for Windows and Linux formats for Linux. If you've got flat data that you want to share between the two you can use NTFS (since Linux can read and write to it, and Windows is really bad with anything else) but don't use it for anything where ownership and permissions are significant, since NTFS doesn't support them. That includes your Steam library, if you have one. Don't use NTFS if you don't use Windows. When it eats itself you need Windows tools to repair it. For things that will only be accessed through Linux, use a Linux format like ext4. 

If you need to edit your partitions, you can't do that if they're already mounted. That means that if you need to change your / partition then you need to use a live USB. You can edit other partitions as long as they aren't mounted. Gparted is the tool you'd use either way - it's already included on the Ubuntu installer image. Back up important information before you fiddle with partitions, just in case.

---

### Post by jgwphd on 2021-02-23
Many thanks for oldfred and catkiller. I'll review all your linked information and just try moving one directory (e.g. /Downloads) or symbolic link to one directory at first. I was thinking to move the /Download directory but I noticed that I have an hplip directory in there. Will this screw up my HP printer (I guess it's ok if it does because I can reinstall it somewhere else). But I am kinda hoping the move will works seamlessly as the documentation pointed to by oldfred seems to suggest, ...or am I being naive.

---

### Post by oldfred on 2021-02-23
I have not had issues.
Back when I had an HP, the download was into /home/Downloads, but the script installed to normal Linux locations.

Make sure you have copied everything in Downloads to your new folder in a data partition. My first time I missed a folder and the mount of the link hid the data in the original /home folder.
Best to have good backups.

---

### Post by jgwphd on 2021-02-24
Thanks for the information and suggestions!!!!

---

