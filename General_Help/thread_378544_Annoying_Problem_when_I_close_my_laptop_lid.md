---
title: "Annoying Problem when I close my laptop lid"
date: 2007-03-07
forum: General Help
---

### Post by linuxbun on 2007-03-07
I have checked the bios settings and set it to "stay active" when I close the lid (on both battery and power) and I have gone to power management and set it to "Do Nothing" when I close the laptop screen it goes to the login screen.

It's so annoying! It's annoying me so much that I'm seriously thinking about physically disconnecting the switch to stop it detecting that I'm closing the laptop lid.

Any suggestions before I resort to drastic measures??? :(

---

### Post by DagMan on 2007-03-07
look in /etc/acpi and see if there is a file called lid.sh or something similar and if so, back it up then make it an empty file. 
There is also a setting for this in the gconf-editor but I think it is the same value that power management is toggling.

Just curious, what brand and model of laptop is it?

---

### Post by linuxbun on 2007-03-08
> **DagMan said:**
> look in /etc/acpi and see if there is a file called lid.sh or something similar and if so, back it up then make it an empty file. 
There is also a setting for this in the gconf-editor but I think it is the same value that power management is toggling.

Just curious, what brand and model of laptop is it?


It's a Dell Latitude C640. Did that, unfortunately it didn't fix the problem :( :(

---

### Post by ddumanis on 2007-03-08
I have the same computer. A good workaround is to change your power management setting from "Do Nothing" to "Blank Screen."

---

### Post by linuxbun on 2007-03-08
> **ddumanis said:**
> I have the same computer. A good workaround is to change your power management setting from "Do Nothing" to "Blank Screen."

I tried all workarounds via power management, neither worked for me.

However, I have found a fix!!!!!!!!!!!!!!! :) :) :)

```
sudo cp /etc/acpi/events/lidbtn /etc/acpi/events/lidbtn.BKUP
```
```

sudo nano /etc/acpi/events/lidbtn
```

Comment out action=/etc/acpi/lid.sh.

(or do: "Underneath that line, put in /etc/acpi/hibernate.sh" ) I didn't do this because I only ever close my laptop screen to transport it to the next room and want it to be ready immediately.

Save the file (ctrl+O in nano), close it (ctrl+X in nano) and restart acpi with

```
sudo /etc/init.d/acpid restart
```



Works like a treat! And I thankfully didn't have to take a screwdriver to the poor thing, lol :lolflag:

---

### Post by ppietryga on 2007-03-17
THANK YOU!!
I was having same problem with my computer (Dell c610) and trying to fix it for the last week.
Now it works.

Thanks again :) :lolflag:

---

### Post by linuxbun on 2007-03-17
> **ppietryga said:**
> THANK YOU!!
I was having same problem with my computer (Dell c610) and trying to fix it for the last week.
Now it works.

Thanks again :) :lolflag:
Yay i helped someone :KS :KS :KS 

Glad it works, f'in annoying when this isn't set, lol.

---

### Post by lophyte on 2007-03-20
Wow, this is awesome! Thanks a lot, I've been having this problem for a while now. I wrote a small script that I like to use for closing my lid. You can find it below.

First, backup your lid.sh file.
```
sudo mv /etc/acpi/lid.sh /etc/acpi/lid.sh.backup
```

Then, open a new one.
```
sudo nano /etc/acpi/lid.sh
```

And enter the following script:
```

#!/bin/sh

grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]; then
        # if closed
        radeontool light off
else
        # if open
        radeontool light on
fi

```

Then, be sure to restart acpid.
```
sudo /etc/init.d/acpid restart
```

This script simply blanks your screen when you close the lid, which, in theory, saves battery power.

---

### Post by linuxbun on 2007-03-21
The above didn't work on my dell :confused: 

However if I did:

sudo nano /etc/acpi/events/lidbtn


and replaced

action=/etc/acpi/lid.sh

with

action=/etc/acpi/screenblank.sh

That turned off the screen and resumed it when you opened it up! Bingo :KS

---

### Post by mr_jrdn on 2007-05-28
I tried all of these on my Dell 600m and none of them worked. Every time I close my laptop lid and reopen it, I am required to provide a password. the screen does blank out, but it is really annoying to have to provide a password every time i close the lid for a few minutes. I'm running Feisty Fawn, any suggestions besides just setting my screen to do nothing when i close the lid?

---

### Post by strabes on 2007-05-28
Sorry for the semi-answer but KDE handles all of this no problem. Make the switch. You'll be glad you did. ```
sudo aptitude install kubuntu-desktop
```

---

### Post by mr_jrdn on 2007-05-31
Well I was just going to live with it, it isn't really a big problem or anything. However, I was playing around with my power management settings, and it seems that if i set my laptop to "do nothing" while on battery power and while on ac power, my screen does just what I want it to do. This seems strange to me, but I'm not going to complain!

---

### Post by Dougle on 2007-08-21
This problem is really annoying me, my media buttons don't work when the lid is closed because the system is locked.

Any more ideas out there? none of the above .sh mods worked for me (lots of different ways to make the screen blank, but still the login prompt)

Cheers, Dan

---

### Post by Dougle on 2007-08-21
in terminal run gconf-editor or find it in system->preferences

uncheck
/apps/gnome-power-manager/lock_on_blank_screen

Done

---

