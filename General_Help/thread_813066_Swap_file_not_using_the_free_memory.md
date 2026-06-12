---
title: "Swap file not using the free memory"
date: 2008-05-30
forum: General Help
---

### Post by Mr dirt on 2008-05-30
I found an article here that stated how to make a swap file/partition. I used gparted to create the part after I had installed ubuntu and tried to merge the file. Everything seemed to go ok but for some reason the swap file isnt using any of its resources, here is what it says.
```

            total       used       free     shared    buffers     cached
Mem:        515096     502732      12364          0      13996     257972
-/+ buffers/cache:     230764     284332
Swap:      4173200          0    4173200

```
How can I get it to start accessing it?
This is the page I got the info from.

[https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq")

---

### Post by cubeist on 2008-05-30
I think the command you are looking for is called *swapon*

In a terminal type *man swapon*

read through that and then to activate swap the command is probably something like:
```
sudo swapon /dev/devicelocation
```


Edit:
Actually, I am not familiar with swapon/swapoff, forget that for now.  I found a link which should provide better info for setting up a swap partition:
[http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/](http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/)

---

### Post by Mr dirt on 2008-05-30
Thanks man I have found out the problem and it is working alright. I didnt use enough memory intensive programs and The swap didnt need to activate.

---

### Post by cubeist on 2008-05-30
Your welcome. not much of a reply though :)

One thing I do know, is if you want to change how frequently your computer access swap you can change your swappiness.

In your /etc/sysctl.conf file you can add a line like:
```
vm.swappiness=0
```
or
```
vm.swappiness=100
```

The default is 60, where 0 is almost never and 100 is more frequently.  Some people have reported a speedup from reducing swappiness, but I find the default of 60 is aok.

ps.  Don't forget to backup you sysctl before editing
```
sudo cp /etc/sysctl.conf /etc/sysctl.conf.backup
```

---

