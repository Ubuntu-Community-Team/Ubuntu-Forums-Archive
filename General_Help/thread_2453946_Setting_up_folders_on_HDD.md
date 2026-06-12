---
title: "Setting up folders on HDD"
date: 2020-11-19
forum: General Help
---

### Post by KieranFitzgerald on 2020-11-19
I have just reinstalled UBUNTU 16.04 64 bit on my system.  I have an SSD which I used for the install including Home but I want to have the files Pictures, Downloads etc on my 1Tb hard drive.   How do I do this?  I have tried setting up a simlink but can't get it to work.  The HDD has a single partition /dev/sdb1 ext4 mounted as  /media/kieran/Data1.   I have made a directory "Downloads" on it.   Can someone help with setting this up.
Thanks

---

### Post by oldfred on 2020-11-19
This is how it do it. And now since I do multiple installs, I have a small script that deletes folders & adds the links.

You have to have it mounted in fstab, so reboot always sees the data partition. And you have to give yourself ownership & permissions to use the data.

But it does not check for data in a partition as I only run it on a new install where I am sure folders like Documents are empty.
First time or two I did it totally manually, deleting one folder & linking that folder.

[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by DuckHook on 2020-11-19
At the risk of digressing from your main issue, you state:> **KieranFitzgerald said:**
> I have just reinstalled UBUNTU 16.04 64 bit on my system.
If reinstalling anyway, why 16.04? Xenial will run out of support in April, 2021. If going to the trouble of customizing fstab, symlinking, etc, perhaps best to do all this work on a version that won't be obsolete in five months.

---

### Post by KieranFitzgerald on 2020-11-20
Should I go to 18.04 or 20.04?

---

### Post by oldfred on 2020-11-20
I typically do a new install of the latest LTS - long term support version when it comes out.
So I suggest 20.04.

But I still have install of 18.04 as I use the linking into my data partition in all installs. And then only have 30GB for / (root). But I also move Firefox & Thunderbird folders into my data partition, remove all snaps & regularly houseclean older log files & whatever cruft I can find. My 20.04 is using about 8.5GB of my 30GB / partition which includes /home but not any of the data.

---

### Post by DuckHook on 2020-11-20
> **oldfred said:**
> So I suggest 20.04.
&#8593; \\:D/

…but try it with a LiveUSB first. If no problems, then it should work well for you installed to bare metal.

---

### Post by KieranFitzgerald on 2020-11-20
Just upgraded to 18.04 all appears to be stable.  I will try 20.04.  Will upgrading change the way the HDD folders are set up?

---

### Post by DuckHook on 2020-11-20
> **KieranFitzgerald said:**
> Just upgraded to 18.04 all appears to be stable.  I will try 20.04.  Will upgrading change the way the HDD folders are set up?
Not your /home folders if that's what you mean. Installing from scratch would wipe them. Always remember to backup before proceeding. It would still be a good idea to try Focal out on a LiveUSB first, but you make that call.

---

### Post by KieranFitzgerald on 2020-11-20
Just tried it from LiveUSB.   I meant the subject of the thread, does the procedure oldfred suggests apply to 20.04.

---

### Post by DuckHook on 2020-11-20
The short answer is yes. Many of us use the same file layout.

The long answer is: when installing, you *must* make sure that you are only formatting the partition on which you will be installing the OS. Leave your data partition alone and the data on it won't be touched (back all of it up anyway, just to be safe). You then use oldfred's procedures as per post #2 above.

---

### Post by Impavidus on 2020-11-21
The mountpoint /media/username/partitionlabel is used for partitions mounted by the file manager. If you mount your partition automatically at boot using /etc/fstab, it's better to mount it somewhere else, or confusing things might happen.

---

### Post by KieranFitzgerald on 2020-11-21
[COLOR=#000000]I have upgraded to 20.04 seems ok
ran oldfreds commands up to and including

sudo mount -a
[/COLOR][COLOR=#000000]ln -s /mnt/data/Music
[/COLOR][COLOR=#000000]

I have a folder called Music but it is not accessible see screen shot
Clicking on the file brings up a error saying the file does not exist

How do I create the file Music on the HDD?  I can't see it under files.


[/COLOR]

---

### Post by ajgreeny on 2020-11-21
I am totally confused about where exactly you have got to so far, and I think your problem is a result of your lack of understanding of Linix permissions.
Does that partition with the Music folder on it belong to you as user, and does it mount at boot, ie, is it included in /etc/fstab file?
Please show us the output of ```
cat /etc/fstab
```

The link that I presume you have made is broken which usually means that the disk or partition on which the files/folders to which the link points is not mounted or has the wrong permissions.

I think you need to tell us in detail where the music files actually sit; we can then tell you how to mount that at boot with a line in fstab, how to ensure that you are the owner of that partition, and also what the command is to create a link from the Music folder on that to Music in your home.

---

### Post by oldfred on 2020-11-21
From my mount in /mnt/data, showing directory:

```
fred@z170-focal-k:~$ ll /mnt/data
total 80
drwxrwxrwx 17 fred fred  4096 Oct 19  2019 ./
drwxr-xr-x 14 root root  4096 Nov  4 12:23 ../
drwxrwxrwx 18 fred fred  4096 Dec 31  2015 Music/
```

Then once linked in /home it is seen in /home with l first showing it is linked.

fred@z170-focal-k:~$ ll *Mus*
```
lrwxrwxrwx 1 fred fred 15 Oct 14 19:37 Music -> /mnt/data/Music/
```

Mount in fstab, now since SSD, I use noatime, when HDD I used relatime.
```
[FONT=monospace][COLOR=#000000]# Entry for nvme0n1p5 : [/COLOR]
UUID=1a44f4af-6780-4bbd-ad0b-6385ed30830b /mnt/data ext4 noatime 0 2
[/FONT]
```

---

### Post by KieranFitzgerald on 2020-11-22
Output from 
[COLOR=#000000][FONT=&quot]cat /etc/fstab
[/FONT][/COLOR]
> 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=a143107f-f4be-478f-be5d-c5b45fd5a132 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=22abfa4b-52bd-4796-90bd-20963137b50d none            swap    sw              0       0
UUID=0c12fac5-49c1-443a-abf3-75cc931734d8 /mnt/Data ext4 auto,users,rw,relatime 0 2


---

### Post by ajgreeny on 2020-11-22
Sorry, I forgot to ask also for the output of commands ```
sudo blkid -c /dev/null
``` to check the UUIDs of partitions and then ```
mount | grep /dev
``` to see the mounted partitions status of your currently booted OS.

To check ownership of your data partition let's also see output from ```
ls -l /mnt/data/Music
```
I have a suspicion it may still be owned by root and if so you may need to run ```
sudo chown kieran:kieran /mnt/data/Music
```to make you owner of the partition and thus able to write to it.

---

### Post by oldfred on 2020-11-22
Note that /mnt/Data is not equal to /mnt/data.
Make sure you adjust other commands to use Data, not data.
In Linux case is important, so you have to be consistent on what you capitalize.

---

### Post by KieranFitzgerald on 2020-11-22
sudo blkid -c /dev/null
> 
/dev/sdb1: UUID="0c12fac5-49c1-443a-abf3-75cc931734d8" TYPE="ext4" PARTUUID="cc294478-01"
/dev/sda1: UUID="a143107f-f4be-478f-be5d-c5b45fd5a132" TYPE="ext4" PARTUUID="e1f2d99c-01"
/dev/sda5: UUID="22abfa4b-52bd-4796-90bd-20963137b50d" TYPE="swap" PARTUUID="e1f2d99c-05"


mount | grep /dev
> 
udev on /dev type devtmpfs (rw,nosuid,noexec,relatime,size=4020304k,nr_inodes=1005076,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
mqueue on /dev/mqueue type mqueue (rw,nosuid,nodev,noexec,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
/dev/sdb1 on /mnt/Data type ext4 (rw,nosuid,nodev,noexec,relatime)


ls -l /mnt/Data/Music
> 
ls: cannot access '/mnt/Data/Music': No such file or directory


edit  There is a directory in mnt (Computer) called Data but it's empty!  mnt and Data ownership is root

---

### Post by KieranFitzgerald on 2020-11-22
I just tried this

> 
ls -l /mnt/Data
*   total 16*
[I]   drwx------ 2 root root 16384 Nov 21 13:05 lost+found

[/I]sudo chown kieran:kieran /mnt/Data

ls -l /mnt/Data
  *total 16*
*  drwx------ 2 root root 16384 Nov 21 13:05 lost+found*



Why is the ownership not changing?

---

### Post by The Cog on 2020-11-22
> **KieranFitzgerald said:**
> 
Why is the ownership not changing?
It probably is. You changed the ownership of /mnt/Data, and then listed its contents.
To view the ownershiip of /mnt/Data itself, you need to tell ls to show the directory rather than to show its contents:
```
ls -ld /mnt/Data
```
But there is no Music folder inside /mnt/Data. You will need to create that. You should be abe to now you own the Data folder.

---

### Post by oldfred on 2020-11-22
You just changed ownership of /mnt/Data.
You need recursion to change everything in /mnt/Data.
But recursion can be dangerous, so make sure you are running just on your data partition and not on some system partition.
We have seen users accidentally put a space after / mnt and then it changes everything in / destroying system.
One more reason for good backups.

I sometimes use sudo when I should not and root controls some files. So I occassionly have to run this.
Note my mount is data not your Data.

# so chown & chmod after mounting either manually or via fstab
sudo chown -R $USER:$USER /mnt/data
# The big "X" will also not make files executable unless they were executable to begin with.
sudo chmod -R a+rwX /mnt/data

---

### Post by KieranFitzgerald on 2020-11-22
You are right The Cog i have now created the file.  Thanks to you all.

---

### Post by KieranFitzgerald on 2020-11-23
I have a folder (link) in Home called Music but it is not listed separately in Files like Downloads or Documents etc. which I haven't linked yet.   How do I restore it?

---

### Post by ajgreeny on 2020-11-23
> **KieranFitzgerald said:**
> I have a folder (link) in Home called Music but it is not listed separately in Files like Downloads or Documents etc. which I haven't linked yet.   How do I restore it?
I'm not quite sure what you mean by this but I suspect it means that you have not created a link to the Music folder in that data partition.

Use command ```
ln -s /mnt/data/Music Music
``` to add a link called Music in your home which will look asm if the Music folder is there.
Make certain you remove any file or folder currently in your home named Music and also get the case of /mnt/**data** correct; as oldfred has said data is not the same as Data.

---

### Post by KieranFitzgerald on 2020-11-23
When I open Files from the launch-bar I get a list of folders on the left of the screen .  Since setting up a link to Music in Data (my name)  Music is missing from the list in files, see screen shot, but appears in Home. How do I replace it?

---

### Post by rbmorse on 2020-11-23
If I understand the question correctly, using the file browser naviigate to and open the folder in question.  

At the top of the browser window find the item for Music.  It should have a down arrow symbol.  Click on the arrow to open the options menu, then select "Add to Bookmarks."  fini.

---

### Post by KieranFitzgerald on 2020-11-23
Please look at the sceen-shot the list of files does not include Music, it did before setting up the symlink.  I'm not sure how better describe the problem.

In the screenshot, the file browser is using the "recent" filter (upper left pane), so it's only showing files/directories that meet its criteria. 

Select "home" just below and see if that works better.

Home works fine I just like the Home folders listed below Home, must be possible!

---

### Post by KieranFitzgerald on 2020-11-23
howefield why have you merged my post with someone else's reply.  I'm surprised this can be done.

---

### Post by howefield on 2020-11-23
> **KieranFitzgerald said:**
> howefield why have you merged my post with someone else's reply.  I'm surprised this can be done.

Ah.. an error when tidying your duplicate post. My apologies.

---

### Post by rbmorse on 2020-11-23
> **KieranFitzgerald said:**
> 

Home works fine I just like the Home folders listed below Home, must be possible!

Do what I said above.  Navigate the the folder you want listed in the left pane, click on the down arrow symbol where that folder is listed in the bar at the top of the folder window to open an actions menu. Click on "Add to Bookmarks".  Fini.

---

### Post by KieranFitzgerald on 2020-11-24
Thanks that works.  Can I reorder the result (move Music Up the list) .  Iv'e tried dragging it but no luck.

---

### Post by rbmorse on 2020-11-24
It's possible, but as I recall it gets complicated.  

The left pane in the Nautilus (file browser) window actually consists of several sections.  There are faint horizontal lines that separate them, but depending upon your display and settings may be difficult to see. 

Icons in the top section are placed by the system and require special majicks to manipulate. Icons for bookmarks created by the user are placed in the lower section. These are more pliable and can be reordered by dragging, but only within their section. 

I'm sure someone else can tell you how to reorder icons in the top section...I've forgotten and the procedure has doubtlessly changed since I last tried.  The search function works pretty well here so you might try searching for "20.04 reorder Nautilus bookmarks."

---

### Post by KieranFitzgerald on 2020-11-30
Disappointed with 20.04 frequent lock ups (have to reset).  Printer and scanner detection not working correctly.

---

### Post by ajgreeny on 2020-11-30
It's a long time since I used gnome or nautilus but part of your problem my be the result of setting the view options for nautilus to show bookmarks rather than folders in the left hand pane.

I am making an assumption that there is such a setting for nautilus; I could be wrong because, as I say, I don't use it and haven't used it for a very long time.

Thebookmarks themselves are stored in the ~/.config/gtk-3.0/bookmarks file.
The format is:

file:///path/to/folder Bookmark_name
so the bookmark name can be and often is different from the folder name.  By manually editing this file you can probably change the order of the bookmarks seen in nautilus.

---

