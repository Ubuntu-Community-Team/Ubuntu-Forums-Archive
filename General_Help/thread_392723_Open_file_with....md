---
title: "Open file with..."
date: 2007-03-24
forum: General Help
---

### Post by Timtro on 2007-03-24
Hi all,

I hope this is a simple problem. I'm using Gnome. When I click a '.dat' file, which I use to mean 'data' (its ASCII text), I want it to be opened with gVim. Instead, I get the message:
```

The filename "Si100_oxide_corr.dat" indicates that this file is of type "MPEG video". The contents of the file indicate that the file is of type "plain text document". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "plain text document", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 

```

Of course, I can 'open with', but this is a pain in the butt. I don't want to rename my files, and modify my programs that make them. How do I control what Gnome things files are supposed to be?

Thanks!

Thanks!

---

### Post by 23meg on 2007-03-24
Right click the file, click "Properties", go to the "Open With" tab and choose the application you want to associate with the file.

---

### Post by Timtro on 2007-03-25
> **23meg said:**
> Right click the file, click "Properties", go to the "Open With" tab and choose the application you want to associate with the file.

I'm well aware of this, but it doesn't work. The qualm I have is that Gnome notices the difference between the file extension, and the innards of the file. Thus, in order to open the file, I must 'right click > open with' every time I wish to open the file! I wish to be able to double click. Double clicking invariably leads to the error above.

---

### Post by Timtro on 2007-03-26
*bump*

I have a feeling people are not reading my problem correctly, and passing it over. Its not the problem the gentleman above thought I was asking.

I'm sorry to be persistent, but this is really starting to piss me off. In Nautalis, when I highlight a file, it moves immediately when it figures out what type of file it is (I arrange by type). This is making it quite irritating to manage files in numbers.

Surely there is a simple way to fix this!

---

### Post by Timtro on 2007-03-26
Never mind, I figured it out myself.

For those in the future, here is what I did.

```


locate gnome-vfs.mime


```

found it in /usr/share/

```


sudo gvim /usr/share/gnome-vfs.mime


```

I'm a Vim kinda guy, so if you don't have it, perhaps gedit, emacs, pico, etc. gedit is default in Ubuntu. Anyhow, I moved the entry 'dat' from MPEG to text/plain.

I haven't tested this fix, but if that is indeed the file where gnome keeps its MIME info, it should work.

---

### Post by Timtro on 2007-03-26
That SOOOO didn't work. I'll test before I post next time.

Any other ideas?

---

### Post by Timtro on 2007-03-28
Okay, well, thanks for nothing everyone. I assume that nobody is reading my most, and assuming that I simply want to know how to manipulate which program opens a file. Well, I suppose that somewhat my fault. I named the post incorrectly.

I have reposted the problem here:

[http://www.ubuntuforums.org/showthread.php?t=395686](http://www.ubuntuforums.org/showthread.php?t=395686)

---

