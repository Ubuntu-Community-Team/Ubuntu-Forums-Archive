---
title: "Can't boot windows 7 after accidentally unmount drive c on linux"
date: 2013-10-31
forum: General Help
---

### Post by ewejin17 on 2013-10-31
I accidentally unmount 240GB Filesystem (C drive) and now I can't boot windows :( I really need it back now as most of my stuff and work are all stored there.


Here's a screenshot of the error
[ATTACH=CONFIG]247407[/ATTACH]

Any help would be greatly appreciated

---

### Post by TheFu on 2013-10-31
Please run boot-info. See my signature for links.

---

### Post by ewejin17 on 2013-10-31
I'm sorry, I'm not a tech-savy person. I seriously have no idea what to do :((

---

### Post by ewejin17 on 2013-10-31
ok, i ran boot repair to obtain boot-info

here's the report:
[http://paste.ubuntu.com/6335204/](http://paste.ubuntu.com/6335204/)

---

### Post by ewejin17 on 2013-10-31
here's the report after the recommended repairs:
[http://paste.ubuntu.com/6335238/](http://paste.ubuntu.com/6335238/)

---

### Post by TheFu on 2013-10-31
Let me try to understand what has happened.
a) ran boot-info
then decided to run 
b) boot-repair

Boot repair did something and you can't boot either Windows or Linux now?  What is the current status of boot for both OSes?

Last - > 
ntfsfix /dev/sda1
Refusing to operate on read-write mounted device /dev/sda1.
is inside the latest boot-info.  It is unclear why this happened. How did you unmount the partition?  
Was Windows or Linux in standby or hibernate before starting?  The "swsuspend" partition is something I've never seen before in a report.

Sorry that I don't have any specific answer. Hopefully someone smarter will jump in and help.

---

### Post by Mark Phelps on 2013-10-31
My guess is that you (somehow) unmounted the Windows OS partition while it was hibernated -- but that's a guess.  Linux will refuse to mount an NTFS partition read/write if it suspects filesystem corruption.  Since Boot-repair can't mount it, I suspect that Linux can't fix it.

When Win7 worked, you could have made a repair CD for free -- from inside Win7 -- but now, you will have to purchase an image online to download and create a Win7 repair CD from the following link: [http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

If that CD doesn't repair your Win7 -- suggest you then go to the Win7 forums (sevenforums.com) and see what they suggest.

---

