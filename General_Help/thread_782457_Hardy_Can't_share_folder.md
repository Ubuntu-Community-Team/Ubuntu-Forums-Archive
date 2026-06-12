---
title: "Hardy: Can't share folder"
date: 2008-05-05
forum: General Help
---

### Post by nottrobin on 2008-05-05
Hiya.

I'm a bit new to Linux, although I've been working with Unix for quite a while.

I'm trying to share folders in Hardy Heron. I created a new folder on the desktop called "SharedFolder". I right clicked on it, clicked "Sharing options", ticked all three boxes and clicked "Modify share". A box pops up asking if I mind modifying permissions. I click "yes". Now it should be shared as "SharingFolder" on my computer.

So I navigate to smb://127.0.0.1 - and all I can see it 'print$'.

I'm sure I'm being rather stupid here, but I don't understand what I've done wrong?

Ta,
Robin.

---

### Post by nottrobin on 2008-05-05
Update:

I stumbled upon this post: [http://www.linuxforums.org/forum/ubuntu-help/118877-samba-hardy.html](http://www.linuxforums.org/forum/ubuntu-help/118877-samba-hardy.html).

I did what they did - that is, emptied my smb.conf and replaced it with a skeleton one, and it did work. Which shows that the error is in Ubuntu's handling of the smb.conf. However, I don't know enough about the samba configuration files to write my own complete one, so I would appreciate it if someone could suggest a way that I can coerce Ubuntu into doing it properly?

Ta,
Robin.

---

### Post by nottrobin on 2008-05-05
This is linked to this bug:
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/214556](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/214556)

---

### Post by nottrobin on 2008-05-05
The "Sharing options" still don't work, but I did manage to share folders properly through shares-admin (Alt+F2 -> 'shares-admin' -> run).

I ended up adding 'shares-admin' to the System->Administration menu.

---

