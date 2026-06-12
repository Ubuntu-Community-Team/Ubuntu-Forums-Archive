---
title: "apt not recognizing optical drives"
date: 2007-05-31
forum: General Help
---

### Post by muimi07 on 2007-05-31
NOTE: I'm a complete newbie when it comes to Linux so please forgive me if this is totally obvious. In my other life, I'm a Windows admin who uses a Mac when not in the office :P

This is an odd (to me) problem that I've been running into. I'm running Feisty Fawn 7.04 and after I run any necessary updates, either via Synaptic or simply

```
sudo apt-get update
```

it's like apt won't recognize /cdrom/. 

[IMG]http://farm1.static.flickr.com/220/523636534_89670cba88.jpg[/IMG] (Full sized version [here]("http://farm1.static.flickr.com/220/523636534_ad5c5f6c1d_o.png"))

My machine has two optical drives: a CD-RW and a CD/DVD drive. Before updating, it would mount the disc in my CD/DVD drive as my /cdrom/ Now, however, as you can see from the screenshot, it mounts as /media/discname/

I can use any disc just fine in either drive but the fact that apt won't recognize the disc since it's not mounted as /cdrom/ is driving me nuts. I can't install things like nfs or smb because of this. Help?

---

### Post by muimi07 on 2007-05-31
Bah, resolved it. Since [this]("http://ubuntuforums.org/showthread.php?t=164965") post was similar, I just commented out whatever referenced deb cdrom.

I'm curious though as to why the updates changed the mount point? :KS

---

