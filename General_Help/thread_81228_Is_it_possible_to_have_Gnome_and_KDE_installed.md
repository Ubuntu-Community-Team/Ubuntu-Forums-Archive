---
title: "Is it possible to have Gnome and KDE installed?"
date: 2005-10-24
forum: General Help
---

### Post by chimera on 2005-10-24
Can I install both desktop enviroments,so that I can choose between them at login or can I only have one installed?

---

### Post by invalid on 2005-10-24
You can have both.

You will be asked at the end of the new desktop installation which manager you would like to be default - and then when it loads, you can always select to use the other if you wish.

Cheers,
Cb

---

### Post by chimera on 2005-10-24
OK,thanks for clearing that up

btw,what's the KDE package called in synaptic?I can't find it

---

### Post by RAOF on 2005-10-24
kubuntu-desktop

---

### Post by chimera on 2005-10-24
thanks

---

### Post by Sutekh on 2005-10-24
You may want to check out this thread too, as installing kubuntu-desktop will add all the KDE apps to your GNOME menus.  You may like having them all there, or you may want them all gone, or you may want some and not others.  Anyway, this thread shows how you can do that.  All it does is add a line to the .desktop files for each KDE application, and is easily changed to suit your preferences.

[http://www.ubuntuforums.org/showthread.php?t=59455]("http://www.ubuntuforums.org/showthread.php?t=59455")

You could probably choose what you want in the GNOME menu editor too.

---

### Post by Pigmudgeon on 2005-10-24
But won't there be a lot of redundant files? That is, files that are identical in each setup?

--p!

---

### Post by Sutekh on 2005-10-24
I'm not quite sure what you mean.

When the Kubuntu desktop is installed the .desktop files for each application are installed in /usr/share/applications/kde/.  The Ubuntu .desktop files are in /usr/share/applications/.  These .desktop files are shared by KDE/GNOME, and there is only one copy of each.  By altering these .desktop files you can change which applications are shown in which desktop environment.

---

### Post by Dr. Nick on 2005-10-24
[QUOTE=Pigmudgeon]But won't there be a lot of redundant files? That is, files that are identical in each setup?

--p![/QUOTE]

If you mean all files in general then no shouldnt be redundancy, it wont ask you which to boot up at the black grub screen , but at the place you type the user/pass

Kubuntu-Desktop is installed ontop of ubuntu. They are on the same partition and share the same files. Either though can be installed by themselves by getting to approite iso , but if you have one you can add the other without duplicating all the files

---

