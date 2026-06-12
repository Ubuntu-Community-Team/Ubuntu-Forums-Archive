---
title: "Compile nvdia driver on a custom kernel? (ubuntu 7.04)"
date: 2007-10-21
forum: General Help
---

### Post by worc on 2007-10-21
[http://ubuntuforums.org/showthread.php?t=584431](http://ubuntuforums.org/showthread.php?t=584431)

Can someone help me out?

I'm sorry the ubuntu version is 7.10 in this case. I write it wrong in the title.

---

### Post by DagMan on 2007-10-22
Hi,
it's easy enough but not with the ubuntu package, instead downloading a driver from the nividia website and letting it install.
to start out, uninstall the old driver and then install a compiler like this.
```
sudo apt-get install build-essential
```

Just download the driver version you want, make sure you get the one for 32 bit or 64 bit OS.
I have a 32 bit computer so I use the the Linux IA32 package 100.14.19  from the website [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) but click on archive to see older version if you think your card isn't supported. Mine is as 7300 go

Copy the driver to your home directory then switch over to a cli and kill the graphics by hitting ctrl-alt-f1, signing in, then
```
sudo /etc/init.d/gdm stop
```
you should be in the same directory as the driver, if not go there. then do this
```
sudo sh NVIDIA*run
```
and follow the questions.
I let it update my xorg.conf for me, which is the last thing it asks you if you want to allow.
then 
```
sudo /etc/init.d/gdm start
```
to restart graphics.

---

### Post by worc on 2007-10-26
Actually things is not that "easy". 
I found out that nvidia official driver v9755 does not work that way while v100.14.19 does. 9755 used to work in Feisty. Refer to the link in my original post for details.

Anyway, thank you for the reply.

---

