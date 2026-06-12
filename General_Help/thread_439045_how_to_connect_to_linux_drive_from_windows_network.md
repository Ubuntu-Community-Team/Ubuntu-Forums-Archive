---
title: "how to connect to linux drive from windows network"
date: 2007-05-10
forum: General Help
---

### Post by paulus4605 on 2007-05-10
Dear
I have the following question:
I have a homenetwork called MSHOME In this network I have My linux pc, a windows laptop and a linux fileserver.
The only problem I have at this point that whenever I want to connect to the linux pc I get a popup screen to enter my username and password? 
I tried the username which I use to enter ubuntu no succes?
when exploring the homenetwork with the linux pc I don't have any access problems 
who can help me out here?
thanks for your help and feedback

Paul

---

### Post by total wormage on 2007-05-10
you'll have to install and configure samba
here are two nice guides :]

[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")
[https://help.ubuntu.com/community/ComprehensiveSambaGuide]("https://help.ubuntu.com/community/ComprehensiveSambaGuide")

good luck

---

### Post by tact on 2007-05-10
What I did was create a folder in /home and gave it a name...  eg...  /home/shared

I cannot remember why I put it in that /home directory now...I am sure I had a good reason at the time.  :)  Oh yes I remember - I had "secured" my own home folder (/home/my_username) by setting permissions such that others cannot even see it exists let alone browse my files...

so there you have it - my shared folder is /home/shared

I had to use sudo to create the directory.  (cos as a user I don't own /home).

I shared that folder (as sudo) but soon found that windows users could not access the folder.  so I had to use sudo to change permissions to 0777 (read/write access to everyone).

hope that helps.

---

### Post by orb9220 on 2007-05-10
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by strabes on 2007-05-10
Yes, you'll have to install the fs-driver on all of the windows machines that you want to be able to access the ext2/ext3 drives on your linux fileserver.

---

### Post by total wormage on 2007-05-11
what? hell no!
you'll only need the fs-driver if you have a ext2 / ext3 harddisk _inside_ your windows computer
when sharing a folder on such a disk on the network it doesn't matter if the computer doesn't have the drivers :p

you just have to configure samba :p
:KS :KS

---

### Post by orb9220 on 2007-05-11
> you'll only need the fs-driver if you have a ext2 / ext3 harddisk _inside_ your windows computer

What are you talking about. I have a dual boot with xp and ubuntu. When I boot into xp I can only access my ubuntu **partitions** with the fs-driver installed. My Ubuntu is not > inside_windows computer.

I think yer confused. The fs-driver is for accessing ext3 partitions normally outside the xp filesystem.

---

### Post by total wormage on 2007-05-11
> **orb9220 said:**
> What are you talking about. I have a dual boot with xp and ubuntu. When I boot into xp I can only access my ubuntu **partitions** with the fs-driver installed. My Ubuntu is not .

I think yer confused. The fs-driver is for accessing ext3 partitions normally outside the xp filesystem.

i am talking about that the person who started this thread is not dualbooting, but simply trying to access a computer on the network, not trying to access a partition.

am i right? :]

---

### Post by orb9220 on 2007-05-11
> i am talking about that the person who started this thread is not dualbooting, but simply trying to access a computer on the network, not trying to access a partition.

am i right? :]

Yes you are and I should not post until more coffee generates the proper synaptic connections and "Brain and Brain,What is Brain!" starts to work.

My apologies, I was Wrrr,Wrrroo,Wrong!

---

### Post by total wormage on 2007-05-11
> **orb9220 said:**
> Yes you are and I should not post until more coffee generates the proper synaptic connections and "Brain and Brain,What is Brain!" starts to work.

My apologies, I was Wrrr,Wrrroo,Wrong!

lol, good luck with that then ;]]]
:KS :KS

ubuntuforums is in need of a coffeesmilie!

---

