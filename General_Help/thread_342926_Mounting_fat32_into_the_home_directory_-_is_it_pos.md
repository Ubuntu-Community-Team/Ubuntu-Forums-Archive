---
title: "Mounting fat32 into the /home directory - is it possible?"
date: 2007-01-20
forum: General Help
---

### Post by knemir on 2007-01-20
Hello everyone,

I have two questions: How to mount fat32 partition into the /home/user_name/some_folder ? And the second one: How to get a pernission to write in that folder (some_folder)? I menaged to mount a partition but I don't know how to get a permission. I tried everything with chmod, but obviously I don't know how to do that. The root has a permission so I can't do anything even when I'm using a sudo. Also, do I have to change something in fstab? 

Thanks in advance.

---

### Post by meng on 2007-01-20
Sure, no problem. Look here for mounting FAT partitions:
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by knemir on 2007-01-20
Thank you very much! This was really helpful! But now, I have a strange message when I'm logging into the system:

User's $HOME /.dmrc file is being ignored. This prevents the default session and language from being saved. Fle should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users"

I suppose that I somehow changed the permissions for my /home/user_name folder.  By the way, what are the default settings for /home directory (I mean "right click on my local folder --> Properties --> Permissions). What should stand for Group permissions and what for the Execute (checked or unchecked)?

---

### Post by meng on 2007-01-20
[http://www.ubuntuforums.org/showthread.php?t=337468&highlight=.dmrc](http://www.ubuntuforums.org/showthread.php?t=337468&highlight=.dmrc)

---

### Post by knemir on 2007-01-20
Is it possible that I receive this message because in my /home/user_name/some_directory is mounted fat32 partition which is owned by root? Anyhow, I still have no permission to write in that fat32 partition. How can I change this?

---

### Post by meng on 2007-01-20
What are the ownership/permissions on /home/user_name/some_directory?

ls -l /home/user_name

will tell you

---

### Post by knemir on 2007-01-20
Now it's really starting to be hairy! I tried with "sudo chmod 700 /home" (without my /user_name directory) and now I can not log in (posting this from windows)!? And if I start in recovery mode, what should I enter to take back my home directory?

---

### Post by meng on 2007-01-20
sudo chmod 755 /home

---

### Post by knemir on 2007-01-20
Here I am - again in Ubuntu :) Thank you very much for help...

---

### Post by meng on 2007-01-20
Glad you got back in! Sounds like you like to live life on the edge.

---

### Post by knemir on 2007-01-21
When you have a lack of knowledge everything is like on the edge :biggrin:  Regards!

---

### Post by rianquinn on 2007-01-21
Make sure you mount the drive correctly. Otherwise you won't have write permissions.

The problem for me usually exists in the /etc/fstab

---

