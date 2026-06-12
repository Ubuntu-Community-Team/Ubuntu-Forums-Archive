---
title: "Midnight Download with crontab - Have I set it up right ??"
date: 2006-12-16
forum: General Help
---

### Post by Portable_Jim on 2006-12-16
Am running Dapper.

This is what I would like to happen:
"I leave my computer on and go to bed. At 10 minutes past 12 midnight my computer executes the command 'wget -c [http://ftp.osuosl.org/pub/ubuntu-releases/6.10/](http://ftp.osuosl.org/pub/ubuntu-releases/6.10/) by 'me' At 6 AM the computer executes the command 'killall wget' also by 'me', to stop wget. Then 10 minutes later root turns off my computer."

Is my 'crontab -e' correct:
10 0 * * * wget -c [http://ftp.osuosl.org/pub/ubuntu-releases/6.10/ubuntu-6.10-desktop-i386.iso](http://ftp.osuosl.org/pub/ubuntu-releases/6.10/ubuntu-6.10-desktop-i386.iso)
0 6 * * * killall wget

is root's 'crontab -e' correct:
2 6 * * * shutdown now

Another question, Do I have to be logged in for the cron job to work??

---

### Post by Portable_Jim on 2006-12-16
bump

---

### Post by dcstar on 2006-12-16
> **Portable_Jim said:**
> Am running Dapper.

This is what I would like to happen:
"I leave my computer on and go to bed. At 10 minutes past 12 midnight my computer executes the command 'wget -c [http://ftp.osuosl.org/pub/ubuntu-releases/6.10/](http://ftp.osuosl.org/pub/ubuntu-releases/6.10/) by 'me' At 6 AM the computer executes the command 'killall wget' also by 'me', to stop wget. Then 10 minutes later root turns off my computer."

Is my 'crontab -e' correct:
10 0 * * * wget -c [http://ftp.osuosl.org/pub/ubuntu-releases/6.10/ubuntu-6.10-desktop-i386.iso](http://ftp.osuosl.org/pub/ubuntu-releases/6.10/ubuntu-6.10-desktop-i386.iso)
0 6 * * * killall wget

is root's 'crontab -e' correct:
2 6 * * * shutdown now

Another question, Do I have to be logged in for the cron job to work??

Cron does not know where all of your commands exist since it doesn't run in a shell environment.

Put in an explicit path for all referenced commands.

---

### Post by Portable_Jim on 2006-12-17
> **dcstar said:**
> Cron does not know where all of your commands exist since it doesn't run in a shell environment.

Put in an explicit path for all referenced commands.
Please explain.

---

### Post by Portable_Jim on 2006-12-17
Problem solved thanks to d4x.
> sudo aptitude install d4x

---

