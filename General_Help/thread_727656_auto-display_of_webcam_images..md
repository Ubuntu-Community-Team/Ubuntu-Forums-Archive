---
title: "auto-display of webcam images."
date: 2008-03-18
forum: General Help
---

### Post by robfindlay on 2008-03-18
I have installed apache as per the ubuntu guide for Gutsy i have it up and running, phundle.getmyip.com 

I have my webcam saving pics to a directory in the /var/www/ what I would like to know is if there is some script....or plugin or something, that would take the pics in that directory and auto-generate an html page, SOOOOO you could open it up and see lets say the most recent image and thumbnails of the last 10 or 30? 

Or even just thumbs of the last 10 or 30 instead of a bare directory like I have now. 

TIA

-R

---

### Post by robfindlay on 2008-03-18
> **robfindlay said:**
> I have installed apache as per the ubuntu guide for Gutsy i have it up and running, phundle.getmyip.com 

I have my webcam saving pics to a directory in the /var/www/ what I would like to know is if there is some script....or plugin or something, that would take the pics in that directory and auto-generate an html page, SOOOOO you could open it up and see lets say the most recent image and thumbnails of the last 10 or 30? 

Or even just thumbs of the last 10 or 30 instead of a bare directory like I have now. 

TIA

-R


Okay found "album" can someone tell me how to setup a cronjob to run album every lets say hour or so? 


-R

---

### Post by robfindlay on 2008-03-18
Please?  a quick reply ?  HELP 

What would the CRON line look like? 

-R

---

### Post by outofnicks on 2008-03-18
use crontab.
that's for user cron jobs.

[http://www.adminschoice.com/docs/crontab.htm](http://www.adminschoice.com/docs/crontab.htm)

First, set your default editor for crontab with the following terminal command:
```
export EDITOR=vi
```

Replace "vi" with your text editor of choice--I used bluefish.

Then do:
```
crontab -e
```

The directions on that link will tell the rest.

---

### Post by robfindlay on 2008-03-19
> **outofnicks said:**
> use crontab.
that's for user cron jobs.

[http://www.adminschoice.com/docs/crontab.htm](http://www.adminschoice.com/docs/crontab.htm)

First, set your default editor for crontab with the following terminal command:
```
export EDITOR=vi
```

Replace "vi" with your text editor of choice--I used bluefish.

Then do:
```
crontab -e
```

The directions on that link will tell the rest.

gnome-schedule 

Will actually write your crontab file for you.  :-)

---

