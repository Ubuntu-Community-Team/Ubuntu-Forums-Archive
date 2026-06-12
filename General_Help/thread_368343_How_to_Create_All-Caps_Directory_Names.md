---
title: "How to Create All-Caps Directory Names?"
date: 2007-02-23
forum: General Help
---

### Post by LaneLester on 2007-02-23
How can I get Ubuntu to create directory names with all capital letters? I type them in caps and always get small letters instead. I can't rename them the way I want them.

I had problems with a Web package because the archive contained "RFC822" and Ubuntu changed it to "rfc822."

Lane

---

### Post by kidders on 2007-02-23
Hi there,

Unless you're using a case insensitive filesystem (in which case, it won't matter anyhow, I suppose), you should have no trouble naming things in capitals... **mkdir "HELLO WORLD"** should work just fine.

---

### Post by LaneLester on 2007-02-23
Thanks for that. It led to a little more investigation, and it seems the problem is with FAT32 partitions. I created HELLO in my home directory, but when I copied it to a FAT32, it got changed to hello!

It's been my practice to keep my archives on a FAT32 to make them accessible to both Linux and Windows (head hanging in shame).

Lane

---

### Post by kidders on 2007-02-23
Ahh. As you may know, FAT32 is case insensitive. Having said that, it is (technically) possible to force Linux to treat it in a case *sensitive* manner. (You should check your dmesg for messages about case sensitivity.)

> head hanging in shameTut tut. Hehe.

---

### Post by lots on 2007-02-23
You could make your file system EXT3, and install the EXT3 driver on windows....

---

