---
title: "Slow Operation Lubuntu on USB"
date: 2014-08-06
forum: General Help
---

### Post by 2-wynand on 2014-08-06
I have recently installed Lubuntu onto a USB Flash Disk (aka memory  stick). This I did by unplugging my HDD , connecting the USB drive and  starting from the Lubuntu DVD. Followed the wizard using default  options. This worked, booted from USB no problems. 

BUT .... It's  quite slow. As in clicking through LXDE's menu , and opening a new tab  in FireFox or launching any other program. Now ... you might say that  the USB drive is the culprit. So , how do I get Lubuntu to load more of  itself into memory ? I believe this is what the live CD version does and runs from ram,  but have also read up about it not being a good idea to use it in this  manner ( persistent kernel and such).

So yes ... how do I get it to use more memory (caching) to improve performance for a normal install on a USB stick?

---

### Post by sudodus on 2014-08-06
1. You can use the method of persistent live drive. Start with the iso file and use an overlay file system in a casper-rw file or casper-rw partition. This can be done automatically, when you use the Startup Disk Creator and Unetbootin. See this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

This method uses RAM-disk, but there are limitations.


2. Do what you did, make a full install system to a USB drive, but use a fast USB 3 pendrive alias flash disk alias memory stick. Often the memory hardware is limiting the speed to much lower that what is possible with USB 2. And of course, it will be even faster if the computer has a USB 3 port. See this link

[Link to USB 2 and USB 3 speed tests for installers]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085")

*. Finally, see this link describing the methods and providing more links
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

---

### Post by 2-wynand on 2014-08-06
Ok ... I understand, but is it not possible just to let lubuntu load more of itself into the memory (RAM) cache to compensate for the slow disk access. Using the normal version  / non persisten live drive. (by the way the pendrive can do 30MB/s read and 8MB/s write).

---

### Post by sudodus on 2014-08-06
Well, there are such methods, so if you have enough RAM, you can try according to this thread
[URL="http://ubuntuforums.org/showthread.php?t=1594694"]
Making Ubuntu Fast using RAM (updated and simplified)[/URL]

I have not tried it myself, but browse the thread and find several users who seem to use the method. I think you can also post in the thread and get help from *terminator14*.

-o-

An important question about your pendrive is: "What about reading and writing many small files?"

---

### Post by 2-wynand on 2014-08-06
Thanks. I will try what you have suggested.

Does the question "What about reading and writing many small files?" apply to flash ? Isn't it more of a mechanical HDD problem ?

---

### Post by sudodus on 2014-08-06
See this link [Link to USB 2 and USB 3 speed tests for installers]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085")

It applies to cheap flash memory more than to HDDs. High quality SSDs are fast.

All flash memory wear faster than HDDs, so an installed system in flash and SSD should have the mount option **noatime** in /etc/fstab and you might consider running without swap or only with zRAM (swapping to RAM). Lubuntu live comes with zRAM, but installed Lubuntu does not use zRAM.

---

### Post by oldfred on 2014-08-06
Since flash drive is small you can turn journal off. Recovery may be more difficult but it reduces writes. 
       sudo tune2fs -O ^has_journal /dev/sdb1

 You normally want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.

You also want to change fstab to add noatime so as to not update access times.
      sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

