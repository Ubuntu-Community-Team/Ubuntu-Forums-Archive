---
title: "vnstat not changing the start of the month [day]"
date: 2016-05-15
forum: General Help
---

### Post by fbird3 on 2016-05-15
Hi, there
I have searched a lot before coming here [I even e-mail the program's author, but no luck yet].
Basically, vnstat is supposed to start accumulating data from day one of every month unless we reconfigure it otherwise [which I did].
Short of removing and reinstalling it [what for, really...? the program works fine, except for that], I will try installing a newer version, if possible.
There is an outside chance that the program will 'get into gear' next month [I changed the configuration file mid-month; stil...], but I am trying to sort it out now.
Any suggestions are welcome.

---

### Post by Habitual on 2016-05-15
What is this "configuration" you are mentioning?
```
vnstat -v 
```
ouput please

---

### Post by fbird3 on 2016-05-16
Hi, Habitual

vnstat -v
vnStat 1.10 by Teemu Toivola <tst at iki dot fi>

The "configuration", though, refers to one line on the /etc/vnstat.conf file which, according to its own man page, is "Config file that will be used unless $HOME/.vnstatrc exists.". More precisely:

# on which day should months change
MonthRotate 10

The line above comes configured to "MonthRotate 1"; following the instructions above from its man page, I changed it to 10, because that's when my wireless broadband internet provider starts a new billing period.
Not once have I found comments about this declared feature working correctly [please, refer to its own website [http://humdi.net/vnstat/](http://humdi.net/vnstat/), where it is stated that "months can be configured to follow billing period"].
That is all.
I hope you can shed some light in this not too bright tunnel...

---

### Post by Habitual on 2016-05-16
My unedited /etc/vnstat.conf (v 1.11)
has
```
# on which day should months change
MonthRotate 1
```

Anytime you make a change you should "bounce the service" (restart vnstat) and I am not sure how that's done on your OS.
Used to ```
service vnstat restart
```

Odd. my vnstat.conf shows it, but the man page has no mention of MonthRotate

---

### Post by fbird3 on 2016-05-16
I have restarted vnstat as you suggested [no problems there, but I had to use the command sudo, though], at least no error messages...]; so far, it has done nothing to its displayed results.
I'll keep trying once daily [who knows...?] and hopefully by next month 10th [sad necessity...!], it could change the MonthRotate day for the displayed results.
The man page does not mention MonthRotate per se, only the configuration file from which I got that variable [MonthRotate]. But its website mentions it by name and intended purpose.

---

### Post by fbird3 on 2016-05-17
Having been in contact by e-mail with vnstat's author, Teemu Toivola, it was revealed that [as I suspected/hoped for] the new setting to MonthRotate will not take effect on the same month that it was done; so I will definitely have to wait until June 10th to confirm this feature of vnstat. Until then, I will keep this thread open.
Oddly enough, despite my intense searching for an answer to this fact, I never read any explanation for it anywhere else; well, there is one now, right here!
Thank you, Habitual, for the assistance.

---

### Post by Habitual on 2016-05-17
Glad to be of "help".

---

### Post by fbird3 on 2016-06-11
I have finally confirmed that MonthRotate does change after all.
I hope this thread will be of some assistance to vnstat users with the same difficulty.

---

### Post by Habitual on 2016-06-11
Glad it worked out!

---

