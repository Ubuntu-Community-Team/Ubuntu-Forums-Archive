---
title: "acess shared folders in windows"
date: 2008-06-18
forum: General Help
---

### Post by dapim on 2008-06-18
Hi,

How can i acess to shared folders in a network, the shared folders are in windows machines,
do i have too install samba server in my machine, for acess the files that are in windows machines?

---

### Post by bubba_169 on 2008-06-18
Not got a lot of experience here but I think think you need to install smbfs by going into a terminal and typing ```
sudo apt-get install smbfs
```then your Windows computers and workgroups will show up in Places->Network from the main menu bar.

I think... :D

---

### Post by infinitezero on 2008-06-18
bubba_169,
Follow this link and download the howto:
[http://ubuntuforums.org/showthread.php?t=832165](http://ubuntuforums.org/showthread.php?t=832165)

iz

---

### Post by bodhi.zazen on 2008-06-19
> **dapim said:**
> Hi,

How can i acess to shared folders in a network, the shared folders are in windows machines,
do i have too install samba server in my machine, for acess the files that are in windows machines?

no it should work out of the box.

You windows shares will not show up in the gui

go to connect to a server, enter you windows IP address => connect.

you so not need to install anything.

---

