---
title: "Mounting :s"
date: 2006-11-12
forum: General Help
---

### Post by iLoVe.cF- on 2006-11-12
hmm..

How to mount ext3 in edgy.. the disk thing in system->perf. or whatever aint in edgy anymore :'(

Ext3 filesystem.. and the fstab is so gay now.. since it got changed in edgy :p

---

### Post by nikhilk on 2006-11-12
Do yo mean through the GUI specifically or mounting a partition generally?
Through CLI it is simple, just say
mount -t ext3 <mount_point> <partition_to_mount>

---

### Post by syadnom on 2006-11-12
fstab is better now from a technical perspective.  now drives are mounted via their id number so usb thumbdrives or external harddisks can be mounted reguardless of their /dev points changing.

this is a good thing.  also, the old syntax still works great as well


/dev/sda1   /usr ext3 default 0 0   !!!

---

### Post by aysiu on 2006-11-12
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by iLoVe.cF- on 2006-11-13
tnx.. 

Ubuntu REALLY NEED A AUTO MOUNT THING.. Seriously.. 

I got like 8 dirves.. for a hdd rack.. and swapping between them.. is like hell :'(


It's kinda messy.. :p

So im gonna make a raid file server =)

8 hdds raid 5 = =) ?:D

but anyway.. tnx for answers =)

---

### Post by aysiu on 2006-11-13
You're right--Ubuntu needs better automounting.

I don't know why it doesn't have it. Knoppix and Mepis have had it for years.

---

### Post by iLoVe.cF- on 2006-11-13
ilove@ilove-desktop:~$ gksu gparted
======================
libparted : 1.7.1
automounting disabled


Hmm.. Automounting is supported.. ? :p

Why not use it as standard ? :p

---

### Post by iLoVe.cF- on 2006-11-20
hmm.. now i got another problem.. :P

How do you get Full permission on EVERY folder inside a partition WITHOUT doing 
sudo chown /media/Pata250GB/Download/CKY
Sudo chmod -R 755 /media/Pata250GB/Download/CKY 

?

I want all folders to be mine.. with one command. i got a non sorted hdd.. cuz i cleaned up about 7 partitions.. and everything is just thrown in that partition.. and its a pain in the *** to do alot of commands...

any suggestions ? =)

---

