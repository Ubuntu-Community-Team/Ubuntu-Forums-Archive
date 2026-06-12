---
title: "Python doesn't write when log files are rotated"
date: 2020-12-24
forum: General Help
---

### Post by shadowsaunter on 2020-12-24
Hi,  I'm trying to find a way to rotate my logfiles.  What I'm doing is correctly rotating my logfile, but Python no longer writes to the file after it is rotated.  I'm rotating the files using a simple bash script, and I'm calling that script once per minute using crontab.

I'm pretty sure that I can fix this in Python using the os library, something like test for my logfile, if present use it, if not create it...and then take the "touch" function out of my bash, but I really want to understand what is happening here.

Also: I can tail -f my example.log and I get updates, but when I look in the file, it is empty.  This is the confusing part!

Here is my quick Python script:

```

import logging as templog
import time


templog.basicConfig(filename='example.log',level=templog.INFO)


def basicLoopFunction():
    print("Starting Function....")
    templog.info("Starting Function....")
    while True:
        print("Executing....")
        templog.info("Executing....")
        time.sleep(10)


basicLoopFunction()

```

My log rotator looks like this:

```



#!/bin/bash
#
# Script to manage log files
#


rm /home/shadow/dev/logTest/example.log.1 &> /dev/null
mv /home/shadow/dev/logTest/example.log   /home/shadow/dev/logTest/example.log.1 &> /dev/null
touch /home/shadow/dev/logTest/example.log 

```

and my crontab line is:

```

* * * * * /home/shadow/dev/logTest/logrotate

```

---

### Post by TheFu on 2020-12-24
close() the file before the rotation, then open() a new file after.
open() files access the same inode, regardless of the filename.
If the file inode is not closed, the new file will not be written into.

The wikipedia article on inodes may be useful background.

Once a minute seems obsessive for production.

---

### Post by The Cog on 2020-12-24
Just re-wording what TheFu said (he is absolutely right): 
Once python has opened example.log for writing, something else renaming the file will make no difference. Python will continue writing to it not even realising that it has been renamed. 

One solution would be to have python open, write and close every time it has log messages to write (or close and re-open fairly frequently). 
Another solution would be to get python to do the rotating.

---

### Post by Holger_Gehrke on 2020-12-24
Why reinvent the wheel ? Python logging has a RotatingFileHandler. An example can be found [here]("https://docs.python.org/3/howto/logging-cookbook.html#using-file-rotation").

Holger

---

### Post by shadowsaunter on 2020-12-24
Thank you all, (everyone.)

---

