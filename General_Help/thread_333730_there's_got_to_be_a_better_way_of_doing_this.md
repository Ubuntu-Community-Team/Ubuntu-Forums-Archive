---
title: "there's got to be a better way of doing this"
date: 2007-01-07
forum: General Help
---

### Post by band-aid on 2007-01-07
In my current setup I have my / in its own 6 GB partition and my /home is in its own. I have 2 GB of swap space and the rest of my hard drive is a windows partition that I use for games.

Why does my root partition get filled up so quickly? I was under the impression that most stuff would be stored in my /home and thats why I made it so large. The reason I am bring this up is because my root filled up unexpectedly and I had to extend the partition. In this process it was corrupted and I had to reformat it. Fortunately my home is fine but lots of other stuff is messed up. Should I completely reformat and start over or should I try and get it working again. How can I get things to use my /home rather than /root or should I put everything on one big partition. I'm kinda confused right now.

---

### Post by scrooge_74 on 2007-01-07
In home you are going to have your user files and configs for that user, but in the / partition is the system and temp files and any program you install to the system.  Packages from the repos get store after installing so you have to delete them, and a lot of other stuff is there like log files, etc

---

### Post by band-aid on 2007-01-07
where are the packages stores so I can keep them under control?

---

### Post by rioghal on 2007-01-07
I have two partitions, both created during the install of Ubuntu 6.06.1 LTS. /dev/hda1 is the '/' partition, which holds everything on the computer. /dev/hda5 is the swap partition. The bulk of the system is going to be in your '/' (root) partition along with almost every app you install from now on. The /home partition only holds your user files and configurations for your user. It sounds as if you were a bit confused to start with, but that's what these wonderful forums are for :D

You really don't want all system apps in your home because if someone broke into your computer, they can easily destroy or take over your computer.. this is why the 'root vs user' model is so much better than having a normal user run as root all the time. Thank $DIETY for sudo, eh?

This root/user model is also why there aren't many viruses for Linux.. it's a waste of time to write a virus that won't do much damage and can't go very far :)

---

### Post by scrooge_74 on 2007-01-07
not sure where they are but after you install something you can do 

sudo apt-get autoclean

---

### Post by RandomJoe on 2007-01-07
The packages are stored in /var/cache/apt/archives, but I'm not sure if it's wise to just delete them - you may need to do some command like scrooge_74 listed to make sure the apt database is kept up to date...  (I'm new to apt!)

In a multi-user setup, then it is more true to say most of the space would be in /home, since any programs you would add would be installed to your own directory.  (And also wouldn't have access to other parts of the system.)  But since we are acting as our own sysadmins when running the package managers, everything gets added to the system directories.  6GB is pretty small nowadays, unless you run a really stripped down setup.

---

### Post by band-aid on 2007-01-07
ok yea I was definately confused from the start, I'll swap around my sizes making my home my root and my root my home. Can gparted do this without nuking everything? I'm going to resize both.

---

### Post by scrooge_74 on 2007-01-07
You better backup your important data, if you repartition there is always a good change you can loose stuff.

---

