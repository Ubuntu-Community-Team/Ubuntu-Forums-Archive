---
title: "[SOLVED] [SOLVED] Evolution, startup segmentation fault"
date: 2008-03-27
forum: General Help
---

### Post by Ux64 on 2008-03-27
```

~$ evolution
evolution-shell-Message: Killing old version of evolution-data-server...
Loading Bogofilter as the default junk plugin
** (evolution:7786): DEBUG: mailto URL command: evolution %s
** (evolution:7786): DEBUG: mailto URL program: evolution
Segmentation fault

```

I clicked one link in email. Evolution crashed, and now I can't even start it. It'll recrash in less than 100 ms.

How I can fix this problem?

- Thank you!

I tried to google and use search with this specific error message and I didn't get any meaningful results.

[Here]("http://forums.gentoo.org/viewtopic-p-4731035.html?sid=08a7e57b2bd2f2f7699a839d742cee8d") they instruct to "emerge libbonobo gnome-python" but emerge is unknown command.

- Thanks!

... Actually after looking for a while and thinking symptoms ...

I found the reason. 

**Solution**

It's the preview for HTML email. If I run evolution with parameter **--disable-preview** I can get it running. So no help needed. But I'm just letting you know that some html email can cause havoc.

---

### Post by IcemanV9 on 2008-03-27
You may want to see if bogofilter is installed. And, emerge is the command for Gentoo linux to install a package. So, for Ubuntu linux, you'll want to use "apt-get or aptitude install" instead of emerge.
```
sudo aptitude install libbonobo2 python-gnome2
```

---

### Post by dcstar on 2008-03-27
> **Ux64 said:**
> 
.......
**Solution**

It's the preview for HTML email. If I run evolution with parameter **--disable-preview** I can get it running. So no help needed. But I'm just letting you know that some html email can cause havoc.

HTML e-mail is an un-standardised mess, every bloody e-mail client does things differently and too many people use the Microsoft "way" which stuffs up other clients all too often.

Someone should take out HTML e-mail and shoot it - twice in case the first one misses!!    :roll:

---

