---
title: "Opera 30 bookmarks on 14.04 inconsistent"
date: 2015-06-22
forum: General Help
---

### Post by jamesisin on 2015-06-22
I have the same repository on two different if highly similar Lenovo laptops (a w500 and a w520):

[http://deb.opera.com/opera/](http://deb.opera.com/opera/)

They are both running Opera 30 (sudo apt-get install opera-stable) yet they are not the same.  This confuses me.

The w500 looks like older versions of Opera and is missing some features from the bookmarks dialogs.  Here is the screenshot from the w520:

[ATTACH=CONFIG]262786[/ATTACH]

The w500 is at home so I can't attach a screenshot at the moment, but suffice it to say the timestamp (at the top) and the Remove button do not appear.

What's up with that?

I tried creating a new user account on the w500 to satisfy myself it was not a configuration issue with my user account.  Same behavior.

Thanks for taking a look.

---

### Post by CantankRus on 2015-06-22
The one in your pic must not be up to date.
I have both opera-developer(32.0.1899.0) and opera-stable(30.0.1835.59) installed and both show as in below pic.
When you hover your mouse over the popup a circle icon appears for adding to speed dial.

Is the opera ppa still enabled on both computers?
If you enter in the address bar  
```
opera://about
```
it will tell you if you have the latest version.

---

### Post by jamesisin on 2015-06-22
I'll have to check the machine when I get home, but your image is the old version.  The machine I am typing on now is the newer version I posted in the OP.

This machine:  30.0.1835.59 - Opera is up to date.

I have run apt-get today.  I have no additional updates available.

---

### Post by CantankRus on 2015-06-22
> **jamesisin said:**
> I'll have to check the machine when I get home, but your image is the old version.  The machine I am typing on now is the newer version I posted in the OP.

This machine:  30.0.1835.59 - Opera is up to date.

I have run apt-get today.  I have no additional updates available.

Maybe they decided to go with the older simplified version of bookmarks then.
I recall seeing as in your pic before but not now.

---

### Post by CantankRus on 2015-06-22
Go to **opera://flags** and search for **pop-up**
Enable the "Improved bookmark pop-up"

---

### Post by jamesisin on 2015-06-23
I was able to confirm version last night.

> Version:	30.0.1835.59 - Opera is up to date

[ATTACH=CONFIG]262807[/ATTACH]

I will take a look at that setting this evening.  Thanks.

---

