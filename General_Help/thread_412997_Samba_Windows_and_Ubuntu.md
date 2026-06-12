---
title: "Samba Windows and Ubuntu"
date: 2007-04-18
forum: General Help
---

### Post by FeraTech on 2007-04-18
Well I have a problem. I've reached the 10 user limit with Windows XP shared folders.

Now, ideally I would like to install Samba on the Windows machine to simply get around the 10 user limit. However, I can not find any info on how to do this.

If worst comes to worst, I have not used Samba on Ubuntu yet but out of the box with either Edgy or Feisty how easy is Samba to set up on both?

---

### Post by rufius on 2007-04-18
You're probably better off setting up a samba server on Ubuntu. The ease of setup should be about the same for both. I have a tutorial for setting up samba on a Linux system thats fairly generic though the operating system used in the tutorial was Mandriva. 

Here's what you need to do before you read the tutorial:
```
user@localhost:~$ sudo apt-get install samba
user@localhost:~$ sudo /etc/init.d/samba start
```

Then read this guide: [http://zacbrown.org/tutorials/SAMBA-HOWTO/](http://zacbrown.org/tutorials/SAMBA-HOWTO/)

It comes with a sample smb.conf. I've been using samba for about 5 years now on the server described in that tutorial and its been great.

---

