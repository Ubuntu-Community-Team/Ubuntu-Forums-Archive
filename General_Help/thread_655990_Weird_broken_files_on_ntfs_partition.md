---
title: "Weird broken files on ntfs partition"
date: 2008-01-02
forum: General Help
---

### Post by Excalibre on 2008-01-02
I had a bad crash while running aMule (on Gutsy-64) and a bunch of its temp files got corrupted. They're on an NTFS partition. Now when I try to see what's in the directory from the terminal, I get an "input/output error"; when I try to look in Nautilus, it displays "unknown" for their size, modification date, type, etc. Obviously these files got completely broken when the thing crashed. How do I get rid of these broken files now? I can't delete them, I just get an "input/output error". How bad is this? What should I do to repair it? I have Windows XP installed if there's not a Linux program to deal with it (given it's not a file system normally used on Linux) so if anyone knows a tool for Windows or Linux to fix it, I'd be grateful.

Thanks in advance!

---

### Post by ~LoKe on 2008-01-02
Hm...why do you have Ubuntu applications running on an NTFS partition?

Anyways...you can use the terminal to resolve this.

Open it up, then cd to the directory.  Since I don't know where your files are located I can't tell you the exact steps.  Could you tell me the full path?

---

### Post by Excalibre on 2008-01-02
I'm not sure why you'd need the full path for this. Anyhow, it's a moot point, since it appears Linux doesn't have much in the way of tools to deal with NTFS issues, so I started up WinXP and chkdsk seems to have fixed everything.

---

