---
title: "Do not have privileges to mount drive?!?"
date: 2008-04-15
forum: General Help
---

### Post by Zurtex on 2008-04-15
I'm attempting to recover some files from a corrupted Windows hard drive.

I was able to view the files fine beforehand, but then switched around IDE priorities (as it was causing havok with my mobo). However it now says something about it being an active Windows drive and I have to force it, it gives me 2 ways of doing this. 1 is through the terminal and it says I need to be root to use the mount command. the other is in /etc/fstab and changing mounting options, which I attempted but it just told me I didn't have privileges. 

I don't understand, I've only made 1 user account "Stew", how do I access this "root"?

---

### Post by fguilhon on 2008-04-15
You can have root access with the **sudo** command. Just prefix any command you want to run with root access with sudo, for example:
```
sudo mount
```

---

