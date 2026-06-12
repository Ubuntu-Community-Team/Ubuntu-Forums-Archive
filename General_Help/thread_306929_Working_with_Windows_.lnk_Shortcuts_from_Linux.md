---
title: "Working with Windows .lnk Shortcuts from Linux"
date: 2006-11-25
forum: General Help
---

### Post by hxx4 on 2006-11-25
I'm curious if there is anyway to create or follow Windows (XP) shortcuts which may be located on other hard drives or network drives from in Ubuntu (or any Linux distro). For example, I want to create a shortcut on the desktop of one of my networked Windows computers to a file in another directory on the same computer. Similarly, I might want to see what file a shortcut on a networked drive references. I think this might be related to working with Windows file systems or samba for networked drives. Thanks for any ideas.

---

### Post by syadnom on 2006-11-25
there is not current way to do it and the .lnk files are not just a text file there are special binary file providing the 'link'.  there are some special characters in these files i cant recognize but the file path can be seen so it is definitely possible and could probably be done with a shell script.

---

### Post by Endolith on 2007-08-31
There is a way to do this in KDE.  See 

[http://bugs.kde.org/show_bug.cgi?id=85348#c7](http://bugs.kde.org/show_bug.cgi?id=85348#c7)

[http://packages.debian.org/stable/kde/kdeaddons-kfile-plugins](http://packages.debian.org/stable/kde/kdeaddons-kfile-plugins)

> This is a collection of plugins for the KDE file dialog. These plugins extend the file dialog to offer advanced meta-information for text, HTML and desktop files, as well as for folders, Windows .lnk files, MIME archives and X.509 certificates.

Is there a way to get this functionality in Nautilus?

---

### Post by stchman on 2007-08-31
> **hxx4 said:**
> I'm curious if there is anyway to create or follow Windows (XP) shortcuts which may be located on other hard drives or network drives from in Ubuntu (or any Linux distro). For example, I want to create a shortcut on the desktop of one of my networked Windows computers to a file in another directory on the same computer. Similarly, I might want to see what file a shortcut on a networked drive references. I think this might be related to working with Windows file systems or samba for networked drives. Thanks for any ideas.

Creating shortcuts (linux calls them symbolic links) are easy.

1.  In the GUI middle mouse click in Nautilus and drag to the desktop.
2.  Use the ln -s <file or folder> ~/Desktop

Hope this helps.

---

### Post by kylegordon on 2008-02-22
> **stchman said:**
> Creating shortcuts (linux calls them symbolic links) are easy.

1.  In the GUI middle mouse click in Nautilus and drag to the desktop.
2.  Use the ln -s <file or folder> ~/Desktop

Hope this helps.


The above information does not assist in dealing with .lnk files, as the original poster was asking. 

There are several ways of handling .lnk files in Linux, some of which are described at the following locations...

[http://bugs.kde.org/show_bug.cgi?id=85348#c7](http://bugs.kde.org/show_bug.cgi?id=85348#c7)
[http://packages.debian.org/stable/kde/kdeaddons-kfile-plugins](http://packages.debian.org/stable/kde/kdeaddons-kfile-plugins)
[http://www.linuxquestions.org/questions/linux-general-1/follow-windows-shortcuts-from-linux-617917/](http://www.linuxquestions.org/questions/linux-general-1/follow-windows-shortcuts-from-linux-617917/)

Regards

Kyle

---

### Post by Endolith on 2008-02-22
> **stchman said:**
> Creating shortcuts (linux calls them symbolic links) are easy.

1.  In the GUI middle mouse click in Nautilus and drag to the desktop.
2.  Use the ln -s <file or folder> ~/Desktop

Hope this helps.

I'm pretty sure that has nothing to do with this thread.

---

