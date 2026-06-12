---
title: "Gnucash and Autokey"
date: 2019-09-26
forum: General Help
---

### Post by rolfedavid on 2019-09-26
Hi, I have installed Gnucash V.3.7 The launcher command is: usr/bin/flatpak run --branch=stable --arch=x86_64 --command=gnucash --file-forwarding org.gnucash.GnuCash @@ %f @@. I am trying to get this to work with Autokey to no avail have tried subprocess.'Popen' & 'xdg-open' I am hoping that someone will know the answer. The new version uses flatpak. The launch command does work from the menu.

---

### Post by TheFu on 2019-09-27
Getting different programs to work together when one of them (or both) are installed using snaps or flatpaks is problematic. [https://fedoramagazine.org/getting-started-flatpak/](https://fedoramagazine.org/getting-started-flatpak/) explains a little:
> Finally, Flatpak runs each program inside a sandbox environment, requesting permission from the user before accessing hardware devices or files.
Basically, it is considered a "*feature*" when programs cannot talk directly.

There might be a flatpak config setting on a per-program realm that will let you allow other programs access.  Perhaps.  IDK.  The easy answer is to find a non-snap/non-flatpak package and install that.

---

### Post by rolfedavid on 2019-09-29
Thanks for the reply. I had already been using an earlier version of Gnucash but thought that a later version would offer something different or better. I came to the conclusion that the problems I had: one of them was that it took two or three minutes to load and launching it in a terminal showed that it compiled the program every time, that it was a flatpak. My next question was going to be can someone explain 'Flatpak'. Thank you your link goes a long way to answer that. I will now go back to use an earlier version. Many many thanks.

---

### Post by HermanAB on 2019-09-29
As far as I can figure, a flatpak is similar to BSD Jails.

It makes things easier and less risky for the system administrator, by increasing the isolation between applications, which has merit on a server, but I would not use flatpaks on a single user desktop/laptop machine.

---

### Post by TheFu on 2019-09-29
> **rolfedavid said:**
> Thanks for the reply. I had already been using an earlier version of Gnucash but thought that a later version would offer something different or better. I came to the conclusion that the problems I had: one of them was that it took two or three minutes to load and launching it in a terminal showed that it compiled the program every time, that it was a flatpak. My next question was going to be can someone explain 'Flatpak'. Thank you your link goes a long way to answer that. I will now go back to use an earlier version. Many many thanks.

If you can find a normal PPA with the newer Gnucash, I bet the issue would go away.  I think it is just a packaging issue and likely that the gnucash team never considered someone would want to use autokey.  I've met one of the gnucash devs. It would be worth opening a bug report with that project to see if they can do something or provide a workaround for your desires.  They use of flatpaks is so developers don't have to make 15 different packages to support 15 different Linux distros.

---

### Post by dragonfly41 on 2019-09-29
Anything you see on your desktop can be automated by an automation script which emulates user actions (like a macro). I use [Actiona]("https://wiki.actiona.tools/doku.php?id=en:code") to automate desktop workflows.

---

