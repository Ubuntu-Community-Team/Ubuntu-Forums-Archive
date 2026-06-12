---
title: "How to install programs to a Different Partition"
date: 2007-03-07
forum: General Help
---

### Post by muffinhead on 2007-03-07
I want to Install/Re-install Ubuntu Edgy Eft, but I'd like to be able to do this if possible:

Create a 2 - 4 Gig Partition for Ubuntu on my Secondary D: Drive.

I'd Also like to Create a Second Partition for my Programs so I'm not using up space on the main Ubuntu Partition.

Once I make these Partitions, is there a way I can direct programs to install on a second partition rather than the Ubuntu Partition?

I always notice it wants to always install in the users home directory or a directory in the root filesystem.

Thanks if anyone can help, and sorry if my question is a bit n00bish ;)

---

### Post by zvacet on 2007-03-08
All programs dowloaded by apt-get or synaptic are stored in var/cache/apt/archives.All programs made theire hidden folders in  your home directory.I think that you want preserve your programs and data during reinstall.Most common way to do that is to make separate home partition.
[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")
I recomend you to make your home partition bigger than root.For root is enough 10-15GB.Swap ia around 1GB(depends of your ram).If you do this way you can reinstall without losing files.One more thing.Before reinstall copy var/cache/apt/archives to your home directory.After reinstall copy them back to var/cache/apt/archives and you will have all your programs and updates preserved.To install content of var/cache/apt/archives 
```
cd /var/cache/apt/archives
```
and when you are there 
```
sudo dpkg -i *deb
```

---

### Post by muffinhead on 2007-03-09
Thanks for the reply.

However that's not what I meant. I don't want to store a backup of packages or Programs.

I instead want to install programs so I can use them on a separate partition so I'm not using my root ubuntu partition to install programs onto because my hdd space is limited now that one of my hard drives burned out.

I also dualboot windows XP as well further limiting available hdd space.

I wanted to make a separate partition on my main hdd, the C: Drive Windows XP is installed on, to install all my Linux or Ubuntu programs, and install Ubuntu (Root) on My Secondary Hard Drive (D: Drive in Windows)

I hope I'm wording this clear enough. Thanks if anyone can help me on this ;)

---

### Post by muffinhead on 2007-03-13
Anyone???? 

A Definite answer on whether this can be done or not would be very much appreciated;)

---

### Post by peabody on 2007-03-13
All installed software files go under /usr.  Xorg, Gnome, everything has its mits in that heirachy.  Put that on the partition you want the programs on.

---

