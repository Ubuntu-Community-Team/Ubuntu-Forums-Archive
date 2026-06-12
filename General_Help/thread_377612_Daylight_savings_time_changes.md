---
title: "Daylight savings time changes"
date: 2007-03-06
forum: General Help
---

### Post by AusIV4 on 2007-03-06
Most of you have probably heard that the start time for daylight savings time has changed in the United States. Initially, it was in about two weeks, but now it's this coming Sunday. There was a big deal about Windows not adjusting properly to the new DST beginning, and I'm wondering if the problem has been fixed for Ubuntu.

I leave for spring break on Friday, and won't be back for over a week. I also run a MythTV box, which is dependent on the current time for recording shows. If my box doesn't update the time properly, it will be an hour behind and nothing it records will be what I wanted.

Can anyone tell me for sure whether or not Ubuntu features corrections for the new DST? If not, does anyone have a script I could add to cron that would update my clock?

Thanks,
- AusIV

[EDIT]
I found [this thread](http://ubuntuforums.org/showthread.php?p=2068322). It said to run

```

xxx@xxx:~$ sudo zdump -v /etc/localtime |grep 2007

```
and if you got:
```

/etc/localtime Sun Mar 11 07:59:59 2007 UTC = Sun Mar 11 01:59:59 2007 CST isdst=0 gmtoff=-21600
/etc/localtime Sun Mar 11 08:00:00 2007 UTC = Sun Mar 11 03:00:00 2007 CDT isdst=1 gmtoff=-18000
/etc/localtime Sun Nov 4 06:59:59 2007 UTC = Sun Nov 4 01:59:59 2007 CDT isdst=1 gmtoff=-18000
/etc/localtime Sun Nov 4 07:00:00 2007 UTC = Sun Nov 4 01:00:00 2007 CST isdst=0 gmtoff=-21600

```
You should be fine, otherwise you'd have to change it manually. The machine I'm worried about has the correct output, however my other machine shows:
```
/etc/localtime  Sun Apr  1 07:59:59 2007 UTC = Sun Apr  1 01:59:59 2007 CST isdst=0 gmtoff=-21600
/etc/localtime  Sun Apr  1 08:00:00 2007 UTC = Sun Apr  1 03:00:00 2007 CDT isdst=1 gmtoff=-18000
/etc/localtime  Sun Oct 28 06:59:59 2007 UTC = Sun Oct 28 01:59:59 2007 CDT isdst=1 gmtoff=-18000
/etc/localtime  Sun Oct 28 07:00:00 2007 UTC = Sun Oct 28 01:00:00 2007 CST isdst=0 gmtoff=-21600

```
Any word on how to fix this?

---

### Post by jimbob on 2007-03-06
I would first try an apt-get update followed by an apt-get upgrade on the machine that is incorrect.

It is my understanding that Ubuntu handled this a while back with an update.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by AusIV4 on 2007-03-06
Apt-get update updates the repository list and databases. apt-get upgrade actually upgrades the software.

I ran sudo aptitude update, then sudo aptitude upgrade, and my DST data is still wrong.

---

### Post by jimbob on 2007-03-06
Set up NTP to run on that computer or check this thread for an alternate method:

[http://www.ubuntuforums.org/showthread.php?t=368082&page=2&highlight=dst](http://www.ubuntuforums.org/showthread.php?t=368082&page=2&highlight=dst)
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by mcwtlg on 2007-03-06
Don't make the same mistake I did...

type:

```
sudo tzconfig
``` 

and make sure you are set correctly.  Somehow I was set to Mexico... on 2 of my 4 machines!

---

### Post by AusIV4 on 2007-03-08
> **mcwtlg said:**
> Don't make the same mistake I did...

type:

```
sudo tzconfig
``` 

and make sure you are set correctly.  Somehow I was set to Mexico... on 2 of my 4 machines!

THANK YOU!

---

### Post by barney_1 on 2007-03-08
I'm quite surprised to find that although I haven't updated my MythTV box in months he time-change is set correctly.  Thanks for posting the way to check in your edited post!

---

### Post by spvo on 2007-03-11
Thanks mcwtlg, I had the exact same mistake.  Both my laptop and my desktop were set to mexico city.  I doubt if I ever would have figured that out.

---

