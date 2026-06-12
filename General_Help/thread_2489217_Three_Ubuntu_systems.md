---
title: "Three Ubuntu systems"
date: 2023-07-22
forum: General Help
---

### Post by h4n2 on 2023-07-22
Good afternoon. The physical disk is divided into 3 disks C, D, E. How to install Ubuntu 20.04 on each disk? I tried, it didn't work, the problem is more likely in the file system. Please help. Thanks in advance!

---

### Post by Rubi1200 on 2023-07-22
Hi and welcome to the forums :-)

What is currently installed on the disk/partitions?

Do you want to dual-boot with Windows or just use Ubuntu on the whole drive?

---

### Post by tea for one on 2023-07-22
> **h4n2 said:**
>  The physical disk is divided into 3 disks C, D, E. How to install Ubuntu 20.04 on each disk? I tried, it didn't work, the problem is more likely in the file system.
I suspect that you mean the disk has three partitions?
Before we go any further, can you let us know your level of experience with Ubuntu?
Installing the same OS three times on one disk is an unusual task?

---

### Post by h4n2 on 2023-07-22
Yes, three Ubuntu on all logical drives - one physical drive.

---

### Post by h4n2 on 2023-07-22
Hardware -M2 1TB/ 9900/ RTX1660/ 32 ram
Three people in the family, each saves a password and has access to one system - one Ubuntu.

---

### Post by dragonfly41 on 2023-07-22
Given the oft warning in these discussions not to put all your eggs in one basket, apply n+1 redundancy engineering methods,  installing on one device is questionable.

I have one old OS still buried in a Windows boot but my main boot is into an external SSD device with current Ubuntu.

You could have separate SSD's  with Ubuntu in each. Or you could have several virtual Ubuntu machines. Or several Virtual desktops in the cloud.

All depends on the reasons for having three OS. Once you explain you might get more directed ideas.
One final point. I use rEFInd to switch between multiple OS configurations. Great little installtion easily installed. One per OS or one servicing all OS.

P.S. I see that you explained while I was typing.

You can have three users accounts on a single OS. Again dependes on pattern of use.

---

### Post by Rubi1200 on 2023-07-22
> **h4n2 said:**
> Yes, three Ubuntu on all logical drives - one physical drive.
Personally, I don't think this makes sense.

One partition with 3 user accounts would be easiest to manage and maintain.

You could consider using one of the other partitions as shared storage for all 3 users if that is relevant

Just my personal point of view.

---

### Post by dragonfly41 on 2023-07-22
Remember backup religion. @TheFu.

---

### Post by h4n2 on 2023-07-22
For each user, separate browsers with browsing history? Separate browser fingerprints?

---

### Post by Tadaen_Sylvermane on 2023-07-22
> **h4n2 said:**
> For each user, separate browsers with browsing history? Separate browser fingerprints?

Yes. A separate user account is entirely off limits to the other users if you choose. You don't need an entirely separate installation for them. I suppose there is nothing wrong with it but it's totally unnecessary and makes management more complicated. Also takes more time to reboot than it does to log out / log in a different user.

Truthfully Windows has a near same feature but it's not as robust and almost no one ever bothers to check if it exists or uses it.

*EDIT* The only downside that I know of to this is in the case of using Wine or any other frontend that uses it. Steam is a similar problem. When you install Steam games they are installed to the users folder. No problem. But if more than one user uses the same game / games then it becomes a storage problem because by default each user has their own "installation" of steam games / wine prefixs. The size of what games or software you use in these method can make storage needs grow real fast if more than one of the users uses them. In my case I play World of Warcraft via Bottles. The bottles flatpak data folder is over 90gb right now. That would be duplicated for each user under their accounts if they also played the same game. So it can be problematic to a degree.

---

### Post by h4n2 on 2023-07-22
How many accounts does ubuntu 20.04 support?

---

### Post by Tadaen_Sylvermane on 2023-07-22
You have access to 50 or 60 thousand uids so... storage is your realistic limit.

---

### Post by Rubi1200 on 2023-07-22
This is what I would do (others may have better solutions):

1. decide how many users you need on the system
2. decide what permissions each user will have
3. create a test user and check all the settings and permissions are as you want them
4. create the real users
5. delete the test user

This link can help: [https://help.ubuntu.com/stable/ubuntu-help/user-add.html.en](https://help.ubuntu.com/stable/ubuntu-help/user-add.html.en)

---

### Post by h4n2 on 2023-07-22
I made test users and they have the same Canvas Fingerprinting in the browser. How to make it so that it would be different for chromium?

---

