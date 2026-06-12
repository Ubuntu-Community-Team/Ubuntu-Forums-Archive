---
title: "How Do I Encrypt An External Hard Drive?"
date: 2014-11-28
forum: General Help
---

### Post by Smallwheels on 2014-11-28
Right now I have some external hard drives that have plenty of data. I have never encrypted anything. Is there a way to encrypt an existing drive with data already on it? 

One important thing is that this needs to work on multiple operating systems. Right now I use GNU/Linux Elementary and Chrome OS. I have owned a Mac Book and probably won't ever buy another one, but; maybe I might need to borrow one or borrow something running (cough-choke) Windoz. I will definitely be trying different versions of GNU/Linux over time too. So this need to work on multiple platforms. 

Will I need to enter a password every time I want to open a folder or file on an encrypted drive? My lack of experience in this area means I really don't know what questions to ask about this topic. Please jump in with any comments or suggestions that explain how encryption can be used. 

The reason I'm now interested in this is I'm going on the road and there will be times when I must leave my computer and drives in a hotel room. Backups will also be made and left in my home. Those will be encrypted too. 

Thank you for your help.

---

### Post by sudodus on 2014-11-28
> **Smallwheels said:**
> Right now I have some external hard drives that have plenty of data. I have never encrypted anything. Is there a way to encrypt an existing drive with data already on it? 

I don't think you can hide the data without encrypting it, but you can encrypt single files, single directory trees, whole partitions, whole drives. And you should wipe the disk space where the data was sitting before the process. I think it is better to move the data into an encrypted drive (and after that wipe the drive where the data was unencrypted).
> 
One important thing is that this needs to work on multiple operating systems. Right now I use GNU/Linux Elementary and Chrome OS. I have owned a Mac Book and probably won't ever buy another one, but; maybe I might need to borrow one or borrow something running (cough-choke) Windows. I will definitely be trying different versions of GNU/Linux over time too. So this need to work on multiple platforms. 

I think you can consider different methods. Pretty Good Privacy, PGP, and the gnu version and software for it, ***gpg***, is available as source code, and can be used in all systems (where you can find a C compiler). Truecrypt is no longer developed or maintained.
> 
Will I need to enter a password every time I want to open a folder or file on an encrypted drive? My lack of experience in this area means I really don't know what questions to ask about this topic. Please jump in with any comments or suggestions that explain how encryption can be used. 

I think it depends on the way you connect to it. If integrated into the system, the original log-in might be enough, like if you have encrypted home in linux, but I'm not sure if that would work in all operating systems. You must expect that increased security will mean decreased convenience, and an encrypted system might need a password 'every time'. And if you forget the password/passphrase, the data are lost.
> 
The reason I'm now interested in this is I'm going on the road and there will be times when I must leave my computer and drives in a hotel room. Backups will also be made and left in my home. Those will be encrypted too. 

Thank you for your help.

-o-

An alternative that is available with the Ubuntu flavours is encrypted home. Another one is encrypted disk with LVM, and encrypted home inside it. See for example this link, actually made for iso-testing, but a good instruction how to install it. These alternatives do not apply to external drives, but the installed system or part of it.

[http://iso.qa.ubuntu.com/qatracker/milestones/318/builds/73663/testcases/1439/results](http://iso.qa.ubuntu.com/qatracker/milestones/318/builds/73663/testcases/1439/results)

---

