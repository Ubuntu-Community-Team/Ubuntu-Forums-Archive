---
title: "in Grub boot menu"
date: 2008-05-25
forum: General Help
---

### Post by Jack Shankle on 2008-05-25
When the Grub menu comes up go to "Other Operating Systems".
Here I have Windows Vista/Longhorn (loader)
and         Windows Vista/Longhorn (loader) the 2nd time.
I would like to change the first one to Vista
and the 2nd one to Vistaalt.
This is my first attempt at altering anything in Grub so I am
leary and ignorant.
Thanks for any help.

---

### Post by forestpixie on 2008-05-25
Make a backup and then open it for editing - you can just change the titles easily enough.

```
sudo cp /boot/grub/menu.lst /bbot/grub/menu.2504
```

Then open for editing

```
gksudo gedit /boot/grub/menu.lst
```

Chnage the text as you want . close and save

---

### Post by bwhite82 on 2008-05-25
Firstly, make a backup of the configuration file:

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old

Then open it:

sudo gedit /boot/grub/menu.lst

Then change the bold items below:
> 
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(**hd0,0**)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(**hd0,1**)
savedefault
makeactive
chainloader	+1


TO:

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(**hd0,1**)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(**hd0,0**)
savedefault
makeactive
chainloader	+1
[/QUOTE]

---

### Post by forestpixie on 2008-05-25
Where did that all come from ?

---

### Post by Jack Shankle on 2008-05-25
Thanks guys for helping.

The commands didn't work for me. I got error 27 "unrecognized command".
I highlighted Windows/Longhorn (loader) and hit "e"
at Grub I typed in your commands.
Possibly something misspelled or a space in the wrong place?
Or a "0" for an "o"?

---

### Post by forestpixie on 2008-05-26
What, exactly are you trying to do here - you have 2 different viewpoints of the first post.

---

### Post by Jack Shankle on 2008-05-26
Obviously I don't know where to enter your GRUB commands
as I get error 27 "unrecognized instruction".

Like I said before I highlight "Windows Vista/Lognhorn (loader)
then I can hit "e" or "c". From there I am lost.....
Thanks for any help.

---

### Post by Gunman1982 on 2008-05-26
Boot into Ubuntu, don't edit in the bootloader (grub) on startup since it won't save any changes you make (luckily).  
Then open a console and do what forestpixie suggested in post #2. Just change the Description in the title line from Vista(Longhorn) to whatever you like.

---

### Post by strabes on 2008-05-26
> **Jack Shankle said:**
> Obviously I don't know where to enter your GRUB commands
as I get error 27 "unrecognized instruction".

Like I said before I highlight "Windows Vista/Lognhorn (loader)
then I can hit "e" or "c". From there I am lost.....
Thanks for any help.

You must open a terminal (Applications > Accessories > Terminal) to enter the commands. The easiest way to enter them is to highlight them by triple clicking on them and then middle clicking in the terminal to paste the highlighted text. When editing /boot/grub/menu.lst be **very** careful. If you mess up you may be left with an unbootable system. This is easily fixable via reinstalling GRUB through the link in my signature, but it's a pain.

---

### Post by Jack Shankle on 2008-05-26
Thank you for responding Strebes.
I did what you suggested and then it asked for my password which
I entered. Nothing happened.:confused:

---

### Post by forestpixie on 2008-05-26
Hi - are you trying to get vista to boot or are you trying to make the name different on the menu list when you boot.

---

