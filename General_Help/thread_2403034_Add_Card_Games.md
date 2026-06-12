---
title: "Add Card Games?"
date: 2018-10-06
forum: General Help
---

### Post by Abe_Hanson on 2018-10-06
I have installed ubuntu-studio 18.04 and can't seem to find much in the way of additional card games. Is there something I need to do to access the available software?
Primarily I am interested in the Poker game, Texas Hold'em.
And while I am asking, where would I find how to change the grub menu as I am dual-booted on this machine?
Thanks in advance.:D

---

### Post by Bashing-om on 2018-10-06
Abe_Hanson; Hello -

Linux has the name "pokerth" - th for Texas Hold'em -.
see the result of terminal command:
```

apt show pokerth

```
If this is what you want, to install run:
```

sudo apt install pokerth

```

as to changing grub, what is it that you want to change ?

[INDENT]my bit to try and help
[/INDENT]

---

### Post by Abe_Hanson on 2018-10-06
Thank you so much for the help, sorry I wasn't more specific about the Grub menu, I just wanted to change the line of the default boot to another OS.

---

### Post by Bashing-om on 2018-10-06
Abe_Hanson; K -

In the grub boot menu, count to the entry you want as the boot, starting the count at zero.
then change the line " GRUB_DEFAULT=0" in the file /etc/default/grub  to contain the entry number -
always make a backup of any file you edit - never can tell what might perchance.

propagate the change to the operating system:
```

sudo update-grub

```

[INDENT][INDENT]all there is to it
[/INDENT][/INDENT]

---

### Post by Abe_Hanson on 2018-10-09
Thanks again for the help, unfortunately  I do not have permission to edit this file.
Unlike Debian, ubuntu won't allow me to log in as root. I can open this file with mousepad but is mousepad the default
text editor? I didn't see an option to use gedit.

Edit: Success, I used 
                               sudo mousepad /etc/default/grub
entered the root password and it opened the file, let me edit and save it, then sudo update-grub and Voila.

---

### Post by Impavidus on 2018-10-10
sudo <some_text_editor> is indeed the way to go to modify any system files, but in general sudo shouldn't be used with GUI programs without some extra precautions, because GUI programs running as root have the tendency to occasionally make other files root-owned and make it impossible to login the next time. Best to use a terminal-based text editor like nano or vim. Using sudo -H <GUI_text_editor> is safe too.

---

### Post by Abe_Hanson on 2018-10-10
> **Impavidus said:**
> sudo <some_text_editor> is indeed the way to go to modify any system files, but in general sudo shouldn't be used with GUI programs without some extra precautions, because GUI programs running as root have the tendency to occasionally make other files root-owned and make it impossible to login the next time. Best to use a terminal-based text editor like nano or vim. Using sudo -H <GUI_text_editor> is safe too.


Thanks for the info.

---

### Post by Yellow Pasque on 2018-10-10
Please mark the thread SOLVED if you have no further questions ("Thread Tools" menu above first post).

If you're coming from Debian, you may want to give this a quick read: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

