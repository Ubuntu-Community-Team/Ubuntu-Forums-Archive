---
title: "why can't i choose more than 15 min for screen locking?"
date: 2024-06-24
forum: General Help
---

### Post by ronjjjg8885 on 2024-06-24
my password is long and i don't like to type it each time i return to the pc..

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293911&stc=1[/IMG]

tnx

---

### Post by currentshaft on 2024-06-24
gsettings set org.gnome.desktop.session idle-delay <delay in seconds>

Took me 2 seconds to Google, probably faster than it took you to make this post.

---

### Post by ronjjjg8885 on 2024-06-24
i see this now
[https://www.techrepublic.com/article/how-to-set-the-gnome-idle-delay-from-the-command-line/](https://www.techrepublic.com/article/how-to-set-the-gnome-idle-delay-from-the-command-line/)
but i don't understand. do i need extra package for that?

---

### Post by Holger_Gehrke on 2024-06-24
'gsettings' is to Gnome as the registry is to Windows, a central binary store of all settings. So if you're using Gnome then the gsettings command should be installed. As a matter of fact it's part of the package libglib2.0-bin which should be installed on all DEs that are based on GTK.

Holger

---

