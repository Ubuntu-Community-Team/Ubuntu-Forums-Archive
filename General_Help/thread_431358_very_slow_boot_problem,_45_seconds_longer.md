---
title: "very slow boot problem, 45 seconds longer"
date: 2007-05-03
forum: General Help
---

### Post by curtk69 on 2007-05-03
hey , i recently was trying to change my screen resolution and started changing  things by first making a backup as per instructions below #1 , then i couldnt figure out how to finish so i didnt finish.

next day i notice it takes my comp a full 45 seconds on this black screen right after the nvidia splash screen and just b4 ubuntu login screen.
so now it takes more than 2 minutes total to bootup?

did i mess somethjing up ?
GDM uses a different Resolution than my Desktop

This problem is easily solvable; to fix it do the following:

1) Make a Backup of your xorg.conf

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

2) Open xorg.conf

gksudo gedit /etc/X11/xorg.conf

3) Locate your Screen Entry

Section "Screen"

You will find multiple entries similar to:

        SubSection "Display"
                Depth     24
                Modes    "1280x1024" "1024x768"
        EndSubSection

The First Entry in the "Modes" Line is what GDM will use, so change it to something lower/higher (Please make sure you know that your monitor and Graphic Card BOTH support this Resolution).

Save the file and close all running applications, restart GDM (/etc/init.d/gdm restart) and look if everything went fine.

If not you can always use:

sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf

to restore your system to the previous state.

CAN I FIX THINGS BY DOING THE RESTORE THING?
OR IS THIS EVEN THE CAUSE?

---

### Post by bikeboy on 2007-05-03
It's hard to tell if that's the cause. The best things to do are

a) return to the backup to see if it fixes the problem (make a copy of your modified xorg.conf too, because if it's not the cause you don't want to lose your resolution fixes).

b) install bootchart. "sudo aptitude install bootchart". It will log your entire boot process and store it as a .png image in /var/log/bootchart. Then you can have a look to see what the system is taking a long time to do. Or get someone more knowledgeable (probably not me) to have a look at it for you since it's not always easy to read :)

---

### Post by curtk69 on 2007-05-03
well doin the restore thing did nothing so i will try the bootchart thing

---

### Post by bikeboy on 2007-05-03
Ok, let us know if you need any more help with that. Hopefully you can sort it out, diagnosis is the first step.

---

### Post by hesaidit on 2007-05-03
question were u in root at the time???

also u could have tryed a res that was to hi for ur card that would slow things down.

---

### Post by pishcotec on 2007-05-03
hey, 
i have the same (?) problem. 
i already disabled network devices. i also have a problem with graphic startup (where to disable it?)
i attach [COLOR="DarkOrange"]bootchart[/COLOR] image of my boot, maybee someone can help me?

thanks a lot,

---

