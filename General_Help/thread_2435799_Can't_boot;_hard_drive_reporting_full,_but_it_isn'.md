---
title: "Can't boot; hard drive reporting full, but it isn't"
date: 2020-01-26
forum: General Help
---

### Post by Bearly Able on 2020-01-26
Using Ubuntu 19.04.  Got a message last night saying my 2TB hard drive is full and recommending I empty the rubbish bin to create space.  I did that, although I couldn't see how the drive could even be close to full.  Today, I've been unable to boot Ubuntu, and it's still reporting that the disc is 100% used.  However, running the Disk Usage Analyser from a "live" USB stick shows less than 250GB used, which is in line with what I would expect.

I tried booting in recovery mode.  Clean only found one removable item, freeing just 2MB, fix broken packages said there wasn't enough space to do so (112MB required), fsck failed to run, and system-summary says the drive is full.  If it is, there's an awful lot of ... something ... which I can't find.

I have no idea where to go from here, and should be most grateful for any assistance.

**Edit:**
I don't know what this means, but if I right-click on my home directory and check properties, it's in line with what the Disk Usage Analyser shows.  However, when I tried to copy that directory, the progress bar showed "preparing to copy X files" and the combined size shot up past 1TB before I aborted.

---

### Post by dragonfly41 on 2020-01-26
This is just a hunch but I vaguely remember that inodes need to be looked at.

