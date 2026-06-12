---
title: "inotify tools"
date: 2014-06-25
forum: General Help
---

### Post by sayre on 2014-06-25
Hi everyone,

I finally figured out how to get an inotifywait bash script running and it works great. Now the only thing I can't figure out is how to return to the command line once I initiate the script, like you would run a daemon.  I couldn't find anything on how to do it. 

Here is my simple script. 

```
[SIZE=2][FONT=verdana]#!/bin/bash[/FONT][/SIZE]
[SIZE=2][FONT=verdana]
[/FONT][/SIZE]
[SIZE=2][FONT=verdana]dir=~/uploads/[/FONT][/SIZE]
[SIZE=2][FONT=verdana]
[/FONT][/SIZE]
[SIZE=2][FONT=verdana]inotifywait -m "$dir" --format '%f' -e close_write  |[/FONT][/SIZE]
[SIZE=2][FONT=verdana]while read file; do[/FONT][/SIZE]
[SIZE=2][FONT=verdana]sendemail -f ***@***.com -t ***@***.com -u File Uploads -m "$file"  -s sm$[/FONT][/SIZE]
[SIZE=2][FONT=verdana]done[/FONT][/SIZE]

```

Thanks in advance.

---

### Post by papibe on 2014-06-25
Hi sayre.

There are couple of options.

You can run your commands to run on the background using 'nohup', or use 'screen'. I personally prefer screen.

Here's a similar [thread]("http://ubuntuforums.org/showthread.php?t=1988379&highlight=screen") that explains how to use screen on post #3, and nohup on post #11.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by sayre on 2014-06-26
> **papibe said:**
> Hi sayre.

There are couple of options.

You can run your commands to run on the background using 'nohup', or use 'screen'. I personally prefer screen.

Here's a similar [thread]("http://ubuntuforums.org/showthread.php?t=1988379&highlight=screen") that explains how to use screen on post #3, and nohup on post #11.

Hope it helps. Let us know how it goes.
Regards.

Works Perfect thank you, I used Screen.

---

