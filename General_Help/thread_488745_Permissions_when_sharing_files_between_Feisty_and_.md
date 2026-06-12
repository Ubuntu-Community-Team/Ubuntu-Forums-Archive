---
title: "Permissions when sharing files between Feisty and Windows XP"
date: 2007-06-30
forum: General Help
---

### Post by markdr on 2007-06-30
Hello. I'm new to these forums as well as Ubuntu in general.

I've set up my computer as a dual boot with Feisty and Windows XP, with a partition for all my documents and data that both OS's can access. This has been set up correctly and indeed both can access it.

However using Ubuntu (7.04), I cannot create, edit or delete files in the folders in this partition that were created in Windows - "Cannot move [x] to the Deleted Items folder because you do not have permissions to change it or its parent folder."

Is there anything I can do to give Ubuntu permission to edit all the files/folders on this partition? As you can probably tell I'm a total newbie to Ubuntu.

Thanks in advance.

---

### Post by markdr on 2007-07-01
*shameless bump*

I'm only trying to do this so I can have access to Windoze whilst I learn Ubuntu...more than likely I'm going to switch to Ubuntu full time when I'm confident enough with it. :p

---

### Post by element3260 on 2007-07-01
I cant believe no one has replied to your post yet...

anyway, their is a program that which makes it very simple to access your windows drives with read/write access, its called ntfs-3g

To install just open up a terminal (Applications > Accessories > Terminal) and type"
```
sudo apt-get install ntfs-config
```

Then wait until it has finished and go to Applications > System Tools > NTFS Configuration Tool

If your NTFS partitions are not yet configured, it will ask you to choose a name that will be use as mount point. Just put the name you want.
Then just enable write support for internal and/or external device, and that's all.
                                                                ~givré's tutorial

---

### Post by markdr on 2007-07-02
Thanks for the reply, put me on the right lines.

I didn't need the tool as the partition was already formatted as FAT32.

The hack I used was changing fstab to make my user the owner of the partition/mount.

Thanks.

---

