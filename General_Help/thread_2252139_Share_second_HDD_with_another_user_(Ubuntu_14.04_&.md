---
title: "Share second HDD with another user (Ubuntu 14.04 &amp; 14.10)"
date: 2014-11-09
forum: General Help
---

### Post by aquablue25 on 2014-11-09
Greetings,

we have two HDD's in our PC: One with Ubuntu on it and the other for data storage and backups. But are formated as EXT4, but only I can access the data-drive though. My girlfriends account, which has the same level of access as my account (admin), can't access the drive. 

How do I change that?

Thanks,
Aqua

---

### Post by nerdtron on 2014-11-09
That depends on what you may want to do. Do you want her to delete/edit the files owned by you and vice versa?

You can use "sudo chmod 1777 /media/data-drive/" to do so.


EDIT: Only owner/creators of the file will be able to edit/delete when run the above command. However, both of you can save on the folder.

---

### Post by aquablue25 on 2014-11-09
Hello,

yeah, she should be able to read, write, delete and edit all files on the drive and vice versa.

I'll try what you suggested and report back ASAP. Btw, is there a way to do what you wrote via a GUI?

Thanks,
Aqua

---

### Post by nerdtron on 2014-11-09
> **aquablue25 said:**
> 

I'll try what you suggested and report back ASAP. Btw, is there a way to do what you wrote via a GUI?


HHmm.. not sure, I don't you'll be able to set this permission in GUI since you need to enable the sticky bit.

> yeah, she should be able to read, write, delete and edit all files on the drive and vice versa. 
Haven't tried this before so let me test.

---

### Post by aquablue25 on 2014-11-13
Hello there,

sorry that it took so long for me to reply, it was a busy week.

Anyway, I managed to share the drive without having to use the terminal. Lol, kinda funny that I didn't see it before. All I had to do is set the correct read and write rights for "other users" via right click on the drive - properties - access rights:

[IMG]http://s14.directupload.net/images/141113/34pskbue.png[/IMG]

Thanks again for helping me out though!

Cheers,
Aqua

---

