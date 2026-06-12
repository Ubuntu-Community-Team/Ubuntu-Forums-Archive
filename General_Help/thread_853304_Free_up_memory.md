---
title: "Free up memory"
date: 2008-07-08
forum: General Help
---

### Post by enchance on 2008-07-08
After running free -m I always find myself scrimping for memory. Is there an app/code which can help free memory?

---

### Post by apswartz on 2008-07-08
How much memory do you have? Just because free -m shows little free memory doesn't necessarily mean you are running out of memory. Linux is very efficient in its use of memory. Check out...

[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

---

### Post by mcduck on 2008-07-08
Are you looking at the "+/- buffers & cache"-line in the "free -m" output? Because that's the one that shows the real memory usage..

Linux will always use as much RAM as there's available, because if the memory is not used it's wasted.. ;) All memeory that isn't used by system or running applications is used as disk cache to speed up your system. If programs needs more RAM some cached data is simply dropped to free more space, so all memory used for buffers is still available for applications to use.

---

### Post by bodhi.zazen on 2008-07-08
First things first, Linux != Windows

This includes memory management.

Start by looking at these links :

[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

[http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?](http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?)

---

### Post by sayakb on 2008-07-08
```
sudo apt-get install htop
htop
```
It would specifically show used and buffered portions of memory.

---

### Post by apswartz on 2008-07-08
> **LinuxIsInnovation said:**
> ```
sudo apt-get install htop
htop
```
It would specifically show used and buffered portions of memory.

Oooooooh... sweet! No more top for me.

---

### Post by enchance on 2008-07-08
> **apswartz said:**
> Oooooooh... sweet! No more top for me.

This is great! Thanks for all your comments guys! It appears the only problem I have is I only have so much memory but still insist on running compiz. Nyahahaa!

---

### Post by NotebookCity on 2008-07-08
That's good advice.

---

### Post by enchance on 2008-07-09
> **NotebookCity said:**
> That's good advice.

Which advice are you referring to? :confused:

---

