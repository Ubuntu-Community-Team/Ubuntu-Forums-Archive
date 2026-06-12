---
title: "Locked out of user account, no desktop, no terminal, no permissions"
date: 2013-03-05
forum: General Help
---

### Post by Luxx on 2013-03-05
I got it. After going through everything  I could find trying to locate .ICEauthority and change permissions, etc. I finally decided to try the simplest solution even though I wasn't sure that was the problem. GUI was only mostly gone with permissions errors.

At login screen I hit Ctrl+Alt+F2 and reinstalled ubuntu-desktop. 

sudo apt-get --reinstall install ubuntu-desktop

I have no idea how I lost it, but I think it may have been the first boot after an upgrade. I have lost my desktop every time I have upgraded Ubuntu regardless of my architecture at the time.

I don't know if reinstalling the desktop was a fix by itself or if the combination of changing ownership and reinstalling did the trick, but it's fine now.

---

### Post by Luxx on 2013-03-09
How do I mark this as solved?

---

### Post by nonamedotc on 2013-03-09
Try the thread tools option on the right side just below the thread title.

---

### Post by claracc on 2013-03-10
> **Luxx said:**
> How do I mark this as solved?

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

