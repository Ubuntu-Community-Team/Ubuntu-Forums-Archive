---
title: "evolution calendar sync with palm treo 680"
date: 2007-05-07
forum: General Help
---

### Post by janbockaert on 2007-05-07
Hi,

first the good news, i can sync evolution with my very new treo 680. Contacts work, file installation works, backup seems to work, and todo's work if i give them a due date. (without date, syncing hangs, there is a bug filed for this in launchpad).

However, i had to add visor in /etc/modules before my treo got recognized. And i had to connect (in gpilot) to /dev/ttyUSB1

(look here for how to add the visor module: [http://ubuntuforums.org/showthread.php?t=417118](http://ubuntuforums.org/showthread.php?t=417118))

but now the strange news:

Before i synced the treo 680, i backed up my old treo 600. The folder i used for syncing the 600 is home/username/treo600

When i added the treo 680 i told gpilot to sync at the standard /home/username/Mypilot  folder (i didn't want to restore the treo 600 database on the Treo 680). However, this folder stayed empty, and al the new data came in the /home/username/treo600 - folder. After deleting the treo600 folder, and doing a new sync (with the treo 680) gpilot recreated the treo600 folder, and put the backup in that place. Deleting the treo 600 from gpilot also did not help.
Any idea how i can force gpilot to use the MyPilot folder? (There is no need any more for any trace of my old treo 600 on my computer)

But now the sad news. 

I appears, i can not sync my calendar... There are no errors in the log, but there are also no calender events synced to my personal calendar in Evolution. Any idea how i can solve that problem? It must be my fault, because i seems to be the onlyone in this forum who is having this problem. i guess i m doing something obvious wrong.

thanks

jan

---

### Post by janbockaert on 2007-05-08
apparently, syncing with calendar works, but not with the standard calendar in evo. Creating a new calendar is another workaround i can live with.

This seems to be an evolution problem. Maybe because of the way i put my .evolution folder back after the update to feisty fawn.

Still if there is anyone who knows how to force gpilot to use the MyPilot folder instead of my old treo600 folder, please share.

---

### Post by ByteDoc on 2007-05-18
Working with a Palm Tungsten E2, can confirm the two steps (adding visor to /etc/modules and using /dev/ttyUSB1).

To thrown in another question: How can I sync multiple calendars from evolution to the palm?
Is this possible using gnome-pilot, or with any other snyc software?

---

### Post by mello on 2007-05-30
Treo 650, ubuntu 7.04. Worked fine here. Thanks!

---

### Post by ljoslin on 2007-08-31
I got my phone to sync, but I can't get MP3s to move over, I would love to get rid of my ipod!  If any one has had any success with this please tell me!  I don't have a card reader on my computer so that option is out for right now!

-=Larry=-

---

