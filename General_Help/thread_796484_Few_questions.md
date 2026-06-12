---
title: "Few questions"
date: 2008-05-16
forum: General Help
---

### Post by xoligy on 2008-05-16
1. Im playing with a script on a localhost and want to check the mail that is sent from the script how would i go around doing that? (i have lamp installed)

2. Sometimes firefox closes for no apparent reason (latest ubuntu and firefox) at a guess im saying its something to do with javascript but im unsure anyone else have this? (i have imacros installed im guessing that and java are a problem)

3. Cronjobs, i want to get these working as the script im messing with uses them and i carnt do some work with out them :( here is one way i tried:
> 
xoligy@xoligy-desktop:~$ crontab -l
15 * * * * sh /home/public_html/work/cronfile/cron.php

How i did the above: made a file in nano, saved it as cron typed what a site said and nothing happend haha, did try another way but i canna remember what i wrote!

4. I treid the nvidia driver that comes with ubuntu with my 6600gt gfx card, home come the screen res drops from 1600 to 1240? Also even tho i get sound the volume control dont work :confused: (onboard sound)

Thanks for any help it is appreciated!

---

### Post by nhandler on 2008-05-17
1) Let me try and get this straight. You have a script on your computer that sends emails to people, and you want to check the messages that are being sent? If that is the case, either modify the script to send you a copy of the messages, or have it also log all messages to a text file.

2) Without more information, this will be difficult to diagnose. Do you know what site(s) you were visiting when firefox closed? Just to be safe, could you post the version of firefox, java, and ubuntu that you are running? I just want to verify that you are running the most recent version.

3) You can edit your crontab by entering 'crontab -e' in a terminal. Cron is used to run a certain command at a certain time/date. For example, that crontab line is running the script every hour on the 15 minute mark (1:15, 2:15, 3:15, etc). You should also you the absolute path of sh (/bin/sh) instead of plain old 'sh'. This is due to cron not having the same path as you.

4) I can't help you with this.

---

