---
title: "Error message at boot"
date: 2007-07-24
forum: General Help
---

### Post by neros_87 on 2007-07-24
I have been using and enjoying Ubuntu and wubi for about a month now. Up untill this point everything was working really well. Yesterday I decided to open up the pc to give it a bit of a spring clean and whilst it was open I installed an old ge-force fx5600 I had recently leant to a friend and repaired a faulty cd-rw drive. Now when I boot into ubuntu I get the following message:

/bin/sh: can't access tty: job control turned off

So far I’ve re-installed wubi a few times to no avail; I’ve also disconnected the aforementioned cd-drive I managed to get working in case that had brought about any problems. I am about to try removing the fx5600 I installed to see if that is the cause. However, the friend I leant it to was running wubi/ubuntu perfectly fine with the same card installed.

Thanks for any help.

---

### Post by neros_87 on 2007-07-27
OK, so it boots up without the graphic card in. Hovever now it says that the x-server is not configured which i guess is understandable as it had previously tried to set up with the fx5600 installed. Any ideas on how to get round this?

---

### Post by tuxcantfly on 2007-07-28
Ctrl-Alt-F1

login using your username and password, then enter:

```
sudo dpkg-reconfigure xserver-xorg
```

---

