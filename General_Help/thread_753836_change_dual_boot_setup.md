---
title: "change dual boot setup"
date: 2008-04-13
forum: General Help
---

### Post by Frank H on 2008-04-13
I need help tring to edit (boot/grub/menu.lst )so I can have windows xp to start auto . When I try and edit menu.lst it tells me that I don't have permission . I need to change this soon

PLEASE

[http://ubuntuforums.org/images/smilies/smiley-faces-75.gif](http://ubuntuforums.org/images/smilies/smiley-faces-75.gif)

---

### Post by angry_johnnie on 2008-04-13
This file must be edited as root, that's why you don't have permission.
If you really want to make changes to it, back it up first.
Open a terminal
Applications > Accesories > Terminal

and type this:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```

This will create a backup, called menu.lst.bak, which can be restored later.

Then you can start editing.
Sill in the terminal, type this:
```

gksu gedit /boot/grub/menu.lst
```

And you'll be presented with the file.

Take a look at these:

[http://www.howtogeek.com/howto/ubuntu/set-windows-as-default-os-when-dual-booting-ubuntu/](http://www.howtogeek.com/howto/ubuntu/set-windows-as-default-os-when-dual-booting-ubuntu/)

[http://ubuntuforums.org/showthread.php?t=71915](http://ubuntuforums.org/showthread.php?t=71915)

---

### Post by Jose Catre-Vandis on 2008-04-13
Open terminal

Issue command:
```
sudo gedit /boot/grub/menu.lst
``` or
```
sudo nano /boot/grub/menu.lst
``` depending on how you like to work

Scroll down from the top of the file a little way until you find the "#default num" section. At the bottom of this section is the word [COLOR="DarkRed"]default[/COLOR] and the number [COLOR="DarkRed"]0[/COLOR]. Over type the 0 with the word [COLOR="DarkRed"]saved[/COLOR]. The line should now look like this:```
default     saved
``` remove the # at the front of the line if there is one.

Now scroll down to the bottom of the file. Look for any entries in the boot listings that say [COLOR="DarkRed"]savedefault[/COLOR], and remove or comment out each instance. Once this is done, go to your Windows boot section which looks something like this```
# WINDOWS
title		Windows XP
root		(hd0,2)
makeactive
chainloader	+1
``` Add the word [COLOR="DarkRed"]savedefault[/COLOR] to the bottom of this section, so it now looks like this:```
# WINDOWS
title		Windows XP
root		(hd0,2)
makeactive
chainloader	+1
savedefault
```

Save the file and reboot. this should now default Windows as your starting OS. If you do not want to see the grub screen, or wish to reduce the time the screen is available, edit the "timeout" and "hiddenmenu" sections near the top of the file. There, i think that is it :)

---

### Post by dejans on 2008-04-13
I recommend installing startup-manager via synaptic, it's very easy to use.

---

