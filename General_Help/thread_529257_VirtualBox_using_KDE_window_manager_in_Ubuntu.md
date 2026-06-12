---
title: "VirtualBox using KDE window manager in Ubuntu"
date: 2007-08-19
forum: General Help
---

### Post by jonathanmotes on 2007-08-19
Hello,

I just installed VirtualBox on Ubuntu (Feisty), but it opens with the KDE window manager. I have KDE installed on my computer, but I'm currently running Gnome. I saw a screenshot [here]("http://bp2.blogger.com/_CYT-hXzRPzk/RhMxz-pOSHI/AAAAAAAAAE0/daE4pjjYCU4/s1600-h/Screenshot-6.png") with it running correctly in Gnome, so I'm supposing that VirtualBox is not a KDE program.

Here's a screenshot of what I'm seeing:

[IMG]http://ubuntuforums.org/g/images/270346/1_Screenshot.png[/IMG]

Hopefully it is big enough to be visible. The Details tab, for example, is clearly KDE. I really would like its appearance to be consistent with the rest of my GNOME desktop.

Thanks!

---

### Post by wolfen69 on 2007-08-19
the details tabs look  the same to me. take another look.

---

### Post by AnRa on 2007-08-19
VirtualBox uses Qt instead of GTK+, that's why it looks different.

---

### Post by netkid91 on 2007-08-19
As stated above, VirtualBox is a QT application, and sadly that means integration with a GNOME desktop is not feasible.  While you CAN use the "gtk" theme for QT which jumps through some hoops to use your GTK styles in QT apps, it causes more problems than the visual integration it provides, and the apps still remain KDE apps at heart so the point is moot.  Sorry!

---

