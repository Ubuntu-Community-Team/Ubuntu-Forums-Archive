---
title: "a few questions to get me started"
date: 2007-03-23
forum: General Help
---

### Post by macm10 on 2007-03-23
hello, i just need to know how to do a few things.

the first is how to install a realtek ACL880 Driver (high definition audio codec) 

the second thing is that im having problems installing cross over office (i have to get iTunes running...if you know of a better way please tell me)

i get the following message from the installer:
```
The '/home/<mylastname>' directory does not belong to you.
Point $HOME to your home directory and try again.

```

And lasty does anyone know of a program (other than kwifi) that will let me connect to my wireless network and not have to go into the network settings every time i start my pc....

i know this is alot,
thanks

edit: for the audio i have a volume slider on the side of my laptop, is there any way to get this working?

---

### Post by devnulljp on 2007-03-23
> **macm10 said:**
> the first is mount one of my partitions
/dev/sda2 (harddrive)
depending on the filesystem, something like:
```
mount -t <filesystem type> /dev/sda2 /some/mount/point
```
where <filesystem type> is one of ext3|vfat|ext2 etc. 
There are other options depending what you want to do....try 
```
man mount 
```
> **macm10 said:**
> the third thing is that im having problems installing cross over office (i have to get iTunes running...if you know of a better way please tell me)
crossover is pretty straightforward
Did you look here [http://www.codeweavers.com/support/docs/crossover-standard/install](http://www.codeweavers.com/support/docs/crossover-standard/install)
Something like:
```
sh install-crossover-<version>.sh
```
I installed in private user mode, so it went into ~/.cxoffice
v6 is working great on Kubuntu 6.06
From your error message though, I guess you did something as root so our home directory belongs to root maybe....try 
```
ls -l /home/
```
If the output doesn't look like this (obviously where username is your username):
```
drwxr-xr-x 96 username username <other stuff, date, time etc.> username
```
but instead looks like this
```
drwxr-xr-x 96 root root <other stuff, date, time etc.> username
```
You need to do
```
sudo chown -R username:username /home/username
```
That will reset the permissions to your username
> **macm10 said:**
> And lasty does anyone know of a program (other than kwifi) that will let me connect to my wireless network and not have to go into the network settings every time i start my pc....
I use wlassistant, and it retains settings between boots. It's in the repositories.
> **macm10 said:**
> edit: for the audio i have a volume slider on the side of my laptop, is there any way to get this working?
Depends on the model...my thinkpad is pretty well supported, I think Sony Vaio too, maybe others.
(haven't a clue about No. 2 though....

---

