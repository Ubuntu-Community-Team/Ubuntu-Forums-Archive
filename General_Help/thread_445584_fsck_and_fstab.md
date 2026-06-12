---
title: "fsck and fstab"
date: 2007-05-16
forum: General Help
---

### Post by thj01 on 2007-05-16
I'm a bit anoyd by the fact that the filesystem is checked aprox. every 30'th time the system is mounting a drive. 

Kan this be changed to 300 ???
to never? (and do it randomly when i have the time/need?


what about security if i change the last two diggits in fstab to 0 0 (removing the fsck rutine check)

I almost never did that i windows and it only did it when windows crashed (never experienced that with ubuntu :) )

---

### Post by heimo on 2007-05-16
You can change it using e2fstune (see *man e2fstune *for all the various options)

---

### Post by thj01 on 2007-05-16
ehhhh

i can only find e2fsck - how do i install e2fstune

---

### Post by anaconda on 2007-05-16
it is tune2fs  not e2fstune

just type man tune2fs in terminal.. to read more..

Sorry I hate when people say use man xxx, but dont know the exact flags..

---

### Post by heimo on 2007-05-16
> **anaconda said:**
> it is tune2fs  not e2fstune

just type man tune2fs in terminal.. to read more..

Sorry I hate when people say use man xxx, but dont know the exact flags..

Hey, sorry for that. Couldn't check the actual command but I was pretty sure I got it right. And yes, I really can't remember flags for that command and personally I would have used manual page to check it. It's not common for me to refer to manual pages (if you want to check my past messages) and thought that it'd be useful to at least give a hint about what to do. :)

But really, thanks for helping him and correcting my (human) mistake. And for thj01, sorry for the wrong information and only pointing to manual pages.

Cool? :)

---

### Post by heimo on 2007-05-16
From man tune2fs
>        -c max-mount-counts
              Adjust the maximal mounts count between two  filesystem  checks.
              If max-mount-counts is 0 then the number of times the filesystem
              is mounted will be disregarded by e2fsck(8) and the kernel.
So something like (sorry, haven't tested) like this could work to disable fsck on device /dev/sda1:

```
sudo tune2fs -c0 /dev/sda1
```

Let's add a warning: Of course it's good to check your filesystems from time to time and disabling automatic periodical check is not recommended.

---

### Post by anaconda on 2007-05-16
> **heimo said:**
> Hey, sorry for that. Couldn't check the actual command but I was pretty sure I got it right. And yes, I really can't remember flags for that command and personally I would have used manual page to check it. It's not common for me to refer to manual pages (if you want to check my past messages) and thought that it'd be useful to at least give a hint about what to do. :)

But really, thanks for helping him and correcting my (human) mistake. And for thj01, sorry for the wrong information and only pointing to manual pages.

Cool? :)

Very Cool.. :)

Actually I didn't mean the comment towards you. I just said 
use man tune2fs
and then I meant to say that I am sorry I am not able to help more than by pointing to man pages, which are quite difficult to read sometimes... expecially for beginners.

But I always think pointing to man pages is a lot  better than no help at all...

So, sorry for the misunderstanding..

---

### Post by heimo on 2007-05-16
> **anaconda said:**
> So, sorry for the misunderstanding..

Not a problem at all. And there are at least two of us who don't like pointing to manual pages, but yes - it's better than nothing. There is this "heritage" - bad experience about some forums / mailing lists / usenet groups / irc channels where "man *command*" / "RTFM" / "google it" culture is way too common and we really don't want Ubuntuforums to be like that.

---

### Post by thj01 on 2007-05-16
I'm greatfull that i get answers and corrections - end even in the same day :-)

So thumbs up for anybody who helps 

I know its unwise never to check the filesystem - but what are a good amount.

i know i NEVER did it in the old days (the happy DOS and win98  days) as a standard but only when  the bad consciousness  hit me. 

My thoughts was to do it once or twice a month .

what are your opinions? 

BTW real men don't make backups - they cry

PS

I'm not a hacker but i am VERY happy anytime someone takes me right to the command line. (and sometimes i evens do study the underlaying thoughts of the command line

So thanks for the help and i will take this to the danish ubuntu site so that you guys can be credited here [http://ubuntudanmark.dk/forum/posting.php?mode=reply&t=588](http://ubuntudanmark.dk/forum/posting.php?mode=reply&t=588)

---

### Post by thj01 on 2007-05-16
oups more questions

sudo tune2fs -c 0 /dev/sda1

souldn't there be a space betwen c and 0 ??

and i i would chose the i option

       -i  interval-between-checks[d|m|w]
              Adjust the maximal time between two filesystem checks.  No post&#8208;
              fix or d result in days, m in months, and w in weeks.   A  value
              of zero will disable the time-dependent checking.

              It  is  strongly  recommended that either -c (mount-count-depen&#8208;
              dent) or -i (time-dependent) checking be enabled to force  peri&#8208;
              odic  full  e2fsck(8) checking of the filesystem.  Failure to do
              so may lead to filesystem corruption (due to bad disks,  cables,
              memory, or kernel bugs) going unnoticed, ultimately resulting in
              data loss or corruption.

should it then be 

sudo tune2fs -c 0  -i m 2 /dev/sda1

if i would chose to have a check every 2 months as the minimum?????????

---

### Post by heimo on 2007-05-16
> **thj01 said:**
> 
My thoughts was to do it once or twice a month .

what are your opinions? 


Even if you already disabled mount count based checking, you have time based checking enabled. You can get a lot of information by running tune2fs with -l (small letter L) and your device name (eg. sudo tune2fs -l /dev/sda1).  Check "Check Interval" and "Next check after". Mine is always checked after 37 mounts or 6 months. And believe me, I hit 6 months before 37 mounts.

Anyway, if you plan to run fsck manually, you could just leave the forced check there, as system would never have to run it. Or you can adjust the values to some higher value - like 100 mounts and time value to something lower like 2 months and see if that's better for your "usage pattern". Yeah, about 30 mounts may be a little low if you're shutting down once-twice a day. I don't see need to constantly check your filesystem, but I understand that values have probably been chosen so that it would catch any problems before they get fatal.

That was my opinion. :)

---

### Post by heimo on 2007-05-16
No need for space there, but put the m after 2. Like this:
```
sudo tune2fs -c0 -i2m /dev/sda1
```

---

### Post by thj01 on 2007-05-16
Heimo

thank you for your thoughts - it was something like that I thought myself.

And yes my problem is that it's a laptop that is booted once or thrice a day

---

