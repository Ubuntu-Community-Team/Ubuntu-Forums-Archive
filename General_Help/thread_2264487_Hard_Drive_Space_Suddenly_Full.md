---
title: "Hard Drive Space Suddenly Full"
date: 2015-02-07
forum: General Help
---

### Post by Clarke_Collins on 2015-02-07
I am pretty new to the Ubuntu world, having most of my computer experience with Macs. But I recently bought a PC to act as a Plex media server and am running the newest version of Ubuntu to save on general system resources.

All was going quite fine until today. I have a 1 TB HDD and ~300 GB worth of movies on the drive. But randomly this afternoon, my system decided to show that I have ~928 GB being used with only a few GB free to use. I ran the disk usage utility and it is showing totally conflicting information. It "confirms" that I am using 928 GB, but the actual folders don't add up to that. The largest folder I have is 306 GB and is nowhere near the 928 GB number. I tried emptying the trash, although that was only a few MB at best. I tried pokling around to see if maybe I duplicated a folder or something in error, but I'm just not seeing where the heck the other 600+ GB is that the system is showing as being used. I attached a screenshot of the disk usage report, if that helps.

I apologize if this is not enough information to go by, but I am not very computer savvy in this regard. Any help would be most appreciated.

[ATTACH=CONFIG]259810[/ATTACH]

---

### Post by kpatz on 2015-02-07
Open a terminal and while in your home folder run the command :
```
sudo du -xd 1
```
Find which directory is using all the space, then cd to that directory and re-run the above command until you've drilled down to the culprit directory.

---

### Post by Clarke_Collins on 2015-02-07
> **kpatz said:**
> Open a terminal and while in your home folder run the command :
```
sudo du -xd 1
```
Find which directory is using all the space, then cd to that directory and re-run the above command until you've drilled down to the culprit directory.

Thank you for the tip, but that didn't really help. The information on the directories definitely has the biggest chunk on my desktop, which is where my Plex folder is, but it's still only showing as ~300 GB. Every other directory is pretty tiny. Here's the text:

19572    ./.mozilla
8    ./.qshutdown
40    ./.compiz
4    ./Music
4    ./deja-dup
76    ./.java
712    ./.adobe
16    ./FrostWire
636    ./Pictures
4    ./Downloads
298924192    ./Desktop
12    ./.dbus
5452    ./.local
752    ./.config
4    ./Documents
52    ./.gconf
4    ./Templates
4    ./Public
4    ./Videos
100    ./.macromedia
285108    ./.cache
4652    ./.frostwire5
899081592    

Where is this amounting to over 900 GB of stuff?

---

### Post by deadflowr on 2015-02-08
disk usage analyzer is not really clear on it's design means.
The 100% used listed in the dropdown for your user means that 100% of the space used in the home directory is used by your user, not that 100% is being used.
If that makes any sense to you.
(I think, though, that if you closed the warnoing bar --the yellow section across the top, it should have a small section with the real values of the space in question; ie, total space and space used)

A better picture of the overall space used can be found either within the system monitor tool >> tab over to the "file systems" tool.
Or a quick terminal command
```
df -h
```

Edit: To add, think of it like this.
The top level (/) is using 100% of the space used. Makes sense, as the / should be the only top level directory on your current partition.
Of that space the /home folder is using 93%.
Of the home folder space used, your user's folder is using 100% of the space used by the home folder.
Hope that clarifies somethings.

---

### Post by Holger_Gehrke on 2015-02-08
> **Clarke_Collins said:**
> Where is this amounting to over 900 GB of stuff?

The sub-directories are about 300 GB, the sum is about 900 GB - so there are about 600 GB in files in your home directory. Those might be hidden (their names would begin with a "."). Execute this command in your home directory:
```

ls -alSr

```
(list **a**ll files in **l**ong format ordered by **S**ize **r**eversed). My guess would be that your media server used your $HOME to dump temporary files from some format conversion and didn't remove them when it was done.

---

### Post by Clarke_Collins on 2015-02-08
> **Holger_Gehrke said:**
> The sub-directories are about 300 GB, the sum is about 900 GB - so there are about 600 GB in files in your home directory. Those might be hidden (their names would begin with a "."). Execute this command in your home directory:
```

ls -alSr

```
(list **a**ll files in **l**ong format ordered by **S**ize **r**eversed). My guess would be that your media server used your $HOME to dump temporary files from some format conversion and didn't remove them when it was done.

I think you might be right about Plex using the space. I ran a movie this morning and the space continues to go down. I think this is definitely the culprit, but I cannot figure out how to find a folder to clear this out. Doing a pretty thorough search, I cannot find any folders that even remotely come close to the 900 GB that the system is telling me are being used up. The most I can find is my actual Plex movie file folder, which is the 300 GB folder. Every scan says it is in my "home" folder, but this doesn't help me locate the sync files from Plex to delete them.

And I'm not sure how to read the df -h screen, but here are the results from that: 
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       913G  866G  809M 100% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           388M  1.4M  386M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.9G   88K  1.9G   1% /run/shm
none            100M   80K  100M   1% /run/user

Here are the bottom few lines from the ls -alSr run, as well:
drwx------  3 collinsfam collinsfam         4096 Dec 25 22:16 .compiz
drwx------ 20 collinsfam collinsfam         4096 Feb  7 19:33 .cache
drwx------  3 collinsfam collinsfam         4096 Dec 30 17:29 .adobe
drwxr-xr-x  3 root       root               4096 Dec 25 21:38 ..
drwxr-xr-x 24 collinsfam collinsfam         4096 Feb  7 18:14 .
-rw-r--r--  1 collinsfam collinsfam         8980 Dec 25 21:38 examples.desktop
-rw-r--r--  1 root       root       614236230773 Jan  7 17:04 testdisk.log

I don't understand what these results mean, so maybe someone can help me make sense of them or point me in the right direction. Thank you all for your patience and help!

---

### Post by steeldriver on 2015-02-08
... looks like you have a ~600GB (614236230773 byte) testdisk.log file

---

### Post by Clarke_Collins on 2015-02-08
> **steeldriver said:**
> ... looks like you have a ~600GB (614236230773 byte) testdisk.log file

That's interesting and is just about the exact size of the discrepancy I'm seeing. Is that abnormal? And does anyone know what that file is and if it's safe to find and remove?

---

### Post by Clarke_Collins on 2015-02-08
Actually, I think I know what this is. I bought an external HDD off of ebay and it wasn't working properly. So I installed test disk to see if it could find the problem and figure out what the heck it was trying to do with its partitions. Long story short, it was a broken drive (lesson learned on that one), but apparently it must have kept some kind of information about that testing on my HDD. I don't need the TestDisk app anymore, so I removed the app and deleted the log file. 

Voila! I'm back to 600+ GB free.

Thank you all for your help! Case solved.

---

### Post by Yellow Pasque on 2015-02-08
Nice. Please mark the thread solved.

---

### Post by Clarke_Collins on 2015-02-08
How do you mark it solved?

---

### Post by Yellow Pasque on 2015-02-08
Right above the first post, there is a "Thread Tools" menu.

---

### Post by Clarke_Collins on 2015-02-08
> **Temüjin said:**
> Right above the first post, there is a "Thread Tools" menu.

Excellent.

Thank you again!

---

