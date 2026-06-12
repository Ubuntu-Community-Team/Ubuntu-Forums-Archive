---
title: "iPod is not being detected"
date: 2005-08-23
forum: General Help
---

### Post by jc3835 on 2005-08-23
Hi all.
4th gen iPod photo...
I've followed the Wiki and the gtkpod.org instructions on how to get an iPod connected to Ubuntu and all.
I get nothing! I get nothing in dmesg, nothing mounts... just doesn't seem to show up anywhere.
I'm completely stumped at this point... any suggestions?  ](*,) 

It is connecting, it starts to charge when I plug it into USB.

Thanks for the help.

JC

---

### Post by astoltz on 2005-08-23
Hmmm, that's wierd.  Just a few things off the top of my head, no particular order.

[list]
[*]Try restarting hotplug:  sudo /etc/init.d/dbus restart
[*]Try different USB ports
[*]do you have a Mac or Windows machine to try it on?
[*]Re-boot?
[*]compare the contents of /dev/* before and after plugging in 
[/list]

---

### Post by jc3835 on 2005-08-23
It's a friend's iPod actually, and he was having issues with it in Windows, so I thought I'd give it a shot under Linux.
I've tried it on 2 Ubuntu machines, same results:
```
'/mnt/ipod/iPod_Control/iTunes/iTunesDB' does not exist. Import aborted.
```
I tried everything you mentioned you far.

I'm beginning to think the issue is with is iPod after all.

Thanks for the advice though.

---

### Post by wellery on 2005-08-23
[QUOTE=jc3835]It's a friend's iPod actually, and he was having issues with it in Windows, so I thought I'd give it a shot under Linux.
I've tried it on 2 Ubuntu machines, same results:
```
'/mnt/ipod/iPod_Control/iTunes/iTunesDB' does not exist. Import aborted.
```
I tried everything you mentioned you far.

I'm beginning to think the issue is with is iPod after all.

Thanks for the advice though.[/QUOTE]

Maybe try this after the device is attached and check the output:

```
dmesg 
```

---

