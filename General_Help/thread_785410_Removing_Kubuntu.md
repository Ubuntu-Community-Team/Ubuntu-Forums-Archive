---
title: "Removing Kubuntu"
date: 2008-05-07
forum: General Help
---

### Post by lagaile on 2008-05-07
I need to remove Kubuntu. My husband doesn't care for it being on the PC. Any  safe way to do this? I have Vista. I've read alot of negative tips on uninstalling. My son put it on and now am I stuck? Thanks.

---

### Post by _sAm_ on 2008-05-07
How did he install Kubuntu; from within Windows Vista or by the normal way? 

Do you have the Vista disc?

---

### Post by zerofool2005 on 2008-05-07
If you have the Vista disk and dont have any data that needs backing up. Just format and install a new install of vista

---

### Post by _sAm_ on 2008-05-07
Install Vista!?!?! NOOO, you can fix this very easy if you have the Vista disc - without the need to reinstall it.

---

### Post by benste on 2008-05-07
why removing?? - only edit grub menu.lst to time out in 0 sec. and vista as primary boot option - (no one will care about ubuntu part less disk space)

---

### Post by _sAm_ on 2008-05-07
If your son installed Kubuntu the normal way, and you have the Vista disc, follow this guide here to fix the MBR for Vista:
[http://windowshelp.microsoft.com/Windows/en-US/Help/5c59f8c1-b0d1-4f1a-af55-74f3922f3f351033.mspx](http://windowshelp.microsoft.com/Windows/en-US/Help/5c59f8c1-b0d1-4f1a-af55-74f3922f3f351033.mspx)

Its easy and has graphical user interface. 

This will remove Kubuntu from the bootmenu. When you have done so you can reboot to Vista and just remove the partition Kubuntu are on.

If your son used wubi to install Kubuntu, meaning from within Vista, you can just uninstall it from add/remove in Vista, just as an normal application.

---

### Post by jimv on 2008-05-07
Tell your son to take it off, if he's computer savvy at all.

---

### Post by lagaile on 2008-05-07
Good idea jimv. :lolflag: I still have Vista. I don't have a Vista disc. How do I set it up to automatically connect to windows and not kubuntu? I'm afraid to fool around with it to much. Thanks for all your help. :)

---

### Post by benste on 2008-05-07
open a terminal
```
gedit /boot/grub/menu.lst
```

search the following lines:
```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
```

change them to
```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		0

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
```

search something like```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

(sda2 and hd0,1 coulöd be different for you) - copy your lines - delete all lines after ```
## ## End Default Options ##
``` (more than 20 lines :-)) and paste the copied windows section.


This is all you need :-)

---

### Post by benste on 2008-05-07
PS: afterwards - save it close all windows and reboot your computer

---

### Post by lagaile on 2008-05-07
Thanks benste...:wink:

---

### Post by benste on 2008-05-07
Short question, does nobody now what this blue and yellow button and the right bottom should be used for :-)

---

### Post by lagaile on 2008-05-07
thanks

---

