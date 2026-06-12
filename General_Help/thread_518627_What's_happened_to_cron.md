---
title: "What's happened to cron?"
date: 2007-08-06
forum: General Help
---

### Post by Beamerboy on 2007-08-06
I dunno what is going on here, but I recently added a script to run every 10 minutes to /etc/cron.d

It was working fine for a week but then it suddenly stopped working (and I made no changes to the script at any point).

The script looks like this:

```

0,10,20,30,40,50 * * * * www-data [ -x /usr/lib/cgi-bin/blog/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache2/blog.paladine.org.uk-access.log ] && /usr/lib/cgi-bin/blog/awstats.pl -config=awstats -update >/dev/null

```

But when I try and run the script to test it I get the following error:

```

paladine@mail:/etc/cron.d$ sudo ./awstats
./awstats: line 1: 0,10,20,30,40,50: command not found

```

Yet if I run:
```

sudo /usr/lib/cgi-bin/blog/awstats.pl -config=awstats -update

```

It works fine.

I can't figure out why cron has suddenly stopped working with scripts in /etc/cron.d no matter what script I try to add there, it fails with "command not found" it just makes no sense.

Any help appreciated.

Paladine

---

### Post by heimo on 2007-08-06
> **Beamerboy said:**
> Any help appreciated.

Not sure if this has anything to do with it, but instead of *0,10,20,30,40,50* try **/10*

---

### Post by Beamerboy on 2007-08-06
> **heimo said:**
> Not sure if this has anything to do with it, but instead of *0,10,20,30,40,50* try **/10*


Tried that and tried 0-59/10 made no difference

---

### Post by Beamerboy on 2007-08-06
Fixed it, there was a permissions issue on the log file.

---

### Post by mister_p_1998 on 2007-09-10
> **Beamerboy said:**
> Fixed it, there was a permissions issue on the log file.

Im getting similar problems...
exactly WHERE is the log file?
Steve

---

