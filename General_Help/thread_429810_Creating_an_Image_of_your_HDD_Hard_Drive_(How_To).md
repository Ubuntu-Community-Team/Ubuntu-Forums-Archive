---
title: "Creating an Image of your HDD Hard Drive (How To)"
date: 2007-05-01
forum: General Help
---

### Post by nami on 2007-05-01
I have managed to partition my hard drive ready to create a backup image of my existing ubuntu install ready to test out ubuntu 7.04.  I want to create an image of the existing install so I can easily roll back to it if the ubuntu 7.04 upgrade goes wrong.

How do I create an image.  I tried using a certain bit of software (cant remember the name) but it was too difficult.

Any help would be appreciated greatly.

Thanks

nami

---

### Post by aysiu on 2007-05-01
Various backup methods are described and/or linked to here:
[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

---

### Post by Irony on 2007-05-01
I've always found this method very easy;

[http://ubuntuforums.org/showthread.php?t=416710](http://ubuntuforums.org/showthread.php?t=416710)

---

### Post by nami on 2007-05-02
Thanks,

I'll look into these on the weekend. :KS

---

### Post by nami on 2007-05-05
The partition I created, I can't seem to see in the system monitor.

[[IMG]http://img522.imageshack.us/img522/772/screenshotcb7.th.png[/IMG]]("http://img522.imageshack.us/img522/772/screenshotcb7.png")

The partition is a ext2 and is hda3.

Do I have to mount it or something?

---

### Post by nami on 2007-05-05
> **aysiu said:**
> Various backup methods are described and/or linked to here:
[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

I am trying to follow the tar guide in that link but it says:

> and go to the root of your filesystem (we use this in our example, **but you can go anywhere you want your backup to end up**, including remote or removable drives.)

How do I go to the new partition I created to store the backup?

---

### Post by aysiu on 2007-05-05
You have to mount the new partition first.

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux) will help you. Just change all the references to *ext3* to *ext2*.

---

### Post by nami on 2007-05-05
Thanks, checking it out now.

---

### Post by nami on 2007-05-05
So if I wanted to unmount the partition, do I simply remove the line from the /etc/fstab file and execute the command "sudo mount -a"?

This will only unmount the partition won't it, it won't delete the information stored in the unmounted partition, or will it?  It may seem like a stupid question, but I need to make sure. :)

---

### Post by aysiu on 2007-05-05
I don't know the answer the first question. I'd probably specify the partition to unmount: ```
sudo umount /dev/hda3
``` But, yes, if you unmount a partition, the information isn't deleted off it. It's just disconnected and safe to turn off or remove physically.

---

### Post by nami on 2007-05-05
Excellent, the backup is taking place as I speak.....  type. :)

---

### Post by nami on 2007-05-05
Got a question:

In that guide (the one about mounting a partition), it said that I need to do the following:

> sudo chown -R marie:marie /storage

I replaced the marie with my own name.  If the system breaks and I need to restore the backup, will the live cd give me rights to that partition?  If the system breaks, will the rights/usernames not get messed up, stopping me from getting access to the backup partition?

---

### Post by aysiu on 2007-05-05
You can always access *anything* from the live CD unless it's encrypted.

---

