---
title: "need permissions or fstab help with external HD data partition"
date: 2017-08-07
forum: General Help
---

### Post by sonicwind on 2017-08-07
I recently set my mom up with Ubuntu 16.04 LTS, running off an external hard drive. The same drive was set up with two data partitions with mount points -- /MMUbuntuData (ext4) and /MMNTFSData (ntfs).

After install, I couldn't create new folders or files on either data partition.

I was able to correct the NTFS partition by relocating the mount point (using Disks) from /MMNTFSData to /media/MMNTFSData. The fstab settings stayed the same but the permissions changed from

```
drwxrwx--- 1 root plugdev
```

to

```
drwxrwxr-x 2 root root
```

and now it works. I don't understand why it works now because the write permission for Others is still - (null). Also, why did the switch to /media make a difference?

Changing the mount point **didn't** fix the ext4 data partition. The fstab settings are the same before and after but the permissions changed from

```
drwxr-xr-x 3 root root
```

to

```
drwxrwxr-x 2 root root
```

What do I need to do to fix this ext4 partition so it can be used? I'm familiar with the basics of fstab and permissions, but I'm not sure of the right way to fix this. Should I do **chmod 777 /media/MMUbuntuData** ? I've never used chmod.

Thank you so much.

---

### Post by #&amp;thj^% on 2017-08-07
You need to seriously think about giving 777 to all files and folders under whatever directory or disk, which means all your files and directories will be readable, writable and executable by whole world

Summary: 775 changes the permissions mode of a file or directory so that the owner and group has full read/write/(execute or search) access and all others have read and execute/search access. The concept of owner/group/everyone else is fundamental to unix-based files and permissions are part of this approach to basic file security.

Each number refers to the total bits of the separate parts of owner/group/other that you can have, from 0–7.

```
0 is no read/write/execute or search access

1 is execute/search

2 is write

3 is write/execute or search

4 is read

5 is read/execute or search

6 is read/write

7 is read/write/execute or search
	

```
For drwxrwxr-x it's:

```
chmod 775  the_path_to_target
```

For drwxr-xr-x it's:

```
chmod 755  the_path_to_target
```
Unless I missed something here?

---

### Post by sonicwind on 2017-08-07
Thanks 1fallen for replying.

As shown above in my post, the permissions line shows the folder/drive is owned by root. Right? So I thought that meant **I** would be the Other group. That's where I thought 777 would be needed. I thought I as the user was that last **-** listed here for the write permission for Other.:

```
drwxrwxr-x 2 root root
```

Am I wrong on that? I also didn't realize that would give all files and folders under that directory or disk those permissions.

I thought each of them would have their own permissions?

---

### Post by #&amp;thj^% on 2017-08-07
> **sonicwind said:**
> Thanks 1fallen for replying.

As shown above in my post, the permissions line shows the folder/drive is owned by root. Right? So I thought that meant **I** would be the Other group. That's where I thought 777 would be needed. I thought I as the user was that last **-** listed here for the write permission for Other.:

```
drwxrwxr-x 2 root root
```

Am I wrong on that? I also didn't realize that would give all files and folders under that directory or disk those permissions.

I thought each of them would have their own permissions?

The way I've always known it to be is the /home folder and all user account folders within it have a default permission of 755

755 for the home folder, except for** .dmrc**, which needs to be 644.

So:
```
chmod -R 755 /home/username
chmod 644 /home/username/.dmrc
```

Should sort out all your problems.

This is worth a look:
[http://www.linuxquestions.org/questions/ubuntu-63/permission-denied-as-root-to-a-root-owned-directory-4175464679/](http://www.linuxquestions.org/questions/ubuntu-63/permission-denied-as-root-to-a-root-owned-directory-4175464679/)

And one Identical to mine:[https://askubuntu.com/questions/409076/permission-drwxrwxr-x](https://askubuntu.com/questions/409076/permission-drwxrwxr-x)
And if I'm wrong I hope someone else chimes in soon. (FTR I'm no guru on this matter but this has worked for me in the past):D
You could wait for others to input if I'm up the creek or not. ;)

---

### Post by sonicwind on 2017-08-07
I'm really confused now. My partition isn't in /home. It's in /media. I'm not sure we're on the same page. Giving 755 to my partition (owned by root) wouldn't allow me to write to it I don't think. Which is the problem.

---

### Post by #&amp;thj^% on 2017-08-07
Those are just examples use your correct path. :)

---

### Post by #&amp;thj^% on 2017-08-08
I'm not trying to confuse you even more but here is how mine reads.(_I just had to verify my information given was accurate_)
File permissions and attributes: and octal file permissions from command line.
In checking mine for permissions with octal values:
Note just the difference for a folder inside of my /home
```
stat -c "%a %n" /Documents
644 /Documents
```

Now the difference with system directory's
```
me on Tue Aug 08 at 07:10 AM in /boot  
>> stat -c "%a %n" /boot
755 /boot

```

```
me on Tue Aug 08 at 07:11 AM in /boot  
>> stat -c "%a %n" /home
755 /home

```
Now here is "root"
```
me on Tue Aug 08 at 07:13 AM in /boot  
>> stat -c "%a %n" /root
700 /root
```


```
me on Tue Aug 08 at 07:13 AM in /boot  
>> stat -c "%a %n" /mnt
755 /mnt

```

