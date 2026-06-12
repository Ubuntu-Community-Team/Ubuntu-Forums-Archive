---
title: "cron trouble"
date: 2008-02-23
forum: General Help
---

### Post by cheeseboy2010 on 2008-02-23
Hey. I use cron on my feisty sever a lot. I have also been using a program called castget to fetch podcasts for me. I was running castget manually, but now I want to use a cronjob.
So, I wrote a simple script to run castget and send the output to a log file. The problem is that all the commands in the script run except castget.
Here's the script. (all the echo commands are there to make the log pretty)

#!/bin/bash
echo $(date) >> /crypt/logs/castget.log
echo "*****************************************" >> /crypt/logs/castget.log
echo >> /crypt/logs/castget.log
castget -v >> /crypt/logs/castget.log
echo >> /crypt/logs/castget.log
echo "*****************************************" >> /crypt/logs/castget.log

Another thing to note is that I can run this manually and it works fine. I read some posts online that said something about the environment, but I'm not sure what they mean.


Can anyone help me out?

---

### Post by pointone on 2008-02-23
Use the full pathname for castget.

Also, if castget is a shell script, make sure you define your PATH at the beginning (assuming it runs external commands), as in:

```
PATH=/bin:/sbin:/usr/bin:/usr/sbin:/usr/local/bin
```

---

### Post by hyperair on 2008-02-23
What do your logs say?

---

### Post by cheeseboy2010 on 2008-02-24
Thanks for the quick reply. Unfortunately, I tried both solutions you gave and neither of them worked. As for the log question, my logs look like this:

*****************************************
Sat Feb 23 22:46:07 EST 2008
*****************************************

Updating channel Diggnation...
Updating channel Systm...
Updating channel Tekzilla...
Updating channel Totally Rad Show...
Updating channel thebroken...
Updating channel Web Drifter...
Updating channel Mac OS Ken...
Updating channel Bungie Podcast...
Updating channel SubSystm...

*****************************************
Sat Feb 23 23:00:01 EST 2008
*****************************************


*****************************************
Sat Feb 23 23:30:03 EST 2008
*****************************************


*****************************************
Sun Feb 24 00:00:02 EST 2008
*****************************************


*****************************************
Sun Feb 24 00:05:01 EST 2008
*****************************************


*****************************************
Sun Feb 24 00:10:02 EST 2008
*****************************************


*****************************************

The date, spaces, and asterisks are form the echo commands and are there to make the log easy to read. The first entry is from running the script manually. After that it seems that everything is being run except castget. Either that or it is just not being output to the log.

---

