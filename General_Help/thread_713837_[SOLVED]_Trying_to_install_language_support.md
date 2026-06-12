---
title: "[SOLVED] Trying to install language support"
date: 2008-03-03
forum: General Help
---

### Post by Spacenoodle on 2008-03-03
Hi, 

So this is the first time i've used Ubuntu, and so far it's going well. However i'm trying to install Korean language support and Korean Keyboard input on the system and it doesn't seem to work. 

I've installed the keyboard, however i can't yet use it, but as far as language support (having the menu items in Korean) i can't seem to install anything. I go to System - Admin - Language Support but i only see English , and there is no options to add another language.

Can anyone please help? 

P.S can anyone recommend a good IRC client for Ubuntu?

---

### Post by kesman on 2008-03-03
Check out applications -> add/remove programs and search for language support. Xchat is a good graphical IRC-client for linux.

---

### Post by erginemr on 2008-03-03
For the IRC; you should definitely install XChat, which kind of *rulez*.

---

### Post by Spacenoodle on 2008-03-03
Ah, Ok when i do that i have a problem , it says the list of apps is out of date, then i download the new list, click on a program, and it tells me the list of apps is out of date again, and i keep going in circles. any suggestions?

---

### Post by kesman on 2008-03-03
close the add/remove and open up terminal from accessories. Type in it:
```

sudo apt-get update
sudo apt-get dist-upgrade

```
and wait for it to finish these two steps. Then try again with add/remove programs.

---

### Post by Spacenoodle on 2008-03-03
EDIT: Scratch that, i checked some boxes and things seem to be working now. Still not sure about how to get Korean installed however or how to enable the Korean keyboard, Korean keyboards like the one i'm using typically have a button which replaces the right alt key which toggles between Korean and English.

Also, when i expand the list of files which are downloading while i'm installing xchat, alot of the files are named twice, one with a URL which is CDROM:// and next to them a it says "failed" and then a regular URL, which says done. SO  i'm guessing that the problem before was that the package manager was trying to grab files from CD rather than over the net, how do i disable that? or does it not matter now?

---

### Post by erginemr on 2008-03-03
From Main Menu -> Administration -> Language Support, when I check Korean, it starts to download language support files (16 in total). 

Once that is done, you should select Korean as the default language from the drop-down menu below and restart our computer. 

Also at the gdm login screen, do not forget to select your default session language as Korean.

---

### Post by erginemr on 2008-03-03
I dn't know if this is necessary for Korean, but you may also need to spend some time in SCIM support tool...

---

### Post by kesman on 2008-03-03
To disable cdrom as a software source, go to system -> administration -> software sources and remove cdrom. Also make sure you have all the sources enabled, this provides you a lot more applications and updates.

---

### Post by Spacenoodle on 2008-03-03
Ok fantastic!! The problem the whole time was the software sorces, once i turned that off everything worked, Thanks for all the help!

---

### Post by erginemr on 2008-03-03
Annyong ha shimnikka,

Great! Have Fun with Ubuntu in your own language! ):P

---

