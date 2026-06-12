---
title: "Opera 9.50 / Firefox 3.0 Fonts"
date: 2008-07-01
forum: General Help
---

### Post by sjmorgan on 2008-07-01
As you can see from [this]("http://img386.imageshack.us/img386/2133/fontslv8.png") screenshot, the same fonts look quite different rendered in Opera 9.50 than they do in Firefox 3.0. Does anyone know how to achieve the same look in Firefox? I'm assuming both programs use FreeType.

Thanks.

---

### Post by sjmorgan on 2008-07-01
No sooner did I post my question than I had a brain-wave and found the answer out for myself.

Opera 9.50 seems to enable the byte code interpreter by default which causes fonts to look different. You can do this for all other programs by symlinking /etc/fonts/conf.avail/10-autohint.conf into /etc/fonts/conf.d/ (if you want to enable the change for everyone) or just copying 10-autohint.conf to ~/.fonts.conf.

---

### Post by HandyAndy on 2008-07-02
Thanks for that tip.

I've tried all sorts to get my Firefox/Swiftweasel 3 fonts looking good.

That made a big improvement.

---

### Post by heyup on 2008-12-06
> **sjmorgan said:**
> No sooner did I post my question than I had a brain-wave and found the answer out for myself.

Opera 9.50 seems to enable the byte code interpreter by default which causes fonts to look different. You can do this for all other programs by symlinking /etc/fonts/conf.avail/10-autohint.conf into /etc/fonts/conf.d/ (if you want to enable the change for everyone) or just copying 10-autohint.conf to ~/.fonts.conf.

Can the OP or someone else explain to a novice like me how to do this.

I installed msttcorefonts but find that the text in some webpages appears very small and not so small in others. Opera doesn't seem to set the text at the same default font size.

I'm using Opera 6.27 in Ubuntu 8.04.

---

### Post by vishzilla on 2008-12-06
Thanks for the tip. I guess autohinting was enabled in previous versions of Ubuntu. Wonder why they disabled it.

---

### Post by vishzilla on 2008-12-06
> **heyup said:**
> Can the OP or someone else explain to a novice like me how to do this.

I installed msttcorefonts but find that the text in some webpages appears very small and not so small in others. Opera doesn't seem to set the text at the same default font size.

I'm using Opera 6.27 in Ubuntu 8.04.

Run this command in your terminal

```
cp /etc/fonts/conf.avail/10-autohint.conf .fonts.conf
```

---

### Post by heyup on 2008-12-06
> **vishzilla said:**
> Run this command in your terminal

```
cp /etc/fonts/conf.avail/10-autohint.conf .fonts.conf
```

That command will copy the file /10-autohint.conf into the file /fonts.conf

The alternative command suggested by sjmorgan is to symlink the file /etc/fonts/conf.avail/10-autohint.conf with the folder /etc/fonts/conf.d/

What is the command to symlink? What's the difference between symlinking and copying?

---

### Post by heyup on 2008-12-14
I found the answer here:
[http://ubuntuforums.org/showthread.php?t=4456](http://ubuntuforums.org/showthread.php?t=4456)
[http://ubuntuforums.org/showpost.php?p=4049873&postcount=172](http://ubuntuforums.org/showpost.php?p=4049873&postcount=172)

> **pawitp said:**
> The preferred way to do this on gutsy is:
```
sudo ln -sf /etc/fonts/conf.avail/10-autohint.conf /etc/fonts/conf.d/
```

This might help others.

---

