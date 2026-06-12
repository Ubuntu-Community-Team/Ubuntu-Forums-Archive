---
title: "Restore whole system from network stored backup?"
date: 2014-05-11
forum: General Help
---

### Post by Jaman42 on 2014-05-11
Hi,
I have read some about Clonezilla which seems to be able to do what I want but I thought I asked here first, perhaps there is another way that's more suitable for me.

I have two NUC's running Ubuntu 14.04, one is used as a server and the other as a client. I want to make a full system backup (image) of the client and store that on the server. If I put a new hard drive in the client I want to connect to the server and do a full system restore from the stored backup.

Can I do this with Clonezilla? Any other ways? Any advice on what I need to set up to get it working?

Thanks for reading

---

### Post by spynappels on 2014-05-11
Yep, Clonezilla will do that for you.

You'll need to boot from a USB drive with Clonezilla on it, and either plug in a USB HDD or use another storage server accessible through ssh or Samba.

Then just create an image from the local disk, the prompts you will get on the screen are pretty comprehensive and will walk you through the process.

Restoring is almost the same, except you choose restore from image instead of create image.

---

### Post by Jaman42 on 2014-05-11
Thanks for the quick reply!

I have already set up ssh access to the server so that sounds like a simple way of doing it.

---

### Post by Jaman42 on 2014-05-21
Another question, the image I want to make is on a 1TB disk. Is it possible to make a image of used data only? Do I have to resize the partition before I make a image or are there any other ways to accomplish this?

In my case I got a fairly clean Ubuntu 14.04 installation with some programs and additional files. Total size is around 5GB only.

Edit: Reading on clonezilla site about "Partclone" but it also says its the default. When I tried to make a image earlier it got aborted stating there wasn't enough space, but there are plenty of space left. I must be doing something wrong. I choose to make a image backup to a ssh server, entered the server ip, username and password, choose the folder where the image should be stored. I used the wizard for beginners. Any ideas?

---

