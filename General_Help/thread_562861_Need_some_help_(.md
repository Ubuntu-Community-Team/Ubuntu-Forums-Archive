---
title: "Need some help :("
date: 2007-09-29
forum: General Help
---

### Post by Suchthefool on 2007-09-29
ive been using ubuntu (feisty fawn) now for a month and its worked perfectly after a few hiccups but now very often itll stop working after a couple of hours of use. the programs which are already open will time out when connected to the internet and when i try and open another program it just wont open. not even the terminal :(

can anyone tell me how to fix this?

any help will be much appreciated
xx

---

### Post by SeanTater on 2007-09-29
If you computer is rather old, you might not have enough memory. I usually use Ksysguard to show me how much of my memory is being used, and I think there is Gnome System Monitor or something of the sort to do the same in Gnome.

---

### Post by Suchthefool on 2007-09-29
yer bang on. thanks for that. will get some more memory :)

---

### Post by Cappy on 2007-09-29
Look in your system log which is at System-->Administration-->System Log and see if you are getting any kind of errors.

Do you have a swap partition?

---

### Post by Suchthefool on 2007-09-29
im receiving a couple of errors but i have no clue what it means. and i dont think they're very major but im not sure im so new to linux :s

and whats a swap partition?

---

### Post by tgalati4 on 2007-09-29
A swap partition is a slice of disk that is used to store memory overflow.

Normally, during a Linux installation, you create a partition that is 2-3 times the size of your RAM.  This allows the operating system to "swap" memory to hard disk when memory is low.  I think Feisty creates its own internal swap file.  Older versions of Ubuntu used a static swap file (called /swap).  You can create a manual swap file as follows:

1)  Create a disk partition of reasonable size (1-3 GB).  Don't clobber your other data, you should have some experience with the partitioner to do this.

2.)  >sudo mkswap /dev/sda4  (assuming your swap partition is on the 4th disk partition)

3.)  >sudo swapon /dev/sda4

4)  >df -h       (to verify)

Now when your system runs out of RAM, it will gracefully start dumping pages of memory out to disk on your swap file.  This can slow the computer down quite a bit.  Feisty can use at least 256 MB of RAM.  512 MB or 1 GB is better.

---

### Post by Suchthefool on 2007-10-02
right i already have a swap partition of 3gb and im running on 512kb of ram and it still stops working. sometimes really soon after boot up. 

any ideas?

---

### Post by wrathkeg on 2007-10-02
Are you connected to a wireless network?  I used to have similar problems to you (slow, unresponsive, hanging etc) and when I stopped using the wireless adapter (USB in my case) the problems disappeared.  So if you are connecting to a wireless network, you might try disabling it and see if that helps.
WK

---

### Post by Suchthefool on 2007-10-02
yea im using a wireless network. i have to use it though :(. is there anyway around it?

---

### Post by wrathkeg on 2007-10-03
Well, yes and no (for me at least). 

I was using a wireless adapter on a desktop PC as there wasn't a telephone socket in the same room as the computer. I bought a very long ethernet cable to run from the dekstop PC to the hub in the other room, and my problems went away. So, I installed a telephone socket in the back room to avoid tripping over the long cables :)

I would try disabling the wireless network temporarily and see if that improves things: if things don't improve for you, the problems don't lie in that area anyway, and you don't need to think about changing your network setup. I can only tell you what worked for me, not what is causing your problems.

WK

---

