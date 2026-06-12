---
title: "Upstart is taking up all disk space available"
date: 2015-07-05
forum: General Help
---

### Post by dax3 on 2015-07-05
So, my Upstart folder is massive currently; its about half a terabyte.
I used the little to no sudo skills I have to get autoclean running and it freed like 90 meg of data, but I still can't save anything to the disc. I need some help with what commands to use to clean this, because I've read that messing with upstart is super risky.
I'm pretty sure it's mostly either logs or crashlogs, but I'm scared to rm them in fear of destroying my rig.
What do?

---

### Post by dino99 on 2015-07-05
which 'upstart' folder are you referring to ? please write the full path; and which ubuntu flavour/version/DE is it ?

---

### Post by Skaperen on 2015-07-05
i assume you mean **[FONT=courier new]/var/log/upstart[/FONT]**. tell us the path if something else.

can you list the files in there?  how many files with names ending in "log" are there?  here is a command to count them:

[FONT=courier new]sudo ls -1 /var/log/upstart|egrep 'log$'|wc -l
[/FONT]
mine has 18.   if yours has fewer than 20 can you list them with sizes and post the result here?   this example command will show sizes in number of blocks, which is good enough to see if they are exceedingly large.

[FONT=courier new]sudo ls -s1 /var/log/upstart|egrep 'log$'[/FONT]

i am wanting to know if you are filled up with a large number of files or a few large files.  also do this command:

[FONT=courier new]df -i /[/FONT]

what is the** IUse%** percentage?

---

### Post by dax3 on 2015-07-05
The path to the upstart folder in question is in the .cache folder (/home/.cache/upstart/). As for the log files I have, I have 2 .log files (I had ~10 before I deleted a few), but about 30 .gz files that have the word log in them. I rebooted the system after taking care of a few log files and the folder shrank from almost 400 gb to 200 mg, then again from 200 gb to 30% of my disc space.
EDIT: My IUse% is 2%. The .gz files have also shrank considerably in size; most are only a few kb or a few hundred mb now. Also, Ubuntu 14.04 is the version I use. Could you please write the sudo I would use to view logs in the .cache upstart folder? I'm pretty uneducated as far as commands go, so I'd like to know to both know for future troubleshooting and so you can see the logs in question.

---

### Post by mc4man on 2015-07-05
all of those logs can be read in a text editor, no sudo needed. Generally they are rotated daily & compressed, no log should be over a Mb or 2.
(- I have prevented logging in that location unless I specifically want to but as I remember no daily individual log got over above mentioned size..

If you have any large one(s)  then open up & read in a text editor (gedit may choke on very large files...
What's this show? - 
```
ls -la ~/.cache/upstart
```

---

### Post by dax3 on 2015-07-05
That command shows an astonishing amount of files; I'm not sure if theres a character limit on these forums, but I'll put it in a pastebin just to save space on this reply just in case. They aren't individually over a gig currently I don't think, but when I looked previously they were by a large margin.
[http://pastebin.com/sHf0UuWi](http://pastebin.com/sHf0UuWi)

---

### Post by mc4man on 2015-07-05
Well you seem to get a lot of crashes, many multimedia related & many from some time ago.
So just go ahead & delete the ~/.cache/upstart folder & log out/in. It will be recreated,  keep an eye on it  & see..

---

### Post by dax3 on 2015-07-05
Yeah, it crashes once in a while, but not as often as you might think. This laptop wasn't mine back then; I bought it from a friend about 3 months ago, so I don't know how he managed to crash this thing so much. I'll update in 24 hours if the deletion of upstart works. If it stays fixed, I'll mark this board as resolved. Currently, I can save to the disc properly, so thanks for your help.

---

