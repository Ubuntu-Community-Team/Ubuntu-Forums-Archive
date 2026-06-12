---
title: "Restore rdiff backup files"
date: 2022-01-07
forum: General Help
---

### Post by mlnease on 2022-01-07
Hello,

I hope this isn't redundant.  I have a full backup using ```
rdiff
``` but can't seem to figure out how to use ```
rdiff
``` to restore them on a new install of 18.04 (long story).

Any help would be greatly appreciated.

Thanks in advance.

mn

---

### Post by TheFu on 2022-01-07
Are you really using rdiff directly? Not rdiff-backup?  

With rdiff-backup, the last backup set is just a mirror and can be copied or rsync'd to restore.  If you need older versions, use the **rdiff-backup -r** command.  If the files aren't only owned by your userid, use sudo for the recovery so the original owner, group and permissions can be retained.  With cp, use the -p option.

---

### Post by mlnease on 2022-01-07
You're right of course The Fu (great to hear from you again)--I am using rdiff-backup.  Sorry for the imprecision.

I'll have a go and post the results here.  Tomorrow, though.

Thanks again.

> **TheFu said:**
> Are you really using rdiff directly? Not rdiff-backup?  

With rdiff-backup, the last backup set is just a mirror and can be copied or rsync'd to restore.  If you need older versions, use the **rdiff-backup -r** command.  If the files aren't only owned by your userid, use sudo for the recovery so the original owner, group and permissions can be retained.  With cp, use the -p option.

---

### Post by mlnease on 2022-01-08
I'm unable to figure this out.  I wanted to restore 'home'--about 60GB--because that solves--or used to solve--so many problems at once.  It isn't practical to restore 10000+ files plus manually so I guess without sbackup my backing up days are pretty much over.  Why bother if I can't restore?

Thanks for your time and trouble.  Sorry to've bothered your.

---

### Post by TheFu on 2022-01-09
> **mlnease said:**
> I'm unable to figure this out.  I wanted to restore 'home'--about 60GB--because that solves--or used to solve--so many problems at once.  It isn't practical to restore 10000+ files plus manually so I guess without sbackup my backing up days are pretty much over.  Why bother if I can't restore?

Thanks for your time and trouble.  Sorry to've bothered your.

I'm confused.  Why not use rsync?  rsync is one of the top 5 commands anyone on a Unix system really would do well to know and use.
Or use **rdiff-backup -r**

[Https://ubuntuforums.org/showthread.php?t=2436006&p=13928432#post13928432](Https://ubuntuforums.org/showthread.php?t=2436006&p=13928432#post13928432)
has a little script to backup HOME and how to restore it. Looks like the restore isn't correct in that link. Sorry.

 ```
sudo rdiff-backup -r 3B /path/to/backup/storage  /path/to/target/
```
I've added the last parameter. The path to the target. In many situations, to restore  ....

```
sudo rdiff-backup -r now /backups/home   /home/
```
is the answer to restore the last backup. If you want to access older backup sets, just change "now" to one of the many different date/time specifications.  The "3B" is 3 backups ago, but the time spec is really flexible.  "4W" or "23D" should work too.  Let me check the manpage.  .... looking .... 

There is a section in the manpage called "TIME FORMATS" which explains, in depth, which can be used.  
```
TIME FORMATS
       rdiff-backup uses time strings in two places.  Firstly, all of the  in&#8208;
       crement  files  rdiff-backup  creates will have the time in their file&#8208;
       names in  the  w3  datetime  format  as  described  in  a  w3  note  at
       http://www.w3.org/TR/NOTE-datetime.     Basically    they   look   like
       "2001-07-15T04:09:38-07:00", which  means  what  it  looks  like.   The
       "-07:00" section means the time zone is 7 hours behind UTC.

       Secondly, the -r, --restore-as-of, and --remove-older-than options take
       a time string, which can be given in any of several formats:

       1.     the string "now" (refers to the current time)

       2.     a sequences of digits, like "123456890" (indicating the time  in
              seconds after the epoch)

       3.     A string like "2002-01-25T07:00:00+02:00" in datetime format

       4.     An interval, which is a number followed by one of the characters
              s, m, h, D, W, M, or  Y  (indicating  seconds,  minutes,  hours,
              days, weeks, months, or years respectively), or a series of such
              pairs.  In this case the string refers to the time that preceded
              the  current  time by the length of the interval.  For instance,
              "1h78m" indicates the time that was one hour and 78 minutes ago.
              The calendar here is unsophisticated: a month is always 30 days,
              a year is always 365 days, and a day is always 86400 seconds.

       5.     A date format of the form YYYY/MM/DD, YYYY-MM-DD, MM/DD/YYYY, or
              MM-DD-YYYY,  which  indicates  midnight  on the day in question,
              relative  to  the  current  timezone  settings.   For  instance,
              "2002/3/5",  "03-05-2002",  and  "2002-3-05" all mean March 5th,
              2002.

       6.     A backup session specification which is a  non-negative  integer
              followed  by  'B'.  For instance, '0B' specifies the time of the
              current mirror, and '3B' specifies the time of  the  3rd  newest
              increment.
```

Flexible and only as complex as needed to accomplish the task. Good Unix design.

---

