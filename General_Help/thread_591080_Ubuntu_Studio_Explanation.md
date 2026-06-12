---
title: "Ubuntu Studio Explanation"
date: 2007-10-25
forum: General Help
---

### Post by jshurst on 2007-10-25
I am interested in doing some audio editing (using Ardour, Hydrogen, etc) which I currently have on Ubuntu Gutsy.  I am wondering if I should switch to Studio though.  I have heard some talk that Studio includes a low-latency kernel which should help with recording music, but I don't know why that is.

I guess my question is could someone tell me what a low-latency kernel is and the benefits of having it?  If it is included with Ubuntu Studio do I have to tell Grub to boot to this kernel, or is it simply the default one?

Thanks,

J

---

### Post by por100pre1 on 2007-10-25
Just try it yourself:

```
sudo aptitude install linux-rt
```

You'll have another kernel to choose from the grub menu.

---

### Post by jshurst on 2007-10-25
Thanks.  I wanted to reinstall Gutsy anyway, so I'm just going to try the Studio fresh install.  Also, I found that it includes the real-time kernel by default in Gutsy so perhaps that will make a difference and hopefully eliminate some of the xruns I was getting when running Ardour (although I probably should have disabled Compiz too ;-)

Thanks,

J

---

