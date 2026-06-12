---
title: "Install Ubuntustudio without a DVD or Internet Connection"
date: 2008-03-03
forum: General Help
---

### Post by ShanghaiTeej on 2008-03-03
Greetings,

I need to install Ubuntustudio to a computer that:

A:  Doesn't have an Internet Connection

B:  Doesn't have a DVD drive (it only has a cd drive)

Besides the obvious choices that cost money (getting cable or buying a dvd drive), is there anyway I can download the parts of Ubuntustudio that I need onto a CD?  If there is, can someone point me in the right direction.

Note:  I already know that I can install Ubuntu on the computer and then upgrade to Ubuntustudio with the official repos.

Any help would be much appreciated!

---

### Post by jeffus_il on 2008-03-03
Download and burn the CD from here:
[PC (Intel x86) alternate install CD]("http://cdimage.ubuntu.com/ubuntustudio/releases/gutsy/release/ubuntustudio-7.10-alternate-i386.iso")

---

### Post by ShanghaiTeej on 2008-03-03
Thank you for your quick reply.  So I can just pop this CD in with a normal Gutsy running and install all the files for Ubuntustudio with this cd instead of the online repos?

---

### Post by jeffus_il on 2008-03-03
It's a full install CD, It will reinstall your OS. It is an "alternate" CD which means your run the install from the command line.

You can also do an upgrade using these instructions:
```
**Upgrading using the alternate CD/DVD**

 Use this method if the system being upgraded is not connected to the Internet. 
 [LIST=1]
[*]Download and burn the alternate installation CD.
[*]Insert it into your CD-ROM drive.
[*]A dialog will be displayed offering you the opportunity to upgrade using that CD.
[*]Follow the on-screen instructions.[/LIST] If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2: 
 gksu "sh /cdrom/cdromupgrade"
Or in Kubuntu run the following command using Alt+F2: 
 kdesu "sh /cdrom/cdromupgrade"
```

taken from [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by ShanghaiTeej on 2008-03-03
Actually, that is an Alternate install DVD that is mislabeled as a CD....so I'm right back where I started.  But I thank you for your speedy help regardless!

---

### Post by jeffus_il on 2008-03-03
Oh, I see it's 800Mb in size. the other alternative is to get the ubuntustudio packages from the archive, burn them to a CD and then use synaptic to install them.

---

### Post by ShanghaiTeej on 2008-03-03
Thanks.

Do I have to put them special folders on the cd?

---

### Post by jeffus_il on 2008-03-03
I am not sure, I haven't used it myself, here is a reference:
[https://wiki.ubuntu.com/AddLocalRepositorySpec](https://wiki.ubuntu.com/AddLocalRepositorySpec)

It should work.

---

