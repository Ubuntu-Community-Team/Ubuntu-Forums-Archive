---
title: "How can i boot XP as default?"
date: 2006-09-12
forum: General Help
---

### Post by winther on 2006-09-12
Yeah, just installed Ubuntu as a dual boot to XP. It's cool and stuff, but the thing is, that now my pc boots to linux as default, after 10 seconds or some... So, how do i change this to boot into XP as default instead?

---

### Post by Thyamine on 2006-09-12
I believe you have to edit your boot/grub/menu.lst file.

Set Windows to be the default there.  I think you have to assign Ubuntu a different/higher number.

---

### Post by Obor on 2006-09-12
1. Backup your GRUB - (open terminal and paste the following, one line at a time)

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
gksudo gedit /boot/grub/menu.lst
```

2. menu.lst will open in a new window

To change default time - Find this line  - 
timeout     10

and change 10 with number of seconds of your choice

3. To change default OS to load find this line 
default     0

and change 0 to number in sequence where Win XP is. (just note that the sequence starts with 0 and separator between ubuntu and windows counts as one as well) ie if windows is 4th in the list including the separator the sequence noumber is 3
[URL="http://ubuntuguide.org/wiki/Dapper#How_to_change_the_timeout_seconds_for_GRUB_menu_on_boot-up"]
more info in ubuntu guide[/URL]

---

