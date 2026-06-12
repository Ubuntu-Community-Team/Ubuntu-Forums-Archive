---
title: "Restart and Powerdown buttons missing"
date: 2007-04-30
forum: General Help
---

### Post by Vekin on 2007-04-30
Hello.  Recently, my login screen changed and my power down button now only lists hybernate, log off, switch user, suspend, and lock screen.  It's missing Restart and Powerdown.  How do I get the old log in screen, and my restart/shutdown buttons back?

---

### Post by ceno-byte on 2007-04-30
hi there Vekin if you dont mind can you provide more information. Ubuntu version , are you using just ubuntu or kubuntu or do u have enhancments such as bery + compiz or xgl running. so we will be able to further help you better.

---

### Post by Vekin on 2007-04-30
I'm running Feisty Fox, and just Ubuntu as far as I know.  I'm using Beryl, and I think that's the only thing I'm running, as far as I know.

Edit: Actually, I did notice that it happened after I installed some KDE applications.  Also, when I make changes to my Firefox plugin properties, they're unsaved when I restart.

---

### Post by ceno-byte on 2007-04-30
ok thanks for the info vekin according to this thread [http://ubuntuforums.org/showthread.php?t=219720&highlight=xgl+shutdown](http://ubuntuforums.org/showthread.php?t=219720&highlight=xgl+shutdown)

try this:

1. Open a terminal. Type in 'gksudo nautilus' to make yourself root. Your 'Home Folder' browser window will pop up.
2. Navigate to the 'file system' folder (located on the left).
3. Open the 'etc' folder.
4. Open the 'gdm' folder.
5. Open the file 'gdm.conf-custom'
6. Scroll down to the bottom of this file. If you have a line called 'SystemMenu=false', delete the 'false' part and type in 'true' ( i.e. the new entry should read: SystemMenu=true )
7. Click 'Save'.
8. Shut off the window.
9. Restart your computer.

i hope that helps you  and good luck.

---