example:
      UUID=41b6b187-be76-4447-b18b-d39cc744b184 /               ext4 [COLOR=#ff0000]   noatime[/COLOR],discard,errors=remount-ro 0       1

Writes will always be slow but that should speed up the reads. But if you have a fair amount of RAM once applications are in RAM it should be reasonably fast.

---

### Post by 2-wynand on 2014-08-06
Thanks for the advice. I will have to read up on how to enable zRAM then.

---

### Post by LubLearner on 2014-08-07
Hi.

I think zRAM must be enabled in your computer, but it might not be used if it has enough RAM since Lubuntu requires very little. You can check if zRAM is enabled easily even without running any shell command. zRAM devices are shown at the Disks utility in the applications menu. Otherwise, run: > cat /proc/swaps

I have seen Lubuntu installed in a couple of computers and there were always zRAM devices. I believe [it started using zRAM by default at Lubuntu 13.10]("http://linuxvillage.org/en/2013/10/next-lubuntu-provided-with-zram-enabled/").

About speeding up Lubuntu without making many changes, could setting some [tmpfs]("https://www.kernel.org/doc/Documentation/filesystems/tmpfs.txt") for caches (navigator, more frequent programs...) help? And, is creating another tmpfs for /tmp folder safe (You could create a symbolic link in order to set it in an easy way)? Those actions are supposed to reduce the usage of the USB and extend its life time. tmpfs stands for Temporary File System which allows to use RAM as another disk one can mount in any folder. I am aware last statement is not technically exact. 

Having at least 2 GiB of RAM is probably necessary to do those and the applications menu will remain slow, but you can reduce its use by creating icons for the most frequent programs in the applications bar, where the default icon for the file manager is. I think there is not a maximum limit of icons.


Anyway, running Lubuntu from RAM seems a extremely more powerful solution.

---

### Post by 2-wynand on 2014-08-08
Ok , so what I have done is to use noatime and zRAM. I see what has been said about tmpfs and setting some apps to use a RAM dive for cache , which would be good if I can do this for FireFox for example. How would I go about doing this ? 

Also what other caching / things that access the disk (flash in this case) alot can I set to rather use ram or disable ? I have installed using ext2 which doesn't do journaling.

---

### Post by oldfred on 2014-08-08
I have seen that it is better to use ext4 and turn journal off than to use ext2, but do not know details.

This post has an example of mounting a tmp in fstab, thread is on SSD, but some of same things apply.
[http://ubuntuforums.org/showthread.php?t=2003022&p=12029006#post12029006](http://ubuntuforums.org/showthread.php?t=2003022&p=12029006#post12029006)

---

### Post by LubLearner on 2014-08-13
Hi.

I have taken a look to that thread. There, an user said that person had moved the Mozilla Firefox cache onto /tmp, but I would rather create two tmpfs: one for /tmp and another for the cache of Firefox. I think it has not disadvantages since the tmpfs only take up the space which their files fill. And you can control the permissions better.

I mean, one can create a tmpfs for the cache of Firefox whose owner is the standard user instead of the root and restrict the permissions. For instance, if you only had one user and wanted to mount the tmpfs onto a hidden folder, which must be create earlier, in its home for the cache of Firefox whose default maximum weight is 350 MiB, you might open the /etc/fstab with leafpad as root and write:

```
tmpfs /home/user/.anchor_folder tmpfs defaults,size=352m,mode=0770,uid=1000,gid=1000 0 0
```

I do not know if choosing just a size of 350 MiB  is a good idea or might cause problems, so I wrote a few MiB more.

If you want to know an user's id and group id, you can run: ```
id user's_name
```

"mode=0770" set xrw permissions for the owner and group which is written at the gid option. If you wanted to limit the permission even more, you could try mode=0700 and could check if Firefox can use that folder as cache by entering about:cache.

You may also include noatime among the options if you consider it better. I do not know if it improves the performance safely.
> noatime 
                 Do not update inode access times on this filesystem  (e.g.,  for faster access on the news spool to speed up news servers).

In order to tell Firefox to use a folder as cache you have to follow this [KB]("http://kb.mozillazine.org/Browser.cache.disk.parent_directory") of MozillaZine.


In the thread which oldfred has linked, there is a [post]("http://ubuntuforums.org/showthread.php?t=2003022&p=12030232#post12030232") with several folders which one could move onto a tmpfs and how to write the lines in /etc/fstab, more or less. However, I had read /var/tmp may contain files needed after a reboot so as to complete updates. You'd better look for more information.


And remember to run ```
sudo mount -a
``` after saving the /etc/fstab file to ensure you have not written any mistakes which would prevent Linux from starting.

---

