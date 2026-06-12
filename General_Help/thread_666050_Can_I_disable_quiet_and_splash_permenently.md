---
title: "Can I disable quiet and splash permenently?"
date: 2008-01-12
forum: General Help
---

### Post by some.hacker on 2008-01-12
I am the kind of person that wants to see what is going on at boot every time that I boot my computer. As a result, I do not want either the quiet or splash options enabled at boot time. I know how to remove it from my menu.lst, but the problem is that every time I update my kernel, it comes back. Is there a way that I can remove these options not only from this kernel version, but ensure it does not come back for future kernel versions?

---

### Post by dcstar on 2008-01-12
> **some.hacker said:**
> I am the kind of person that wants to see what is going on at boot every time that I boot my computer. As a result, I do not want either the quiet or splash options enabled at boot time. I know how to remove it from my menu.lst, but the problem is that every time I update my kernel, it comes back. Is there a way that I can remove these options not only from this kernel version, but ensure it does not come back for future kernel versions?

There is a section in the menu.lst file with default options, change that.

---

### Post by ~LoKe on 2008-01-12
```
gksu gedit /boot/grub/menu.lst
```

Look for the line that goes:
> # defoptions = ro quiet splash
Remove "quiet splash".

Then scroll down a bit to your kernel lines and remove it from that, too.

---

### Post by some.hacker on 2008-01-13
a-HA! Thank you guys very, very much :)

---

### Post by Spydr4590 on 2008-01-14
What does quiet do without splash?

---

### Post by druhboruch on 2008-01-14
You could also:
```
sudo apt-get remove usplash
```
```
sudo apt-get remove usplash-theme-ubuntu
```

---

### Post by Spydr4590 on 2008-01-14
Nm, I figured out what quiet does :)

---

