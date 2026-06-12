---
title: "how to share folders on a mounted drive"
date: 2013-09-30
forum: General Help
---

### Post by john.errington on 2013-09-30
I'm running Ubuntu 12.04 on a laptop. It has a "data" partition (NTFS - windows xp) that is auto mounted at start-up. 

I want to share folders (eg "My Music") in this partition on my home network (windows). However it tells me I am not the owner. 

I have found "data" at /media/data and the sub-folders are there. How can I share them on the network?  Help please?

---

### Post by Morbius1 on 2013-09-30
There isn't enough information in your post and what there is seems contradictory so I'm going to make some WAGs:

Open nautilus as root:
```
gksu nautilus
```
And use the "Sharing Options" right click menu to share the folder.

If that doesn't resolve the issue then my guesses were wrong so I will need to know how you are automounting the ntfs partition. The output of the following command will tell me that:
```
cat /etc/fstab
```
And just in case the "you are not the owner" error is coming from the client rather than when you try to create the share I will need the output of these commands:
```
testparm -s
```
```
net usershare info --long
```

---

### Post by john.errington on 2013-10-01
gksu nautilus did the trick! 

However for future info, can I direct the output of the other commands to a file?

(FYI I'm a long-time windows user with a windows network; however when my laptop got a virus I removed te virus - and windows with it! 
I've been running ubuntu on it since 10.10 and now at 12.04. I use it for music - running audacity, banshee, hydrogen, lilypond, etc etc.
and when I upgrade I'll be staicking with UBUNTU!)

---

### Post by Morbius1 on 2013-10-01
> **john.errington said:**
> gksu nautilus did the trick! 

However for future info, can I direct the output of the other commands to a file?
Yes, example:
```
cat /etc/fstab > /home/john/Desktop/fstab.txt
```

---

