---
title: "How to change Calendar to Monday on PopOS / Ubuntu Gnome or in KOganizer?"
date: 2020-12-08
forum: General Help
---

### Post by Keen101 on 2020-12-08
I know this is an old problem from many years ago, but I can't seem to find an applicable answer in 2020 or even from 2019 that will work. Frustrating as i hear even modern Windows machines have this option to change.

I live in the U.S., and I understand that convention and locale settings for the U.S. dictate that the calendar weekdays start on Sunday. However even as an American, this bugs me as Sunday is considered to be the "weekend". Therefore I like to be like Europe and Australia and have my Calendars start on Monday. How do i change this in the default PopOS / Ubuntu Gnome calendar without changing my other locale settings?

Looking in "Region and Language" settings only allows me to change by country convention, which does not work for me as i would still like to use US-Letter settings for my printer and use Imperial Settings, u.s. time and date conventions, etc. Except for the start day of the week.

Or how do i change this is KOrganizer to allow me to print out a phsical calendar that starts with Monday? I seem to remember years ago the old KDE Kalendar app let me print out calendars that started with monday, and while KOrganizer has the option to set monday as the start day it does not actually change anything (a bug?).

Any ideas? Any alternative Calendar apps to KOrganizer that will let me print out a physical calendar with Monday at the start day?

---

### Post by #&amp;thj^% on 2020-12-08
Try adding or changing this:
```
LC_TIME="en_GB.UTF-8"
```
That will start your week at Monday, and leave your other desired settings intact.
EDIT:>I keep forgetting not all users are advanced/experienced.
"en_GB.UTF-8" locale should be per-generated before setting LC_TIME it done like this (sudo dpkg-reconfigure locales) 
```
sudo dpkg-reconfigure locales
```
The file to edit is in **"/etc/default/locale"**

---

### Post by #&amp;thj^% on 2020-12-10
I have not seen you since your request for help, I'll take that as not SOLVED then.
Here's a one liner for your ease:
```
sudo localectl set-locale LC_TIME="en_GB.UTF-8"
```
Then You'll need to run:
```
sudo locale-gen
```
Now you will need to logout or some have told me they had to reboot to see the change.
```
$ locale
LANG=en_US.UTF-8
LANGUAGE=en_US
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME=en_GB.UTF-8
LC_COLLATE=C
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"

```
Good Luck.

---

