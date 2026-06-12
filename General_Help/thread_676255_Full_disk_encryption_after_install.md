---
title: "Full disk encryption after install"
date: 2008-01-23
forum: General Help
---

### Post by chungy on 2008-01-23
Hi everybody... I got a laptop about a month ago, and unfortunately I didn't have the foresight when installing it to have encryption from the start, and now that I might start travelling with it, I would like to encrypt the disc, use a USB drive (I have a 1GB drive that can be used) to boot it so it'll load the encryption keys into RAM etc.

I've tried searching the web, but I haven't found *how* to do this from an existing installation. I don't want to do an install from scratch, obviously that'll take a lot of (imo) unnecessary time. Yes, I know the importance of backups already, no need to lecture me on that... just how to encrypt a disk with existing data on it to preserve?

---

### Post by gvartser on 2008-01-23
To encrypt single or multiple files, like documents etc, your could always use "ccrypt"

Example: encrypt all your private files in your home_dir/private
```
ccrypt -r ~/private
```

It will prompt for at password, do not forget or you will not be able to unlock them again.

I'm aware that this doesn't answer your question regarding the whole file system, but it could come in handy. 

/g

---

### Post by chungy on 2008-01-23
Yeah, I want my ENTIRE disk encrypted. I don't want to worry about what to encrypt, or what not to encrypt. I don't need my emails saved in swap, or my bookmarks in /var (who knows why Konqi keeps them there ~_~), and have to worry about them. In short, I want my whole disk encrypted so I don't have to worry about *anything* of any importance being left unencrypted.

---

### Post by Craigus on 2008-01-23
> I don't want to do an install from scratch, obviously that'll take a lot of (imo) unnecessary time.

I'm not convinced that doing it the way you are wanting to will be any quicker.

I guess you've found this:

[https://help.ubuntu.com/community/EncryptedFilesystemHowto]("https://help.ubuntu.com/community/EncryptedFilesystemHowto")

---

### Post by chungy on 2008-01-23
I looked over it, but it didn't seem to satisfy the wish to keep my partitions exactly as they are, just encrypting them (besides obvious config changes required)...

I should also note that I will not mind having to boot into a live environment such as RIP, I've already anticipated that this will probably be necessary.

---

### Post by bodhi.zazen on 2008-01-23
As far as I know, encryption is destructive.

Here is a nice how to : [http://www.hermann-uwe.de/blog/towards-a-moderately-paranoid-debian-laptop-setup--part-1-base-system](http://www.hermann-uwe.de/blog/towards-a-moderately-paranoid-debian-laptop-setup--part-1-base-system)

Sure, it's debian, but ...

---

### Post by chungy on 2008-01-23
*sigh* I don't get why encryption has to be necessarily destructive... when you can encrypt normal arbitrary files.

Well I could probably handle having to do multiple partitions. My current setup is a / (/dev/sda1) and a swap (/dev/sda2) partition. I could resize /dev/sda1 small enough to create a /dev/sda3 between them, and move files...

eventually the plan is to return to my original setup more or less:
1. With an encrypted partition, how difficult would it be to move and resize it (I assume you'd just do "resize2fs /dev/mapper/crypto" like you would normally do on an unencrypted partition)
2. How could I make a USB boot device to load the kernel, necessary modules, etc to store the encrypted key? Obviously having the key itself on hard disk is a bad idea.

---

