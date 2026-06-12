---
title: "Where Does GRUB Really Go?"
date: 2007-12-13
forum: General Help
---

### Post by oeolycus on 2007-12-13
I'm having trouble conceptualizing where GRUB exists. I thought it was in the MBR, but some of the files are in /boot I've found. I discovered this the hard way. I had an XP/Ubuntu dual boot, but I decided to restart. I made 3 new partitions where the old Ubuntu partition was in preparation to reinstall Ubuntu, Arch, and other distros I wanted to test. Perhaps I'm not ready for Arch as this was a newbie mistake. But I prefer to learn by breaking...

Here's the order of my partitions:

```
Before:
[--MBR--------------XP-------------------][------------------Ubuntu---------------]

After:
[--MBR---------------XP------------------][--ext3--][--ext3--][--ext3--][--swap--]
```

I thought GRUB would remain intact, and I was half right, except that it doesn't have the config files it needs to boot past GRUB error 17. I'm trying to restore that right now, and my question is:

**Is there a way to restore GRUB without reinstalling Ubuntu?**

EDIT: as an extension to that question, what's the best way to keep an intact GRUB whilst I'm flipping distros? I can't fit a /boot partition in front of the XP partition anymore clearly...

EDIT: my guess is this is not possible. With a LiveCD in the grub shell, find /boot/grub/stage1 returns "File not found."

---

### Post by taurus on 2007-12-13
[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles)

---

