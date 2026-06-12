---
title: "Installing another OS / Dual Boot"
date: 2007-10-21
forum: General Help
---

### Post by RuB3N on 2007-10-21
I have been using ubuntu for a while now and it is my mail OS. But I want to try a new linux os just for fun and to see how it compairs.

I have partitioned my hard drive to where i can dual boot and have my mail os and my extended partition for adventuring other linux os.

How would i go about breaking up my extended partition to where I can safely install a new os in it without messing up my main partitions 1,2,and 3?

---

### Post by benerivo on 2007-10-21
You should be able to just shrink sda5, by about 8GB from the live cd, and make a new partition in the resulting free space to put the other linux. Or make two partitions in the free space and have a '/' and a '/home' setup as you do now.


EDIT - resize using gparted partition manager from the live cd.

---

### Post by oilchangeguy on 2007-10-21
> **RuB3N said:**
> I have been using ubuntu for a while now and it is my mail OS. But I want to try a new linux os just for fun and to see how it compairs.

I have partitioned my hard drive to where i can dual boot and have my mail os and my extended partition for adventuring other linux os.

How would i go about breaking up my extended partition to where I can safely install a new os in it without messing up my main partitions 1,2,and 3?

if all you want to do is check out another distro, find a distro(s) that use live cd's (not all do). and run it that way, just to compair. if you must install it, make sure to backup your data BEFORE you do anything, incase something goes wrong.

---

### Post by RuB3N on 2007-10-21
Ok I did something wrong.

it wont give methe option to boot ubuntu or fedora.

this is what my partition looks like.

---

### Post by rsambuca on 2007-10-21
> **oilchangeguy said:**
> if all you want to do is check out another distro, find a distro(s) that use live cd's (not all do). and run it that way, just to compair. if you must install it, make sure to backup your data BEFORE you do anything, incase something goes wrong.
I don't think you can get a true feeling for a distro from the liveCD.  They are better just for checking out-of-the-box hardware compatibility.  There is nothing wrong with installing a bunch of distros.

---

### Post by benerivo on 2007-10-21
It's difficult to know what's gone wrong, but it must be something involving the installation of fedora. To recover your system, you could try...

A. installing fedora again on sda5
B. Installing ubuntu on sda5, to dual boot ubuntu

---

