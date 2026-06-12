---
title: "Show/Give drive name, and not &quot;xx.x GB media&quot;"
date: 2008-06-06
forum: General Help
---

### Post by studo77 on 2008-06-06
Hi, I went through a lot of partitioning, and file moving.

I am now free of NTFS! yay.

But, my partitions shows up in places as "xx.x GB media". How do i give the partition a name?

The windows equivalent is to right click the drive in explorer, and change the name.

But where and how do i do this in Ubuntu. In GParted i can't find anything that does this. Nautilus also has nothing.

It is frustrating to remember that size disk is for my documents, and that size is for music.

I have mounted the partitions in a logical structure in /home, but i would like to change the name showing in "Places" and Nautilus, same thing.

How do i do that?

---

### Post by sdennie on 2008-06-06
You should be able to do this using e2label.  For example, if your music partition is /dev/sda2:

```

sudo e2label /dev/sda2 Music

```

You may have to logoff/logon before you can see this change in nautilus or possibly reboot (I'm sure there is a service you can restart for this to work but, I'm not sure which).

Edit:
This assumes the partitions are ext2/ext3.  There are similar commands for other filesystems though.

---

### Post by kpkeerthi on 2008-06-06
> **studo77 said:**
> Hi, I went through a lot of partitioning, and file moving.

I am now free of NTFS! yay.

But, my partitions shows up in places as "xx.x GB media". How do i give the partition a name?

The windows equivalent is to right click the drive in explorer, and change the name.

But where and how do i do this in Ubuntu. In GParted i can't find anything that does this. Nautilus also has nothing.

It is frustrating to remember that size disk is for my documents, and that size is for music.

I have mounted the partitions in a logical structure in /home, but i would like to change the name showing in "Places" and Nautilus, same thing.

How do i do that?

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive). Works for non-USB  disk partitions too.

---

### Post by studo77 on 2008-06-06
Thanks for the help! It takes a reboot, for the names to work.

I did forget to say i am using ext3, on the partitions. The USBrename link gives an explanation for all types of disks. Nice.

But i found another thing, after i reformatted. File recovery tools mostly say it only works on ext2. Can that give me problems? Not that i care alot, but an accidental delete can happen once every three years. (in my experience) So in a few years the tool might exist.

---

