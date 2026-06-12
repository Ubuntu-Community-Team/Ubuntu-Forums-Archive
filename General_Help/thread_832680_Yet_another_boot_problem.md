---
title: "Yet another boot problem"
date: 2008-06-17
forum: General Help
---

### Post by boxofrokx on 2008-06-17
I had a system that was largely working (running ubuntu 8.04). I wanted to try kde so I started downloading it last night. During the download, I placed my laptop on a couch. It overheated and froze up.

When I rebooted, everything went normally until the end. I get a desktop but no menus (the bars that start on top and bottom, hold the 'Applications Places System' headers).

What do I need to try?

---

### Post by boxofrokx on 2008-06-18
Ok, a little more info.

I can boot to recovery mode, I can run **xfix** and **dpkg**, no change.

It allows me to login. It gives me the picture that is my desktop backgroung and nothing else.

I can **ctrl+alt+f1** and get command line mode. I don't know what to do from there.

Any ideas?

---

### Post by sailor2001 on 2008-06-18
hit ALT + F2 and type in 'xfce4-panel'

---

### Post by boxofrokx on 2008-06-18
Thanks for the help. You pointed me in the right direction.

I tryed 'xfce4-panel' on a command line. It said 'xfce not present, try sudo apt-get install xfce4'.

Well, I had to access the net to get that.

I then tryed 'sudo apt-get install gnome-panel'

success. Retrying KDE now.

---

