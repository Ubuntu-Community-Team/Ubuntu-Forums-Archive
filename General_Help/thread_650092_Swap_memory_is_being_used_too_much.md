---
title: "Swap memory is being used too much"
date: 2007-12-25
forum: General Help
---

### Post by anyo409 on 2007-12-25
I have 4 GB of RAM memory & 20 GB of swap. Problem is that when I use too many programs at once, like Vmware, Firefox, OpenOffice and Google Earth .....  Ubuntu is using ½ RAM and ½ Swap and that makes my system a little slow. I have an AMD 5600 dual core, 64bit. 

Is there any way I can use only my RAM memory and not use swap at all. I am guessing Swap is slowing my system down & since I have plenty of RAM why use Swap memory ? I have attached a screen shot of system monitor for anyone to see what's going on with my system.

Any solution ? ....... can I deleted swap for good ? is it safe ?

Thanks in Advanced.

---

### Post by sc30317 on 2007-12-25
20GB swap is wayyyyyyyy too much.  With 4GB of memory, you most likely dont need any swap at all, unless you open like >100 windows at a time.

remove the swap, and see what happens!  You can always create a new swap partition with gparted

---

### Post by anyo409 on 2007-12-25
how can I remove the swap partition? and is it safe ? because I never shut down my system.

Is there a way I can may be keep the swap but mostly use my RAM memory ?

---

### Post by mikewhatever on 2007-12-25
> **anyo409 said:**
> how can I remove the swap partition? and is it safe ? because I never shut down my system.

Is there a way I can may be keep the swap but mostly use my RAM memory ?

I would not remove swap. You never know when you decide to put your computer to sleep or suspend to disk. However, resizing it to something more useful is a good idea.
To get to use more RAM, try these links: [http://ubuntuforums.org/showpost.php?p=1255511&postcount=43](http://ubuntuforums.org/showpost.php?p=1255511&postcount=43)
[http://thewebsbest.net/index.php?option=com_content&task=view&id=121&Itemid=30](http://thewebsbest.net/index.php?option=com_content&task=view&id=121&Itemid=30)

---

### Post by articpenguin on 2007-12-25
read this
[https://help.ubuntu.com/community/SwapFaq#head-b179a5c0d7df0ab7d0ea1d58caaa47c7a5f8ab0e]("https://help.ubuntu.com/community/SwapFaq#head-b179a5c0d7df0ab7d0ea1d58caaa47c7a5f8ab0e")

you change swap the priority if the swap such as using it as a last resort

---

### Post by anyo409 on 2007-12-25
how can I remove the swap all together ?

---

### Post by PinkFloyd102489 on 2007-12-25
I know it's already been posted, but I'll post it again with an edit.


Edit /etc/sysctl.conf and add this line to the end:

vm.swappiness=0

I know the previous one said 10, but 0 really cuts the usage down a lot. Im running 380MB RAM with 400MB swap and it helps.

---

### Post by kuja on 2007-12-26
> **anyo409 said:**
> how can I remove the swap all together ?

Pull up something like cfdisk or (g|q)parted **from a livecd** and delete the swap partition. Boom, swap will be gone.

---

