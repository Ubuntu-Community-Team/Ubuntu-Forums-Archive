---
title: "Cant see anything"
date: 2007-08-26
forum: General Help
---

### Post by nzgabriel on 2007-08-26
I recently went into the restricted device manager (or something similar) and told it to use the ATI driver thing. But now whenever I try and load Ubuntu, instead of seeing the login screen, all I see is, well, nothing.

Is there a way to fix this problem without getting rid of all my files, because I have stuff I would really like **not** to lose?

Seeing as I am not too familiar with Ubuntu, I would like to know how to fix this in a step-by-step way; thanks.

---

### Post by mikaelsnavy on 2007-08-26
If you it (I think) Ctrl + Alt + F4 when it goes blank, do you get to a command line or a login command line?

---

### Post by nzgabriel on 2007-08-26
> **mikaelsnavy said:**
> If you it (I think) Ctrl + Alt + F4 when it goes blank, do you get to a command line or a login command line?

No, if I do that while it's booting up it also goes blank at this point.

I can get into recovery mode though, which has a command line.

---

### Post by merlinus on 2007-08-26
Boot into recovery mode, login...then enter:

```

sudo dpkg-reconfigure xserver-xorg

```
You can probably go with the default for most screens, but select "vesa" for your video driver.

Then:
```

startx

```
or reboot.

This should at least get you to a GUI, then you can search how to install the correct video drivers for your card.

-merlin

---

### Post by nzgabriel on 2007-08-26
Thanks, that fixed it. Your help is very, very much appreciated! :KS

---