[https://stackoverflow.com/questions/653096/how-to-free-inode-usage](https://stackoverflow.com/questions/653096/how-to-free-inode-usage)

---

### Post by Bearly Able on 2020-01-26
Thanks.  I'll look into that further, as I confess I didn't entirely understand it at first read.

However, it doesn't seem to explain why there is such a huge variation in reported disc usage.  Most of the disc usage I'm aware of is photographs, and I haven't uploaded any recently.  I hadn't done anything which would explain a sudden report of disc full yesterday.  I don't have large numbers of old kernels, and "clean" failed to find much to remove.  I emptied the rubbish bin last night, which did contain a substantial number of large files, but the disc is still reporting full.

---

### Post by TheFu on 2020-01-26
Troubleshooting.  Please post:```

df -hT
df -i
```
using code tags, as shown.  Without code tags, the output is too hard to read, so please take the effort to get that done.

Also, in the output, we don't need to see anything with tempfs or related to snaps. Please edit those lines out to keep the cruft to a minimal.

---

### Post by Bearly Able on 2020-01-26
```

ubuntu@ubuntu:~$ df -hT
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  7.8G     0  7.8G   0% /dev
/dev/sdd       iso9660   1.9G  1.9G     0 100% /cdrom
/dev/loop0     squashfs  1.8G  1.8G     0 100% /rofs
/cow           overlay   7.8G  524M  7.3G   7% /
/dev/sdc1      fuseblk   1.9T  531G  1.4T  29% /media/ubuntu/HD-PCFU3
/dev/sdb4      ext4      1.7T  1.7T     0 100% /media/ubuntu/50bc67b0-7e13-4c81-a34e-a553b85c0419

```

```

ubuntu@ubuntu:~$ df -i
Filesystem         Inodes   IUsed      IFree IUse% Mounted on
udev              2031011     620    2030391    1% /dev
/dev/sdd                0       0          0     - /cdrom
/dev/loop0         156349  156349          0  100% /rofs
/cow              2036624    4302    2032322    1% /
/dev/sdc1      1398629040 1417614 1397211426    1% /media/ubuntu/HD-PCFU3
/dev/sdb4       109895680 2170154  107725526    2% /media/ubuntu/50bc67b0-7e13-4c81-a34e-a553b85c0419

```

Hopefully I've got that right and removed the right bits.

---

### Post by deadflowr on 2020-01-26
> **Bearly Able said:**
> Sorry, but I don't know how to run those commands on the relevant hard drive.  I'm currently using a live USB version of Ubuntu as the machine won't boot.

The commands will output info for all mounted partitions.
So as long as the partitions with problems are mounted they'll be seen by the commands.
You might also want to double check the funky system's fstab file to make sure that no other mount points exist like /boot.

---

### Post by TheFu on 2020-01-26
> **Bearly Able said:**
> Sorry, but I don't know how to run those commands on the relevant hard drive.  I'm currently using a live USB version of Ubuntu as the machine won't boot.

Ah - you said that. Sorry I missed it.

In the live environment, you'll need to get all the partitions mounted. Probably the easiest way is by opening a file manager and clicking on each partition.  Then open a terminal and run those commands.

Show both commands and the relevant output for each.  "code tags" can be selected on the Advanced editor here - '#' button.  Or use the normal 'quote' button on the default editor, just manually replace QUOTE ---> code at the beginning and end of the block.

---

### Post by Bearly Able on 2020-01-26
Sorry - I finally worked it out and edited my last post, as folk were replying, thus screwing up the order of the thread.  My apologies

---

### Post by TheFu on 2020-01-26
```
/dev/sdb4      ext4      1.7T  1.7T     0 100% /media/ubuntu/50bc67b0-7e13-4c81-a34e-a553b85c0419
```

is clearly full and it is just 1 partition. If that is where the OS is located, you are learning a valuable lesson.  There's a reason experienced Unix admins limit the OS to be just 25GB in size - that is so when a bonehead user fills their /home/ partition, the OS still works and keeps going.

So - you'll want to delete about 2GB of files on that partition, then boot into the OS and prevent whatever might be filling it (stop bittorrent immediately!) from running.  Then you should consider fixing the disk layout and not being lazy. from now on.  ;)
Here's my layout on a desktop: [https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277](https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277)

**inodes - off topic:**
You do have plenty of inodes, BTW.  in general, inodes don't become an issue on partitions with 10GB or more storage, but we always need to check.  On partitions with less than 10G, inodes frequently run out because the default inodes reserved is based on the total storage amount.  I've been burned a few times on web servers with little data, but 500K web-server script files.  At the time of file system creation, it is possible to manually configure the number of inodes reserved.  For tiny, minimal-storage, servers, I'll reserve 1000x more than the default.
If you want to learn a little more about inodes, there is a wikipedia article.  It is worth knowing just a little more.

---

### Post by Impavidus on 2020-01-26
A separate issue, you write that you use Ubuntu 19.04. That reached end of life a few days ago.

---

### Post by Bearly Able on 2020-01-26
> **TheFu said:**
> 
So - you'll want to delete about 2GB of files on that partition, then boot into the OS and prevent whatever might be filling it (stop bittorrent immediately!) from running. 

Well, that's my problem.  I don't know what's filling it.  I can't find any obvious culprit and don't know where to look.  Running the Disk Usage Analyser is showing me pretty much what I expect to be there and nothing unusual.  I don't have bittorrent running and have not run it in the last six months, IIRC; I've never downloaded videos, music ...  

[https://imgur.com/A8ZPxoo](https://imgur.com/A8ZPxoo)

> **TheFu said:**
>  Then you should consider fixing the disk layout and not being lazy. from now on.  ;)
For the record, that's the default Ubuntu installation.  I assumed it knew better than I did and didn't try to meddle with it.  I will look into it, though.

---

### Post by TheFu on 2020-01-26
It also looks like 
```
/dev/sdc1      **fuseblk**   1.9T  531G  1.4T  29% /media/ubuntu/HD-PCFU3
```
isn't using a native Linux file system, so you can only put straight, simple, data onto it. It can't be used for /home/ or any critical Linux settings or programs.

---

### Post by Bearly Able on 2020-01-26
That's an external hard drive used for backups. It has always worked OK, and curiously is not showing signs of filling up, which I would have expected if my home directory were the source of the huge increase in files.

---

### Post by oldfred on 2020-01-26
have you housecleaned trash?
And then check logs, some systems get runaway logs if some setting is not correct.

RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:

Over 365 days
find ~/.cache/ -depth -type f -atime +365 
Delete all old cache entries
find ~/.cache/ -type f -atime +365 -delete

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB

cd / or cd /home, then drill down to folder that is large, or too large
sudo du -hc --max-depth=1
Shows just /
sudo du -hx --max-depth=1 / 2> /dev/null

---

### Post by TheFu on 2020-01-26
For large files, 
```
 sudo find / -type f  -size +1G # files larger than 1GB
```
No need to match on a name, but we don't want directories.

I had to do this earlier today after seeing a backup with 3.6G of stuff which made no sense to me.  Backups are normally under 50MB daily.  Turned out to be 2 flatpak package installs yesterday - each included a full gnome or KDE platform!  The programs to be installed were about 30MB each, but all the "packaging" cruft that came along was 900MB+.

---

### Post by TheFu on 2020-01-26
> **Bearly Able said:**
> That's an external hard drive used for backups. It has always worked OK, and curiously is not showing signs of filling up, which I would have expected if my home directory were the source of the huge increase in files.

Please test a restore, since it is almost 100% certain that critical metadata about the files will be lost going to a non-Linux file system like that.  I hope the restore actually works, but doubt it will.  Don't get burned when you really need it.

---

### Post by Bearly Able on 2020-01-26
> **TheFu said:**
> For large files, 
```
 sudo find / -type f  -size +1G # files larger than 1GB
```
No need to match on a name, but we don't want directories.


Thank you - that's located the issue.  There are still files in .Trash, even though I'd emptied the rubbish bin.  I don't know why they weren't deleted, and I don't know how to delete them now; using the "delete" key has no effect, and neither does "move to trash", which I'd expected to give me a "delete permanently" option.

As to the backups, yes, they work.  I've restored from them on more than one occasion.  I am surprised the file system is non-Linux, as I thought I'd formatted the disc, but I guess I must be getting mixed up with another external drive I have.  Another thing to sort out ...

---

### Post by yancek on 2020-01-26
Move to Trash does not delete anything but simply moves the files/folders to the Trash directory as expected.  Generally, a single left click on a file/folder to highlight it and then simultaneously holding down the shift/delete key is the method I use and can be used for multiple files/folder. You could do this with all the files in the Trash directory if you want to delete them all.  Also many commands you can use from a terminal to remove multiple files/folders.

---

### Post by Bearly Able on 2020-01-27
> **yancek said:**
>  simultaneously holding down the shift/delete key is the method I use
Thank you - that was what I'd forgotten.

I managed to remove the files successfully, but I'm puzzled as to why they were never deleted when I emptied the rubbish bin.  They were quite old, and I've certainly emptied the bin several times since then.  (Note to self: in future, check that it really *is* empty.)  Other files were removed successfully, but not the old backups.

Unfortunately, I still can't boot into Ubuntu, despite my hard drive now reporting 22% used instead of 100% used.  I think my best bet at this stage might be to do a fresh install of 19.10, given that I need to upgrade anyway.

---