```
me on Tue Aug 08 at 07:15 AM in /boot  
>> stat -c "%a %n" /proc
555 /proc

```

```
me on Tue Aug 08 at 07:15 AM in /boot  
>> stat -c "%a %n" /sys
555 /sys

```

```
me on Tue Aug 08 at 07:16 AM in /boot  
>> stat -c "%a %n" /run
755 /run

```

```
me on Tue Aug 08 at 07:16 AM in /boot  
>> stat -c "%a %n" /var
755 /var

```

```
me on Tue Aug 08 at 07:16 AM in /boot  
>> stat -c "%a %n" /usr
755 /usr
```


```
me on Tue Aug 08 at 07:16 AM in /boot  
>> stat -c "%a %n" /etc
755 /etc
```

Now this is just one file inside of home I found different and told you about.
```
stat .dmrc
  File: .dmrc
  Size: 43        	Blocks: 8          IO Block: 4096   regular file
Device: 801h/2049d	Inode: 18087949    Links: 1
Access: (0644/-rw-r--r--)  Uid: ( 1001/      me)   Gid: ( 1001/      me)
Access: 2017-08-06 16:02:02.994976870 -0600
Modify: 2017-08-06 16:02:02.994976870 -0600
Change: 2017-08-06 16:02:03.038310201 -0600
 Birth: -
```
Or just for the value:
```
stat -c "%a %n" .dmrc
644 .dmrc
```

And root with a little more information:
```
stat /root
  File: /root
  Size: 4096      	Blocks: 8          IO Block: 4096   directory
Device: 801h/2049d	Inode: 20054017    Links: 8
Access: (0700/drwx------)  Uid: ( 1001/      me)   Gid: ( 1001/      me)
Access: 2017-06-19 12:18:01.605805235 -0600
Modify: 2017-07-02 18:50:12.568007669 -0600
Change: 2017-07-02 18:50:12.568007669 -0600
 Birth: -
```
So long story short here I found** NO "777"** octal values/permissions on a sound system.
Anyway you can read here, if you have not already: [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)
And Good Luck :)
EDIT: This not a suggestion/for solution for the OP but Information only for permissions

---

### Post by sonicwind on 2017-08-08
As my original post showed, I've already tried both 755 and 775 and neither worked in various configurations. I think something else is holding this up.

For kicks, today I removed that partition from fstab using Disks by setting Automatic Mount Options to ON. This handed the duties of mounting the partition to udisks2. But it didn't make any difference in being able to write to the partition.

At this point, I think I might just create a new thread in hopes of getting fresh help. Nobody is going to read all this to get to the bottom.

I do appreciate your help, 1fallen. Thank you. If anyone else reads this and has any ideas, please help.

---

### Post by Dennis N on 2017-08-08
For ext4 formatted data partition (no OS on it), I change the owner and group of the partition to my user. Changing permissions is not necessary, since when you are the owner, you have all the permissions needed for full access.

if your user name is peter, and the partiton is mounted at /mnt/data:

```
sudo chown -R peter:peter /mnt/data
```

---

### Post by oldfred on 2017-08-08
This is what I do, from this thread. Note correction by Mobius1 of my use of Octal.

 sudo mkdir /mnt/data
# ( permissions stay with the partition not with the mountpoint ).
# so chown & chmod after mounting either manually or via fstab
sudo chown $USER:$USER /mnt/data
# The big "X" will also not make files executable unless they were executable to begin with.
sudo chmod -R a+rwX /mnt/data
#Edit fstab with your UUID:
sudo blkid -o list
sudo cp /etc/fstab /etc/fstab.backup
sudo nano /etc/fstab 


 Seems like a better way as you have more control over what is executable. See post #8 & 10 by morbius1.
[http://ubuntuforums.org/showthread.php?t=1795369](http://ubuntuforums.org/showthread.php?t=1795369) 

 First, Octal chmods aways have to have odd values so that directories have the execute bit enabled.
But you don't want to do a "chmod -R 555 / path" either since that makes every file within it executable as well. It's best not to do a recursive chmod in octal at all but that's another discussion.

---

### Post by oldos2er on 2017-08-08
> **sonicwind said:**
> At this point, I think I might just create a new thread in hopes of getting fresh help.

Please don't do that; we frown on duplicates as indicated by the Code of Conduct:

**"Thread Closing:** Staff are not required to do so, but are  requested to post an explanation in a thread that is closed when time  permits. This is a non-exhaustive list of reasons a thread may be  closed, but will give the general idea:

...The thread topic is a duplicate of another current and active thread." 

> **sonicwind said:**
>  Nobody is going to read all this to get to the bottom.

I think you are underestimating the patience of our very helpful members.

---

### Post by sonicwind on 2017-08-08
Thank you Dennis and oldfred for responding. I've learned so much from both of you while reading this forum.

I'm going to wait until my brain is fresh in the morning and give this a try. It makes sense.

I will let you know how it goes.

oldos2er: Point taken! Thanks.

---

### Post by sonicwind on 2017-08-09
It worked guys! I moved the mount point back to /media/MMUbuntuData and from there chown did the trick.

Thank you 1fallen, Dennis N, oldfred and oldos2er for your help. I will mark this thread solved.

---

