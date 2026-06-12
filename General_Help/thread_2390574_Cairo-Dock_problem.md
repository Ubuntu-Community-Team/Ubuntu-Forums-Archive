---
title: "Cairo-Dock problem"
date: 2018-04-30
forum: General Help
---

### Post by Y^2om&amp;#7sgP on 2018-04-30
Hi All
I've just performed a clean install of Xubuntu 18.04 on my laptop.  Everything appears to be great, but for some reason the shortcuts folder has an error 'No disks or bookmarks were found'
It does the same thing on a Xubuntu 18.04 VM.
But, there are shortcuts if I go straight to file manager.
I suspect that it's xubuntu as cairo-dock works on a desktop currently running 16.04
Can anyone shed any light?

---

### Post by herve-fournerat on 2018-05-01
Hi everyone,
I have the same problem, except I don't have any error message. After upgrading from Ubuntu 17.10 to 18.04, the "shortcuts" plugin for cairo-dock is empty.[IMG]https://image.noelshack.com/fichiers/2018/18/2/1525172214-capture-d-ecran-de-2018-04-30-10-07-02.png[/IMG]
RV

---

### Post by Y^2om&amp;#7sgP on 2018-05-03
Any ideas anyone ?

---

### Post by Claus7 on 2018-05-03
Hello,

it is advised to quit cairo-dock.

Then just run the command:
```
sudo apt-get install cairo-dock-gnome-integration-plug-in
```

then start cairo-dock and shortcuts will be working again.

Regards!

---

### Post by Y^2om&amp;#7sgP on 2018-05-03
Thank you Claus7, works :P

---

### Post by herve-fournerat on 2018-05-05
Thanks ! Works here also \\:D/

---

