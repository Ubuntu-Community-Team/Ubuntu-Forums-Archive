---
title: "NTFS Drive on Ubuntu 7.10 Permissions"
date: 2007-10-25
forum: General Help
---

### Post by duncan426 on 2007-10-25
I have a dilemma.  I am running 7.10 and have a NTFS drive hooked up to my system as an external drive.  IT shows up it my /media folder.  I use a program called ycopy to copy all the necessary data from the HD to a server.  When I try to copy the data from this hd it wont copy hardly any files because of permissions.  on my windows box all i do is take owenrship od the drive and everything copies.  I am new to linux and was wondering do i need to do the samething in ubuntu.  How do I take ownership of the complete drive and all the files.  Thanks for any help.

---

### Post by taurus on 2007-10-25
Try using sudo.

```
gksudo nautilus
```
Then, just drag 'n drop.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

