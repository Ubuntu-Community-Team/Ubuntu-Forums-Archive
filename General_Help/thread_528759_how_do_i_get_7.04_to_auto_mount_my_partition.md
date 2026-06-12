---
title: "how do i get 7.04 to auto mount my partition ?"
date: 2007-08-18
forum: General Help
---

### Post by syborfical on 2007-08-18
How do I get ubuntu 7.04 to auto mound my partition?

When I installed ubuntu I had ;
A 20 GB system  partition /
100GB ntfs. Partition /dev/sda2


Then I added
I added 120gb EXT partition which is /sda4

My problem is the I have to mount the partition for every user. I have about 5. 
This is a pain in the ****.
And then when I do end up mounting it I cant execute anything off it. 

So what im pretty much asking what how do I auto mount this partition
As /media/disk &#8230; so every user can execute off it? 

Is there one file I can change ? 

Thank you

---

### Post by taurus on 2007-08-18
You can add an entry in /etc/fstab to mount it each time you boot Ubuntu.  Then, everybody can access that partition.

What filesystem is /dev/sda4 anyway?

---

### Post by trak87 on 2007-08-18
hehe You must be British, otherwise that would be three asterisks.

You need to make an entry in /etc/fstab so the external drive is loaded every time at bootup. External drives are problematic however. There are lots of messages on this forum and throughout the net regarding Feisty where folks describe errors with external drives. For example, after a certain amount of time the drive reverts to read-only access. Bummer.

---

### Post by syborfical on 2007-08-19
What filesystem is /dev/sda4 anyway? Is Ext 3

Lol I&#8217;m not british I&#8217;m Australian

---

### Post by taurus on 2007-08-19
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sda4   /media/storage   ext3   defaults   0   1
```
Save the change.  Then, create a new mount point and mount it.

```
sudo mkdir /media/storage
sudo mount -a
df -h
```

---

### Post by syborfical on 2007-08-22
> **taurus said:**
> Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sda4   /media/storage   ext3   defaults   0   1
```
Save the change.  Then, create a new mount point and mount it.

```
sudo mkdir /media/storage
sudo mount -a
df -h
```

Auto mount works for all users.
the only problem is i still cant exercute and the drive is Read-only.
id like all users to be able to read write and exercute.

i have played around with fstab but still cant get this to work..
what are the commands i need to add for exercute and rw for all users

---

### Post by merlinus on 2007-08-22
```

sudo chmod -R 777 /media/storage

```-merlin

---

