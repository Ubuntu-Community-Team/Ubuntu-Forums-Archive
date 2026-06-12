---
title: "Disk space used by logs"
date: 2014-06-08
forum: General Help
---

### Post by garysferrao on 2014-06-08
Hey, while I was just working on fixing a crashed hard disk, I noticed a message saying that my filesystem "/" has only 93MB remaining. While I was shocked because I had around 10GB of free space when I started off that day. On closer inspection, I found that my "/var/log/syslog" had become 5.8GB and "/var/log/kern.log" was 5.8GB; and correspondingly "sys.log.1" was 1.1GB and "kern.log.1" 1.2GB.

Is it normal to have such huge logs? I had installed 12.04 (and still have 12.04) in February 2014.

And it seems to have the most recent modification date, 9 June 2014; so I think that it is the reason of my low space. Is there any way to free up my space? I think just deleting these logs will cause trouble. Nothing else seemed out of the ordinary.

---

### Post by deadflowr on 2014-06-08
If you view the kern.log file is there anything odd?
I would look toward the end of it for any repeating lines, perhaps something is stuck and it's repeating the same line(s) over and over again.
(5.8GB is pretty big, so please do not try to post the file here, maybe [pastebinit]("https://help.ubuntu.com/community/Pastebinit"), or small snippets from the file, but not the whole thing, please.)

---

### Post by CharlesA on 2014-06-09
This is probably going to suck but run this:

```
sort /var/log/kern.log | uniq | less
sort /var/log/syslog | uniq | less
```

---

