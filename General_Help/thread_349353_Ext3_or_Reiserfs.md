---
title: "Ext3 or Reiserfs?"
date: 2007-01-30
forum: General Help
---

### Post by bongoard on 2007-01-30
Hello,

1st I like to inform you, that i've been using ubuntu since 4.10 until now 6.10. 
Moving back and forth between Windows XP and Linux, I'm also using another distro, RedHat, Suse, and even BSD flavor (FreeBSD). The longest I'm sticking with ubuntu is when it comes to 5.04 and 5.10 which is the best release in my opinion.
Recently I'm trying SUSE Linux enterprise Desktop 10, right before I give Ubuntu Dapper a try. 
I found that SLED 10 is faster and snappier than Ubuntu Dapper.
Knowing that SLED format the filesystem with reiserfs by default, I came to a temporary conclusion that maybe reiserfs is faster than ext3, and so I install Ubuntu Edgy with reiserfs, and then I give it a try and It even faster than SLED 10! (perhaps it is because the Gnome version). 
Sure it fast, until I tried to use Firefox, launch nautilus, and using Netbeans or Eclipse, it began using swap like a pig... (yes, I'm lacking of memory...)
Desperate with that situation, I decided to try ext3, Lo and behold! ext3 is faster (and snappier) than reiserfs?!
So here's my question, which one is faster? which one you guys recomend for : Java and web programming (and application), multimedia application, database application, general application, etc.; 
Reiserfs or Ext3 on Ubuntu with Gnome System? (don't mention kubuntu or xubuntu, since I'm going to use Gnome).

---

### Post by Jussi Kukkonen on 2007-01-30
If your machine lacks memory, then the filesystem choice is going to be a very, very minor problem -- I doubt the differences are really noticeable in normal use. On the other hand, if you *know* that you spend a lot of time waiting fpr disk IO, read some file system comparison articles. The web is full of them.

Novell is moving from reiserFS to ext3 too, by the way.

---

### Post by larini on 2007-01-31
I installed ubuntu in my 250GB HD using reiserfs, it taked about 55 seconds to boot.
I move to ext3, and now it takes 26 seconds to boot.

---

### Post by Jussi Kukkonen on 2007-01-31
larini, that's because the "achilles' heel" of reiserfs is the time it takes to mount/umount...

---

