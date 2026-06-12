---
title: "Getting LIRC working on a ThinkPad"
date: 2008-07-09
forum: General Help
---

### Post by 50words on 2008-07-09
I am trying to get LIRC working on my ThinkPad so that I can use an Apple Remote to run slideshow presentations.

I am stuck on getting LIRC to recognize my infrared receiver so that I can use it.

I did enable the infrared receiver in the BIOS setup, and I have tried to decipher this page on ThinkWiki, but I have not been able to make any use of it: [http://www.thinkwiki.org/wiki/How_to_make_use_of_IrDA](http://www.thinkwiki.org/wiki/How_to_make_use_of_IrDA)

Any ideas?

---

### Post by spiderbatdad on 2008-07-09
You could be more specific as to how you have "not been able to make use" of the tutorial.

Do you understand:```
Edit /etc/modprobe.conf and add the following lines

alias tty-ldisc-11 irtty-sir
alias char-major-161 ircomm-tty

```

That could be confusing, as there is no /etc/modprobe.conf. Instead look to edit /etc/modprobe.d/aliases

This section:```
To use it, run # irattach /dev/ttyS1 -s; modprobe ircomm-tty
```
Might be confusing also. Instead try ```
sudo irattach /dev/ttyS1 -s & sudo modprobe ircomm-tty
```

You will still have to set the dongle and setserial, but know you know which file to edit...hopefully. To edit system files, try ```
 gksu gedit /etc/modprobe.d/aliases 
```

---

### Post by 50words on 2008-07-09
Well, it is a generic tutorial with lots of "if you want to do this, do this, but if you want to do this other thing, do this other thing," where all instances of "this" are things that make no sense to me.

A step-by-step guide would be awesome, but I realize there may not be that many other people looking to do this.

---

