---
title: "Secure Delete/ File Shred"
date: 2007-04-12
forum: General Help
---

### Post by Madmoose on 2007-04-12
Is there an open source secure shredder? One that will clean out the cache of Firefox, and I can use to delete documents.

---

### Post by fritz_monroe on 2007-04-12
There is a little application called [wipe]("http://wipe.sourceforge.net/").  I haven't used it, but looks like it would do the shredding thing.

---

### Post by nadamsieee on 2007-04-21
Try the secure-delete tools: [http://packages.ubuntu.com/feisty/utils/secure-delete](http://packages.ubuntu.com/feisty/utils/secure-delete)

To remove a particular file use the **srm** command:

```
$ srm my_file
```

You can also use **srm** to remove a directory:

```
srm -r my_directory
```

Simply deleting a file (using **rm**) [won't actually remove the file; it will only unlink it from the filesystem]("http://www.hackinglinuxexposed.com/articles/20031214.html"). To wipe clean previously rm'd file, use **sfill**. For example, you might want to clean up the **/tmp** directory:

```
sfill /tmp
```

These commands work best if you have (at a minimum) **/home**, **/tmp**, and **/** on separate partitions. You might want to turn on [mandatory locking]("http://www.mjmwired.net/kernel/Documentation/mandatory.txt") for a particular partition in your **/etc/fstab** file:

```
# note: your fstab file may use UUIDs instead of device names
/dev/hda2 /tmp            ext3    defaults,mand        0       2
```

You can also sort of 'fake' mandatory locking for a particular file:

```
$ chmod g+s,g-x my_filename
```

For more info:

```
$ man srm
$ man sfill
$ man sswap
$ man smem
```

---

### Post by nadamsieee on 2007-04-21
Note that in order to clean the swap space you must first turn it off. First figure out which partition is mounted as the swap partition:

```
$ cat /etc/fstab
```

You should see an entry in **/etc/fstab** associated with swap. **For example purposes**, lets assume **/dev/hda37** is the correct partition. Now turn off the swap:

```
sudo swapoff /dev/hda37
```

Now you can clean the swap partition:

```
sudo sswap /dev/hda37 && sudo swapon /dev/hda37
```

---

### Post by paulieman on 2007-04-21
> **nadamsieee said:**
> Try the secure-delete tools: [http://packages.ubuntu.com/feisty/utils/secure-delete](http://packages.ubuntu.com/feisty/utils/secure-delete)

That looks awesome!  I was looking for something similar, thank you for the link!!

---

### Post by Madmoose on 2007-04-22
Sweet!

Thanks!


Moose.

---

### Post by Dave54 on 2007-04-22
I usually use
```
shred -u [file]
```
to shred files. This overwrites the file 25 times with random data, then deletes it. The -n operator can be used to overwrite more times, and it can hide the shredding. Check the notes though (shred --help) to make sure it'll work on your computer, though.

---

### Post by korvins on 2008-07-18
A graphical interface for that anyone?

---

