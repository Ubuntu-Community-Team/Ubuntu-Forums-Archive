---
title: "Dell Optiplex gx110"
date: 2013-01-12
forum: General Help
---

### Post by maxwille on 2013-01-12
Hello,
 
I have an old Dell Optiplex gx110 wich originaly ran Windows 2000 pro.
The previous owner installed Windows xp pro on his name (I found out what the password was),I used the computer for about 5 years, and then I forgot all about it when I discoverd it was filled with old files, I tried reinstalling xp but it only became worse! The icons and the task bar became big, properties was unreachable etc. I tried to 
[COLOR=black][FONT=Tahoma][SIZE=2]change resolution but it did not help. Then I tried to install ubuntu I used the ubuntu boot helper because the computer would not boot from cd witch is strange! I am not sure what happened but the computer stopped working. It would start loading dell write an error message and restart! Could anyone explain the problem? Is it fixable?[/SIZE][/FONT][/COLOR]
 
Thank you in advance!
Victor

---

### Post by tgalati4 on 2013-01-12
Open the machine, blow out the dust, reseat all of the cards, ribbons, connectors.  Try again.

Many times, the power supply goes out on these older machines because of bad capacitors.  Check the 5VDC and 12VDC with a meter, or boot into BIOS if you can and check the voltages under "Health Monitoring".

Take the machine to your local Linux User's Group.  They will know exactly what to do with it.  Although don't be surprised if it ends up in a battle-robot ring!

---

### Post by maxwille on 2013-01-12
[COLOR=black][FONT=Tahoma][SIZE=2]Hello,[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Tahoma][SIZE=2][/SIZE][/FONT][/COLOR] 
[COLOR=black][FONT=Tahoma][SIZE=2]I tried unplugging everything and plugging it back again (my hard drive was barely plugged)[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Tahoma][SIZE=2]but unfortunately it did not work! And the computer still will not boot from a live cd.[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Tahoma][SIZE=2]This is what the computer wrights:[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Tahoma][SIZE=2]Invalid BOOT .INI file[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Tahoma][SIZE=2]Booting from C:\winnt\[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Tahoma][SIZE=2][/SIZE][/FONT][/COLOR] 
[COLOR=black][FONT=Tahoma][SIZE=2]Then the screen changes and it wrights:[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Tahoma][SIZE=2][/SIZE][/FONT][/COLOR] 
[COLOR=black][FONT=Tahoma][SIZE=2]Windows could not start because the following file is missing or corrupt[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Tahoma][SIZE=2]<Windows root>\System32\hal.dll.[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Tahoma][SIZE=2]Please re-install a copy of the above file.[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Tahoma][SIZE=2][/SIZE][/FONT][/COLOR] 
[COLOR=black][FONT=Tahoma][SIZE=2]What does that mean? how can I reinstall it?[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Tahoma][SIZE=2]And can I boot from a live cd?[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Tahoma][SIZE=2]Thank you in advance,[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Tahoma][SIZE=2]Victor[/SIZE][/FONT][/COLOR]

---

### Post by mörgæs on 2013-01-12
You are booting from the hard disk, not from the CD.

Look closely for messages during boot, especially regarding which F-key to push in order to control the boot sequence. I guess it's F12, but could also be F2.

Here is some advice for a slightly newer computer:
[http://ubuntuforums.org/showpost.php?p=12292664&postcount=828](http://ubuntuforums.org/showpost.php?p=12292664&postcount=828)

---

### Post by maxwille on 2013-01-12
[COLOR=black][FONT=Tahoma][SIZE=2]Hello,[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Tahoma][SIZE=2][/SIZE][/FONT][/COLOR] 
[COLOR=black][FONT=Tahoma][SIZE=2]I tried booting from cd and it only sais "press F1 to try again or F2 to boot menu"[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Tahoma][SIZE=2]cd drive works but does not recognize cd![/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Tahoma][SIZE=2]How can I fix this?[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Tahoma][SIZE=2][/SIZE][/FONT][/COLOR] 
[COLOR=black][FONT=Tahoma][SIZE=2]Thank you in advance,[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Tahoma][SIZE=2]Victor[/SIZE][/FONT][/COLOR]

---

### Post by tgalati4 on 2013-01-12
Exactly what disk are you trying to boot from?  Sometimes CDROM drives go bad--the sensors oxidize or get too dirty to read correctly.  You can clean them by taking them apart or find another one to put inside.

---

### Post by maxwille on 2013-01-12
Hello,
 
I tried to boot from a ubuntu and windows xp cd.
Should I buy a new cd drive?
 
Thank you in advance,
Victor

---

### Post by mörgæs on 2013-01-12
This old fellow certainly does not work with Ubuntu. As mentioned in my link an alternate Lubuntu is your best choice.

How much memory does it have?

---

### Post by maxwille on 2013-01-13
Memory on my computer or cd?

---

