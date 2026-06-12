---
title: "xrdp: desktop and remote have two different views"
date: 2013-12-03
forum: General Help
---

### Post by fra_87 on 2013-12-03
Hello everybody.
I have a problem. I just installed xubuntu 13.10 on my PC and wanted to use RDP to remotely connect to it.
so (after a apt-get update and upgrade) i simply did sudo apt-get install xrdp and then created a file in my home called .xsession and with "xfce4-session" written in it (without quotes).
Now, when i connect, i can see that there are different modules with xrdp. I use sesman-xvnc (because sesman-x11rdp doesn't work) and this is the result:

[http://i42.tinypic.com/i1wq5l.jpg](http://i42.tinypic.com/i1wq5l.jpg)

while this is what i see when i login directly from the pc

[http://i41.tinypic.com/20tghi1.jpg](http://i41.tinypic.com/20tghi1.jpg)

As you can see some icons (most of them actually) are missing, while the theme is grey instead of the original black. Moreover (you can't see it from the images) the "start" menu is different (the programs are placed in different ways).

I found that at the beginning the right theme (black bar and so on) loads up, but then after 2 or 3 seconds it "crashes", giving me the first image.

also i found that the environment variables are different from the ones in the "desktop" mode (i.e. locally connected). Is it normal?

What can i do?

Best regards

---

