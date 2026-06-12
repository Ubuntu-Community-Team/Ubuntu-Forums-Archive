---
title: "Wubi Boot Menu duplication?"
date: 2007-11-13
forum: General Help
---

### Post by anon2243 on 2007-11-13
I noticed that ubuntu-linux menu item on boot is listed twice, once beneath vista and once inside of the legacy menu.  Is this on purpose?

---

### Post by ago on 2007-11-13
not sure what a legacy menu is

---

### Post by anon2243 on 2007-11-19
right now im dual booting xp and vista and b4 using wubi my boot menu looked like this (sorry):

legacy menu -> windows xp home
windows vista home

the legacy menu being a sub menu in the boot order

after installing wubi it looks like this:

legacy menu -> windows xp home
----------------------ubuntu-linux
windows vista home
ubuntu-linux

---

### Post by ago on 2007-11-19
Yes this is normal, it's difficult for us to understand how nested widnows bootloaders are configured, so we avoid any issue by installing in any bootloader we find, uninstalling ubuntu will remove all wubi entries, to remove a single entry you have to do it manually by editing boot.ini (XP) or easybcd (vista)

---

### Post by anon2243 on 2007-11-20
thanks for the replay...boot.ini shows no vista or ubuntu-linux entries since vista becomes the standard when installed (bcd)

when i used easybcd it showed no entries for ubuntu....just what the menu should look like when i uninstall...

any suggestions?

because actually before installing ubuntu i had my menu set up (via easybcd) that there would be no nested menus just this:

xp home
vista home

but wubi seemed to default to nests and place itself twice

---

### Post by Computer Guru on 2007-11-23
EasyBCD | Tools | Edit Legacy Entries

Delete the Wubi line from there (back it up first)
Save and exit notepad.
 
EasyBCD | Add/Remove Entries | Linux -> Wubi
Add Entry
Exit EasyBCD and reboot to test.
 
(you need to be using EasyBCD 1.7.1)

---

### Post by anon2243 on 2007-11-25
> **Computer Guru said:**
> EasyBCD | Tools | Edit Legacy Entries

Delete the Wubi line from there (back it up first)
Save and exit notepad.
 
EasyBCD | Add/Remove Entries | Linux -> Wubi
Add Entry
Exit EasyBCD and reboot to test.
 
(you need to be using EasyBCD 1.7.1)

Im sorry but the adding of wubi did not work as it just created a new C:\nst folder with a different menu.lst and neogrub file that didn't work.  When i copied and renamed the fiels from the /ubuntu/winboot directory to the nst folder the ubuntu boot worked

---

### Post by Computer Guru on 2007-11-26
Sounds like EasyBCD couldn't see your other menu.lst file...
 
The default neogrub file should have searched for, found, and loaded-up Wubi's menu.lst.... it would help if you could tell me what it said before you replaced it?

---

### Post by anon2243 on 2007-11-26
Im not sure what it said cause it happened so fast and dropped me to terminal....

Does it help if I say i ran the whole easybcd from my C: partition and the ubuntu/winboot was installed on my D: partition?

---

### Post by Computer Guru on 2007-11-27
It shouldn't matter since EasyBCD/NeoGrub will search for the winboot folder + files on *all* drives... but I really can't say without any more info.
 
I'm glad you've got your system working though, I guess that's what matters...

---

### Post by Computer Guru on 2007-11-30
OK, I think this is probably because the latest versions of EasyBCD have been re-configured to work with the 7.10 Wubi release, and not the older versions.

(In 7.10 the path was changed to \ubuntu\winboot\menu.lst)

---

### Post by anon2243 on 2007-11-30
Sorry I am running the 7.10 release...

D:\ubuntu\winboot\menu.lst

It didn't seem to find it and just created its own Neogrub which wasn't the same size as the wubidr one...thats how i knew something was wrong.

---

### Post by Computer Guru on 2007-12-02
OK, can I bother you to add a Wubi entry in EasyBCD 1.7.1?

(it won't modify your working dual-boot, just add a second entry that won't work)

When I do that, I get this in my NeoGrub's menu.lst:
```
# NeoSmart NeoGrub Bootloader Configuration File
#
# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst
# Please see the EasyBCD Documentation for information on how to create/modify entries:
# http://neosmart.net/wiki/display/EBCD

find --set-root --ignore-floppies \ubuntu\winboot\menu.lst
configfile \ubuntu\winboot\menu.lst

# All your boot are belong to NeoSmart!
```

Basically, it will search for Wubi's menu.lst, and load it up.
On my computer, this works OK.

Is your \NST\menu.lst file the same as mine?

---

### Post by anon2243 on 2007-12-02
Yeah its the same but maybe to search a different partition one wold have to add the hd(0,1) <<im not sure of syntax on that....before the /ubuntu/...

---

### Post by Computer Guru on 2007-12-05
No, that should work as-is.

Because I can't guarantee that all users will have it on hd(0,1), I tell NeoGrub to searh all HDs on the following path for the Wubi menu.lst file :)

---

