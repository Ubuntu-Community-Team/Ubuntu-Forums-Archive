---
title: "Installing programs on a second hd"
date: 2013-02-15
forum: General Help
---

### Post by R3dW00t on 2013-02-15
In a windows enviroment, i've always had my os on one disk, and all the programs that don't make a fuss about it,  installed on a second. 
In windows this is pretty much straight forward imho.

My question is, how to do this in Ubuntu?
I haven't tried it yet, since i don't want to mess up my current setup.
It's much safer to ask questions first...:P

---

### Post by Bufeu on 2013-02-15
You can't "choose" where to install programs on the same way in Linux. I once asked the same question too: [http://ubuntuforums.org/showthread.php?t=2032215](http://ubuntuforums.org/showthread.php?t=2032215).

---

### Post by sudodus on 2013-02-15
Most linux programs share the same libraries, they are linked dynamically (instead of statically which is typical in Windows). This means that the linux programs will be much smaller, so that the root partition need not be very big, and will not grow rapidly.

If you wish, you can separate /home from the root partition / by moving it to an own 'home' partition. This is an advantage, when you change to a new version of Ubuntu. Then you can simply keep the /home partition while you make a fresh install of the root partition, and you will keep settings and data stored for several application programs, for example bookmarks for Firefox and mails for Thunderbird.

---

### Post by R3dW00t on 2013-02-15
That's an option indeed. Moving my /home directory to another partition.
From what i've read from Bufeu's thread, there's some work involved ,but thats part of the fun, right?

First of all i'm going to try this on a virtual machine. 
Let's see where i'll end up.

Thx for the help!

---

### Post by sudodus on 2013-02-15
You are welcome and good luck :-)

---

### Post by Impavidus on 2013-02-15
Program binaries and data are not stored in the same directory. Those binaries aren't very big. The programs that need a lot of data can often be configured to find their data in a non-standard place, typically using environment variables or command line options. So if your /usr/share/games/whatever grows to contain too much data, you can probably move some to another partition, like on your second hd.

---

