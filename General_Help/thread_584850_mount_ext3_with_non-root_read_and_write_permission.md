---
title: "mount ext3 with non-root read and write permission?"
date: 2007-10-21
forum: General Help
---

### Post by gregconquest on 2007-10-21
I'm so frustrated in trying to find information on how to mount files. There are guides, and there are examples, but I can't find an understandable, comprehensive guide with examples, specifically on ext... All the questions and answers are on how to mount fat and ntfs partitions...

My question:

How do I mount an ext3 partition to enable read and write permission by:
- me (not from root)
- any applications (for example Thunderbird for its profile, and konqueror not launched from root?)

I want to assign the above read/write permissions to several ext3 data drives via fstab. For the other linux home partitions, writing only while root is fine, but for the data partitions, I want it to be as easy as is feasible.

This is what I have now:
```
LABEL=DATA3      /mnt/DATA3 ext3    rw,user        0       2
```
Can I do this without using chmod or chown? fstab alone can mount it as I wish? My impression is that chmod and chown only set the permissions for this session. fstab sets them for all boots.

Note: I have ubuntu and kubuntu on this machine now. I just deleted WindowsXP because it had problems. I also removed openSUSE because 10.3 could not install grub correctly. Boy, do I feel clean now :rolleyes: I have several partitions just waiting for other OS's. All my documents are in common partitions.

Thanks for the mount command and/or the fstab entry
                          or
Thanks to a guide that does answer my questions.

Thanks,
Greg Conquest

---

### Post by weijie90 on 2007-10-21
Nope, just chmod 777 /mount/point

---

### Post by gregconquest on 2007-10-21
> **weijie90 said:**
> Nope, just chmod 777 /mount/point

The permissions set from chmod will persist? I enter this one time today, and those partitions maintain the same permissions even after reboots?

And I guess I would need to issue the same command from each OS?

Greg

---

### Post by weijie90 on 2007-10-21
Yes to both questions.

Assuming that "each OS" is a *nix box.

---

### Post by PmDematagoda on 2007-10-21
No, you need to use chown for the partitions:-

```
sudo chown username:usergroup /mount/point
```

---

### Post by weijie90 on 2007-10-21
> **PmDematagoda said:**
> No, you need to use chown for the partitions:-

```
sudo chown username:usergroup /mount/point
```

Meh. What's the difference in the result?

---

### Post by PmDematagoda on 2007-10-21
Give chmod a try and see what you get, it won't damage the system but it certainly would be a failure .

---

### Post by weijie90 on 2007-10-21
I did a chmod 777 /media/disk to get my USB hard drive accessible yesterday. it works perfectly.

---

### Post by PmDematagoda on 2007-10-21
Really? Maybe I am wrong, but chmod did not work when I tried to make a partition read/write, so I had to use chown.

---

### Post by gregconquest on 2007-10-21
weijie,

So, for:
```
chmod 777 /mount/point
```
"777" means anyone can execute files as well. I only have data on these drives, but sometimes applications access this data (like Thunderbird reading and writing to the profile.) This does not count as executing? If not, would "666" be just as useful?

And if I execute:
```
chmod 666 /mnt/DATA3
```
will all files ***and subfolders*** on the ext3 partition mounted at /mnt/DATA3 be read and write for all users?

Thanks,
Greg

---

### Post by weijie90 on 2007-10-21
Ah! Yes, I forgot about executables. Sorry.

Chown-ing the mount point will work if I'm not wrong.

Use this interactive chmod numberic code generator if you want to learn about file permissions: [http://catcode.com/teachmod/numeric2.html](http://catcode.com/teachmod/numeric2.html)

---

### Post by gregconquest on 2007-10-21
OK. Thanks weijie90. I will try this. It is late here in Japan, so I'll follow up here tomorrow.

Thanks again.
Greg

---

### Post by weijie90 on 2007-10-21
No problem. Nice name you have there btw.

---

### Post by eph1973 on 2007-10-21
Could you be a bit more specific about what sort of drives you are referring to?  Are you talking about USB flash drives?  External USB drives?  Internal drives that are always available to you?  Are you trying to plug them in/remove them while the OS is running so that you can mount/umount them?  Or are they always installed?  Have you tried reading [this page]("http://ubuntuforums.org/showthread.php?t=168221"), which discusses udev rules, which, if you are using a flash drive, you may find interesting.  See post #11 on that link to see a discussion about gnome-volume-manager.  Have you read man mount?  It has a discussion of what the various options mean for your /etc/fstab entry.

Be careful with chown and chmod.  If you are looking to make directories accessible by anyone, the best way to do it would be
```
sudo chmod a+X -R /mnt/DATA3
```The above command would only change the permissions of the directory and all subdirectories of the mount point to be accessible by anyone.  That will not change the mode of the files in any way, so you don't go making everything on the whole drive an executable file with something like sudo chmod 777 -R (directory), which could be bad.

You could also chown the directories and subdirectories with a command such as:
```
sudo chown (your_user_name):(your_user_name) -R /mnt/DATA3
```This command will chown the mount point and all files and subdirectories under it to your user name and group (the colon and the second (your_user_name) is optional).

See also man chown and man chmod for more details.

---

