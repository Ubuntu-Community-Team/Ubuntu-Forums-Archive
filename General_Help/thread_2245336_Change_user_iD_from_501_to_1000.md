---
title: "Change user iD from 501 to 1000"
date: 2014-09-22
forum: General Help
---

### Post by Bhakti108 on 2014-09-22
I have an issue with a directories on an external HDD created on a mac. those dir have a user ID of 501 which means I cannot access their contents in Ubuntu. I no longer have the Mac that created them, (I trashed it lol) 

Does anyone know how to change the UID to 1000 or above so that I can then use sudo chown to change the permissions to read write and get my documents into Ubuntu.

TIA

---

### Post by TheFu on 2014-09-23
Are you saying that **sudo chown** doesn't work?  What is the error?

I'd use **find** with the **-uid** search option, then **-exec **into **chown**.  **man find** will explain and there are many examples on the internet.

Of course, this assumes a Linux file system on that external drive. I don't know what happens with OSX file systems.

---

### Post by coffeecat on 2014-09-23
If the external HD is formatted HFS+ journalled (which is more than likely) you will only be able to mount the drive read-only. Therefore you will not be able to chown or chmod the contents. Off the top of my head, there are three options:

1 - use another Mac to disable the journal in the HFS+ filesystem, after which you will be able to mount it read-write in Ubuntu and chown the UID of the files you need from 501 to 1000. You'd need to google how to disable the journal in MacOS. Years ago, you could do this from Disk Utility, but then in versions around Leopard and Snow Leopard, you had to use the Mac terminal. I vaguely remember reading that with later versions of MacOS you could use Disk Utility again, but I may be wrong on that point.

2 - If you have access to another Mac, even better would be to use the Mac to change ownership and/or permissions on the files you want to copy. You can use either the GUI or the terminal.

3 - Failing all this, using a root-owned file manager in Ubuntu should allow you to browse the contents of the HD and copy the files to another filesystem.

One big caveat. If the HDD is a Time Machine backup you won't be able to access any of your files from Ubuntu in the ordinary way. If that is a Time Machine backup, have a look at this post:

[http://ubuntuforums.org/showthread.php?t=2193764&p=12874113&viewfull=1#post12874113](http://ubuntuforums.org/showthread.php?t=2193764&p=12874113&viewfull=1#post12874113)

---

### Post by Bhakti108 on 2014-09-28
Thanks for the information guys. After some time I realised that I could not change the UID because the ext drive is indeed hfs+. So managed to find a a mac, and changed permissions for the folders and files I needed. 

So all is good now. 
Thanks

---

