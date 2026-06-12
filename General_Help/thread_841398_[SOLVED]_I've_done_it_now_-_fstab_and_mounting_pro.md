---
title: "[SOLVED] I've done it now - fstab and mounting problems"
date: 2008-06-26
forum: General Help
---

### Post by rdingram on 2008-06-26
So I have been trying to figure out a way to mount my second ext2 partition that I have created in xubuntu as my home directory. So I read a post about adding the partition to my fstab and then running

```
sudo mount -a
```

My problem is that I did this before copying my existing files in my home directory onto the new partition before mounting it. So... I have lost my old home directory files. I tried to unmount the partition but it can't because umount reports the device as busy obviously.

Here is my fstab.

```

proc /proc proc defaults 0 0
# Entry for /dev/sda2 :
UUID=27755706-6b6c-47f0-affa-c6dc6c3b5817 / ext2 relatime,errors=remount-ro 0 1
# Entry for /dev/sda3 :
UUID=d9d0af67-4e19-48bd-b106-912b0abe57fe none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
# UUID=5fe63f30-16d6-44d9-a85a-43623df0eb50 /home/david ext2 relatime 0 2

```

Here is blkid.
```

/dev/sda1: UUID="5fe63f30-16d6-44d9-a85a-43623df0eb50" TYPE="ext2" 
/dev/sda2: UUID="27755706-6b6c-47f0-affa-c6dc6c3b5817" TYPE="ext2" 
/dev/sda3: TYPE="swap" UUID="d9d0af67-4e19-48bd-b106-912b0abe57fe"

```

Here is what happens when I...
```

~$ umount -f /dev/sda1
umount2: Device or resource busy
umount: /home/david: device is busy
umount2: Device or resource busy
umount: /home/david: device is busy

```

I am lost on a way to get the old contents of my home directory. I am getting all kinds of errors because of missing config files, so any help would be appreciated.

Thanks!

---

### Post by drs305 on 2008-06-26
Were you using "sudo umount -a" to unmount the partitions?

In any case, if your files are still in your original home partition and you can't access them because you changed the fstab, you can simply change fstab back to the way it was. 

If you haven't deleted or moved the files or changed the original partitions, things should resort to the way they were. You have the /home line commented out. Was that your original  /home listing (or is that the new "unsuccessful" partition)?

Once you have made the changes back to the originals you will have to reboot to make them effective.

---

### Post by rdingram on 2008-06-26
Thank you for the reply.

I was using 'sudo mount -a' to mount the partitions after altering fstab. When I realized that the new fstab configuration didn't work properly I decided to comment out the /dev/sda1 line in fstab and try the 'sudo mount -a' again to no avail.

If I am hearing you correctly then all I have to do now that the new partition is commented out of my fstab I can reboot to my previous configuration?

---

### Post by drs305 on 2008-06-26
> **rdingram said:**
> If I am hearing you correctly then all I have to do now that the new partition is commented out of my fstab I can reboot to my previous configuration?

Was the last line (commented out) in your fstab the new home partition?
I can't see a line for /dev/sda1 in your fstab, what was that? 

If: 
You made a new home partition
Edited your fstab to include a new home on a new partition
Did not move or delete your original /home data
and then had problems during boot ... 

The answer to your question is yes. You can simply comment out the new fstab /home reference and when you reboot it will mount things the way they were originally (with /home part of the / partition and not mentioned individually).

You have to reboot because ubuntu is not going to allow you to unmount either your root or home partitions, wherever they are.

---

### Post by rdingram on 2008-06-26
I have rebooted now with my changes commented out of fstab and all is restored to normal. I am now going to copy the entire contents of my old home directory to my new partition and add my changes back to fstab.

Thanks for the help! I was afraid I had really screwed myself up.

---

### Post by drs305 on 2008-06-26
> **rdingram said:**
> 
Thanks for the help! I was afraid I had really screwed myself up.

One of the good things about fstab is that it doesn't ever change data - it only makes it accessible or not. 

Please mark this thread solved with the Thread Tools link. 

Good luck with your move... ;-)

---

