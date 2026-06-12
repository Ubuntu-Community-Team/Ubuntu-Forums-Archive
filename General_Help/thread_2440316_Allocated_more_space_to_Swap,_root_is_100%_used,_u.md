---
title: "Allocated more space to Swap, root is 100% used, ubuntu won't start"
date: 2020-04-08
forum: General Help
---

### Post by datagueule on 2020-04-08
Hi all,

I did a mistake! 
I tried to allocate 15 G to my swap with this[ tutorial ]("https://linuxize.com/post/how-to-add-swap-space-on-ubuntu-18-04/")


```
sudo fallocate -l 15G /swapfile
```

this command actually took all of my size from my root```
 /
``` which on my partition is ```
/dev/sdb2
```

I just wanted to took some of my space from ```
 /home
``` ```
/dev/sdb3
``` and add it to the swap 

but now, my root is totally full and ubuntu won t even start. I tried to use "clean" on the recovery mode, but it was not enough

Anybody has an advice?

thank you! :D

---

### Post by HermanAB on 2020-04-08
Boot with an install disk (don't install obviously). Mount the HDD.  Change the size of the swapfile.  Reboot.

---

### Post by yancek on 2020-04-08
Before creating the swap file, you should have determined how much free space was available on the various (including /) partitions which you could have done with the df -h command.  This would have saved you the trouble you are currently having.   I expect the problem is caused by the command you quote to create the swap shown below, the /swapfile means you created it in the / (root) of the filesystem rather than where you wanted it.  TAke a look at the link posted below beginning with post #4 which shows how to use a different path to create the swapfile.

> sudo fallocate -l 15G /swapfile

[https://www.linuxquestions.org/questions/linux-newbie-8/swap-file-on-external-hard-drive-connected-to-raspberry-pi-3-a-4175611225/](https://www.linuxquestions.org/questions/linux-newbie-8/swap-file-on-external-hard-drive-connected-to-raspberry-pi-3-a-4175611225/)

---

### Post by TheFu on 2020-04-08
15G is really, really, large for swap.  4.1G is almost always the "correct" answer for swap these days for any desktop system.  There's a thread here started about 2 weeks ago about swap.  Has all sorts of information and links for why swap exists and different sizes with concrete examples.

---

### Post by datagueule on 2020-04-09
Hi all, thanks for your answers! 
so How could I do that? I connected  a USB key and tried to mount the sdb2 with the terminal.. it didn t  worked and says "can't find in /etc/fstab"
and what command could I  use to un-allocate the space I gave to /swapfile? I tried to search on  google but couldn't really find the opposite of fallocate. And I m  afraid if I just delete it, it would **** up everything.

thank you!

---

