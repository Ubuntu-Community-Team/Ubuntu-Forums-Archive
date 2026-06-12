---
title: "Which download closest to Ubuntu"
date: 2006-07-11
forum: General Help
---

### Post by SteveHoffmanUK on 2006-07-11
I was delighted to see that Mailwasher, an anti-spam program, offers its non-free version in a Linux version. However, when I went to their download page, I was disappointed to see the choice as:
Linux (Fedora 2)
Linux (Fedora 3)
Linux (Fedora 4)
Linux (Linspire 4.5)
Linux (Linspire 5.0)
Linux (Mandrake 10.0)
Linux (Mandrake 10.1)
Linux (SuSE 9.1)
Linux (SuSE 9.2)
Linux (Mepis)
Linux (Mepis 2004)
Linux (Kubuntu)
Linux (Sarge)
Linux (Xandros)

...but no Ubuntu! 

Which of these is the best to download for Ubuntu, and what do I have to do to install it? I'm a newbie, so a nice terminal script would be very much appreciated.

---

### Post by Ramses de Norre on 2006-07-11
The kubuntu one, there is no difference in the packaging system between ubuntu and kubuntu (or xubuntu or whatever).
It's probably a .deb file which you'll download, then you go to the directory you downloaded it into, if it's in /home/username/downloads you do ```
cd ~/downloads
``` and then you install it with ```
sudo dpkg -i filename.deb
``` (fill in the right filename, type the first two or three letters and press tab to autocomplete, if nothing happens type a few more letters and press tab again)

---

### Post by The Noble on 2006-07-11
...or just double click on the downloaded file for ease, that is if it is a .deb.

---

### Post by SteveHoffmanUK on 2006-07-12
Thanks to both of you for the advice. I did it but there were some dependencies missing, so will have to work my way through it.

---

### Post by T700 on 2006-07-12
If you don't need the specific functionality of Mail Washer, you might try the free program, Spam Assasian (sp?).  It is in the repos.

Paul

---

