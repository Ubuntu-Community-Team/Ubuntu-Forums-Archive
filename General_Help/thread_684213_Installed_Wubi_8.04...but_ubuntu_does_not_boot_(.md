---
title: "Installed Wubi 8.04...but ubuntu does not boot :("
date: 2008-01-31
forum: General Help
---

### Post by siddharth.unnikrishnan on 2008-01-31
hey...

Ive come across a peculiar case....I installed wubi 8.04-alpha-rev395.exe with the latest build of hardy heron (31st Jan) 

The problem is that even though ubuntu starts to load correctly, it gets stuck when it comes to _**'* Starting bluetooth'**_ and the system stays like that forever (the _**[OK]**_ never comes next to it) with no activity (no blinking hdd lights). I guess the *Starting bluetooth line comes just before loading ubiquity and hence I just cant get ubuntu to start :( ..

I tried everything from running chkdsk /r and inserting commands like 'apic=off noapic nolapic'. I also went into the menu and chose all the various options of booting, but nothin worked and it just gets stuck when it comes to _***Starting bluetooth**_.

Is there any way i can surpass this line? or any way i can get over this? or is there a way to deactivate this line?

plz help guys....

:(

regards...
Siddharth.

---

### Post by ago on 2008-02-01
try ctrl+alt+f2 and 

sudo /etc/init.d/bluetooth stop

---

### Post by siddharth.unnikrishnan on 2008-02-01
tried ctrl+alt+f2 and entering sudo /etc/init.d/bluetooth stop...but no use...

the system now stays inactive with **_*Stopping bluetooth_** and the [OK] sign never comes....

---

### Post by ago on 2008-02-01
Press esc boot in recovery mode and disable blooetooth as a service + blacklist it, there are a few guides on how to do that. Then when you have more time, consider filing a proper bug report. This is unlikely to be a wubi specific issue.

---

