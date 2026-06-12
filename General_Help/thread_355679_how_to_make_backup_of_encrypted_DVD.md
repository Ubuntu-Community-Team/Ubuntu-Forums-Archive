---
title: "how to make backup of encrypted DVD"
date: 2007-02-07
forum: General Help
---

### Post by fouadk on 2007-02-07
hey all

is there is a program like clonedvd that is used to make backup copies of original encrypted dvds coz i dont like to use the original DVD coz it will get scratched...

please help

Thanks in advance

---

### Post by heathenx on 2007-02-07
k9copy

---

### Post by ardchoille42 on 2007-02-07
I have been using xdvdshrink to shrink dual-layer DVD (DVD9) movies down to fit on a single-layer blank DVD (DVD5) and it works great.

[http://dvdshrink.sourceforge.net/](http://dvdshrink.sourceforge.net/)

You'll need some deps but the xdvdshrink installer checks for them and reports what you need before xdvdshrink can install. The deps are in the repos.

---

### Post by fouadk on 2007-02-08
thanks alot, i will try both k9copy and dvdshrink and see which one suits me better...

thanks alot

---

### Post by maxamillion on 2007-02-08
```
man dd
```

... in the terminal, read, enjoy :)

---

### Post by BLTicklemonster on 2007-03-27
> **ardchoille42 said:**
> I have been using xdvdshrink to shrink dual-layer DVD (DVD9) movies down to fit on a single-layer blank DVD (DVD5) and it works great.

[http://dvdshrink.sourceforge.net/](http://dvdshrink.sourceforge.net/)

You'll need some deps but the xdvdshrink installer checks for them and reports what you need before xdvdshrink can install. The deps are in the repos.

Using Feisty, having installed all three files from the above link, I get this:

```
bill@bill-desktop:~$ k3b
```



nothing happens.

Okay, so this, maybe:

```
bill@bill-desktop:~$ k3bsetup
QSettings::sync: filename is null/empty
```

---

### Post by stchman on 2007-04-02
> **fouadk said:**
> hey all

is there is a program like clonedvd that is used to make backup copies of original encrypted dvds coz i dont like to use the original DVD coz it will get scratched...

please help

Thanks in advance

Intsall k9copy.

sudo apt-get install k9copy

It does the exact same thing as DVDShrink.  Follow the steps on my webpage:

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

This will get CSS decryption up and going on Ubuntu.  After k9copy is done decrypting and compressing it will burn it to a DVD using k3b or just create a .iso.

---

### Post by paf69 on 2007-04-06
is there anyway to make it so dvdshrink doesn't resize it...i have a bunch oh DVD-DL disks and i don't want to loose quality

---

### Post by stchman on 2007-04-16
> **paf69 said:**
> is there anyway to make it so dvdshrink doesn't resize it...i have a bunch oh DVD-DL disks and i don't want to loose quality


I am going to assume you are meaning k9copy as DVDShrink is a Windows program.  Yes k9copy will do both DVD9-DVD5 compression and will just keep the size to fit on DVD9 disc.  It is in the settings menu.

---

### Post by orb9220 on 2007-04-16
I use DVDShrink  with wine. 

The reason is that linux programs do not give me the control I want. Like custom compressions for different parts of the dvd like max compress for extra's,ease of stripping and replacing annoying start screens,etc..

Also use dvdecrypter under wine.

I wish the linux programs where as powerful. The reality is they are getting there but lack ease of use with flexibly of options that the windows programs give.

[https://help.ubuntu.com/community/DVDShrink](https://help.ubuntu.com/community/DVDShrink)
[http://www.mrbass.org/linux/ubuntu/dvdshrink/](http://www.mrbass.org/linux/ubuntu/dvdshrink/)

---

### Post by mgmiller on 2007-06-06
> is there anyway to make it so dvdshrink doesn't resize it...i have a bunch oh DVD-DL disks and i don't want to loose quality

Yes.  
Start DVD shrink and click on Edit and preferences.
In the first preferences tab there is a drop down to select the size you want.
either DVD5 or DVD9 or custom.  I think you will want DVD9.

---

