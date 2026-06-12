---
title: "Ububtu 17.04 Bolnagri (Hindi) keyboard layout"
date: 2017-05-04
forum: General Help
---

### Post by astroaniket on 2017-05-04
The Bolnagri (Hindi) keyboard layout has been long supported on Ubuntu. It is a nice phonetic keyboard with an intuitive layout. After upgrading my Ubuntu to 17.04, it suddenly stopped working. I tried removing it from installed keyboard layouts and then add again. But it doesn't even show up in the list. The only Hindi keyboard option is something called "Indian", which is non-intuitive. 

What exactly went wrong? Did ubuntu stop supporting Bolnagri? I tried google searching the answer already. I only found answers relevant to old versions of Ubuntu. But mine was working fine with older versions.

---

### Post by #&amp;thj^% on 2017-05-04
Please see this: [https://cgit.freedesktop.org/xkeyboard-config/commit/?id=913af7dafaab8ff4a9ae0d1e4c4097caf4a8022d](https://cgit.freedesktop.org/xkeyboard-config/commit/?id=913af7dafaab8ff4a9ae0d1e4c4097caf4a8022d)

EDIT I should be more helpful here:

They are hidden and not dropped. If you open a terminal window and run this command:

```
gsettings set org.gnome.desktop.input-sources show-all-sources true

```
the Bolnagri layouts should be shown in the user interface again.

---

### Post by astroaniket on 2017-05-12
Worked like charm. Thank you very much.

Others using this thread: Please reboot machine once after you run the command. It may not work without reboot.

---

### Post by #&amp;thj^% on 2017-05-12
Your Welcome! :)
It might be of great help to others looking for the solution...if this was marked as [SOLVED]: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
And yes a reboot when changes like this are made is always the proper choice.

---

