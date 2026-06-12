---
title: "Just need to verify relocating my /home directory"
date: 2013-02-19
forum: General Help
---

### Post by xeddog on 2013-02-19
I just had a hard disk crash and so I just had to do a fresh install of Ubuntu 12.04 on a new disk.  I already have a second disk in the machine that was used as my /home directory for the old system, so it think I just need to open a terminal and as root:
```
mv /home /home-old
mount -t ext3 /dev/sdb1 /home
```

Then add to fstab
```
/dev/sdb1       /home           ext3    defaults,errors=remount-ro 0    1
```

Does that sound about right?  I just need to make sure that I don't screw up that file system because it has some un-backed-up goodies I was working on.

Thanks,

Xeddog

---

### Post by papibe on 2013-02-19
Hi xeddog.

Moving home it is not necessary.

Just updating fstab would get you there. However referencing the disk by device name can create problems in the future.

Use UUID instead. For example:
```
$ sudo blkid 
... 
/dev/sda2: UUID="46a24626-359c-4307-ad03-5f0716c837a1" TYPE="ext3"
... 

```
Then your fstab entry should look something like:
```
UUID=46a24626-359c-4307-ad03-5f0716c837a1  /home  ext3  defaults,errors=remount-ro 0    1
```
Then restart (remember to use your own UUID).

See [here]("https://help.ubuntu.com/community/Partitioning/Home/Moving") for more details.

Let us know how it goes.
Regards.

---

### Post by xeddog on 2013-02-20
> **papibe said:**
> Hi xeddog.

Moving home it is not necessary.

Just updating fstab would get you there. However referencing the disk by device name can create problems in the future.

Use UUID instead. For example:
```
$ sudo blkid 
... 
/dev/sda2: UUID="46a24626-359c-4307-ad03-5f0716c837a1" TYPE="ext3"
... 

```
Then your fstab entry should look something like:
```
UUID=46a24626-359c-4307-ad03-5f0716c837a1  /home  ext3  defaults,errors=remount-ro 0    1
```
Then restart (remember to use your own UUID).

See [here]("https://help.ubuntu.com/community/Partitioning/Home/Moving") for more details.

Let us know how it goes.
Regards.

Thanks papibe - 

The purpose of the move is so I can go back and delete the old home directory once I get the new one established.  I don't think I could delete it otherwise.  

After I posted I did think that using the device name might not be a good idea.  If I were to throw an additional drive into my machine I could potentially lose my home directory.  So I had decided to use the uuid.

But I do have one more thing I would like to clear up which is probably not a big deal since this is a single user machine.  The directory structure on the new home drive is not /home/userid, but just /userid.  /home itself is still on the boot drive.  So the initial move command to rename the existing home would be "mv /home/userid /home/userid-old" for example.   Then "mount -t ext3 UUID=blahblahblah /home/userid", and the fstab entry would also reference /home/userid as well.  Right???
 
Thank you again,

X

---

### Post by papibe on 2013-02-20
> **xeddog said:**
> The purpose of the move is so I can go back and delete the old home directory once I get the new one established.  I don't think I could delete it otherwise.
You won't, but you are not going to be able to move home while you are logged. Boot into recovery mode, make sure you can remove things from the root partition by running:
```
mount -o rw,remount /
```
Double check that /home is your old home and no the new one:
```
ls /home
```
And then you can remove home:
```
rm -rf /home
```
That would let you without a proper mount point though, so you need to create one:
```
mkdir /home
chmod 755 /home
```

> **xeddog said:**
> The directory structure on the new home drive is not /home/userid, but just /userid.  /home itself is still on the boot drive.  ...
Then "mount -t ext3 UUID=blahblahblah /home/userid", and the fstab entry would also reference /home/userid as well.
Not exactly.

The mount itself would create the correct tree structure. Just mount the disk on /home (not /home/userid).

You can test how mount works by doing some "mounting-around":
```
sudo mkdir /media/myfuturehome
sudo mount -t ext3 /dev/sdb1 /media/myfuturehome
```
Then you can see what's there:
```
cd /media/myfuturehome
ls
```
Does that helps?

Let us know how it goes.
Regards.

---

### Post by xeddog on 2013-02-20
Got it.  My references to mounting on /home/userid were not correct.  Worked like a champ when I used /home.  It's nice that I got a lot of my apps and other customizations back.  Whew!

Thank you,

X

---

