---
title: "little help!!"
date: 2008-04-02
forum: General Help
---

### Post by gaza14 on 2008-04-02
hey i just installed linuxe on my computer after windows and gave it a partitioned space of 20gb and all through the set up it was fine. i then tried [this]("http://http://ubuntuforums.org/showthread.php?t=224351") but stil and error 17 comes up.

any help would be appreciated.

---

### Post by ibuclaw on 2008-04-02
I presume its a problem with booting up Ubuntu?

Try these steps carefully:
```

 o  Enter BIOS

 o  Make sure all HDD's are detected. 
     Take down notes of of the current settings for them,
     incase you have to restore them back later.

 o  Search for the HDD that has Ubuntu  installed and set its **MODE** to **AUTO**
     (IF the setting says LBA, large, or normal, change it.)

 o  If you have this option available, set **TYPE** to** USER**,
     but** don'**t change any of the figures that were automatically detected.

 o  Save the settings, and reboot.

```
If this doesn't work, set the settings back to their originals and we'll think of another way.

Regards
Iain

---

### Post by ugm6hr on 2008-04-02
If you install Ubuntu after Windows, it will install Grub as default.

Why did you need to install it manually?

---

