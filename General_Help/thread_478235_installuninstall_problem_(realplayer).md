---
title: "install/uninstall problem (realplayer)"
date: 2007-06-19
forum: General Help
---

### Post by ineffigy on 2007-06-19
Hi!

I'm quite new to linux and ubuntu. I was installing Realplayer10gold.bin like this 
 
$ cd Desktop
$ chmod a+x RealPlayer10GOLD.bin
$ sudo ./RealPlayer10GOLD.bin

but in installation i specified wrong installation place. I specified just /usr/local/bin but i needed to specify /usr/local/bin/realplayer and now that bin folder is in big mess. So tell me please how to uninstall it in such situation.

---

### Post by Qu4k3R on 2007-06-19
I have the same problem. Is there any repository for realplayer?
Thanks

---

### Post by wpshooter on 2007-06-19
> **Qu4k3R said:**
> I have the same problem. Is there any repository for realplayer?
Thanks

Yes, I believe it is in one of the repositories, BUT my suggestion would be that you just google Realplayer for Linux and then download Realplayer directly from the Realplayer site.

---

### Post by mali2297 on 2007-06-19
@ineffigy:

Can't you run Realplayer? It shouldn't matter where you install it, symbolic links are created in /usr/bin anyhow. But if you want to remove the installed files, you can type:
```

$ sudo rm -r  /usr/local/bin/*

```
WARNING though, that will remove everything in the folder. It might be safer to move the content 
to some temporary folder and delete it later.

---

### Post by FuturePilot on 2007-06-19
It might be easier if you add this```
deb http://archive.canonical.com/ubuntu feisty-commercial main
```to your sources list then
```
sudo apt-get update
```
and ```
sudo apt-get install real-player
```

---

### Post by aghiadb on 2007-06-27
i just want to say thanx, i find it useful, and hope it'll work

bye

---

### Post by jtreach on 2007-07-05
the last entry should be ```
sudo apt-get install realplay
```

I got that by guessing different names! :)

---

### Post by DM was on fire! on 2007-07-05
If you update the Add/Remove Programs, there should be the Helix player (which is the Linux version of RealPlayer). :D But, since it's been figured out how to install it, never mind. ^^;;

---

