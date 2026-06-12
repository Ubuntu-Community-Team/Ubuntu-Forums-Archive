---
title: "Printing envelopes"
date: 2014-10-25
forum: General Help
---

### Post by daniell59 on 2014-10-25
I completely messed up the formatting in Libre Office Writer. Is there anyway to reset it back to the default setting so that I can start again?

Ubuntu 14.04 32

---

### Post by VH-BIL on 2014-10-25
try deleting your settings for libreoffice and restarting the app after that, that is what I would do anyway :)

Located at:
/home/<user name>/.config/libreoffice/3/user *[COLOR=#daa520](since LibreOffice3.5.0)[/COLOR]*
/home/<user name>/.libreoffice/3/user *[COLOR=#daa520](prior to LibreOffice3.5.0)[/COLOR]*

---

### Post by daniell59 on 2014-10-25
> **VH-BIL said:**
> try deleting your settings for libreoffice and restarting the app after that, that is what I would do anyway :)

Located at:
/home/<user name>/.config/libreoffice/3/user *[COLOR=#daa520](since LibreOffice3.5.0)[/COLOR]*
/home/<user name>/.libreoffice/3/user *[COLOR=#daa520](prior to LibreOffice3.5.0)[/COLOR]*

I would appreciate further assistance. This is as far as I know how to go.
See image.

---

### Post by btindie on 2014-10-25
Do it in a terminal.... Hold Ctrl+Alt and press T to open a new terminal window and type
```
rm -rf ~/.config/libreoffice
```
but make sure you close any open LibreOffice windows first. That'll then remove any user setting relating to it.

Alternatively use the following to rename the directory should you have anything in there that you wish to keep (such as a custom dictionary or template which you can then copy to the new config it creates)
```
 mv -v ~/.config/libreoffice{,.bak}
```

Then run libreoffice and it should create a new config.

---

### Post by daniell59 on 2014-10-25
> **btindie said:**
> Do it in a terminal.... Hold Ctrl+Alt and press T to open a new terminal window and type
```
rm -rf ~/.config/libreoffice
```
but make sure you close any open LibreOffice windows first. That'll then remove any user setting relating to it.

Alternatively use the following to rename the directory should you have anything in there that you wish to keep (such as a custom dictionary or template which you can then copy to the new config it creates)
```
 mv -v ~/.config/libreoffice{,.bak}
```

Then run libreoffice and it should create a new config.

I did as you instructed but it still did not bring me back to the default settings.

I do appreciate your assistance.

---

### Post by VH-BIL on 2014-10-25
You do not have to use the command line to delete, You can use the Files (Nautilus). When you press CTRL + h it will toggle the viewing of hidden files. Any file with a . (dot or period) at the start of it is hidden. Make sure LibreOffice is closed, navigate to the LibreOffice settings directory (I gave the path to you in an earlier post) and delete it and empty recycle bin. The next time you start LibreOffice it will start with default settings because the old settings will not exist.

---

### Post by daniell59 on 2014-10-26
> **VH-BIL said:**
> You do not have to use the command line to delete, You can use the Files (Nautilus). When you press CTRL + h it will toggle the viewing of hidden files. Any file with a . (dot or period) at the start of it is hidden. Make sure LibreOffice is closed, navigate to the LibreOffice settings directory (I gave the path to you in an earlier post) and delete it and empty recycle bin. The next time you start LibreOffice it will start with default settings because the old settings will not exist.

Please forgive my ignorance. I am ashamed to ask what may be an inane question.
In the home folder I don't see my user name. It is daniel.

---

### Post by coffeecat on 2014-10-26
Where it says "Home" near the top-left means that you are in /home/daniel. To convince yourself, press ctrl-L and you will see the actual path in text. Press esc to get back to the so-called bread-crumb trail.

Double-click on the .config folder and you will find the libreoffice folder inside that. Rather than delete anything, rename the libreoffice folder to libreoffice.orig (make sure libreoffice is closed when you do this). Now restart libreoffice and see if this helps. A new libreoffice folder should be generated with the default settings. Once you are happy that everything is OK, you can delete the libreoffice.orig folder and contents. Or if things get worse (unlikely) you can restore the original libreoffice folder.

---

### Post by VH-BIL on 2014-10-26
The file system on Linux is a little different to Windows and may take some getting use to, but in time you will find it is organised better. It is very similar to Apple OSX.

If you click Computer under Floppy Disk that will take you to the root of your file system. In there you will see the home directory, click on that and you will see your name. Clicking on Home where you did is a short cut to your home directory. Like coffeecat said, CTRL+L will show you the full path.

Good luck!

---

### Post by daniell59 on 2014-10-27
Let me preface this by thanking those that have taken the time to help me. For some reason, I am still missing something. I cannot seem to go further than the image illustrates. I hope that it will become clear to me before your patience runs out.

---

### Post by coffeecat on 2014-10-27
As VH-BIL said, pres ctrl-h to reveal the hidden folders and files - those that are prefaced with a dot - and you will see the .config folder. You should be OK after that.

Instead of the keyboard shortcut, you can choose View from the Nautilus menu (up in the top bar, and invisible until you mouse over it) and then "show hidden files".

---

### Post by daniell59 on 2014-10-27
I finally got it thanks to all.

---

