---
title: "Detecting Chrome memory leaks and stopping Chrome"
date: 2018-09-24
forum: General Help
---

### Post by SagaciousKJB on 2018-09-24
I use a pretty older system and I've only got 6 GB of RAM.  Frequently I run into the problem where Chrome will have a memory leak and start gobbling up swap, making my computer dreadfully slow to use.  So slow in fact that it's faster simply to log in over SSH with my tablet  to kill Chrome than to wait for my mouse to respond to movement and close the window.

Lately I decided to create a script to run in the background and detect if Chrome starts to use too much memory and terminate it if it does.  I haven't started tweaking with the percentage to terminate at yet, but right now I'm just having problems with thew  way I'm acquiring the memory percentage.  Here is the script so far...

```

#!/bin/bash

ChromeMemUsage=`ps -eo %mem,stat,args --sort user | grep chrome | grep SLl | cut -d " " -f 2 | sed "s/\.[0-9]//g"`

while : ; do
	ChromeMemUsage=`ps -eo %mem,stat,args --sort user | grep chrome | grep SLl | cut -d " " -f 2 | sed "s/\.[0-9]//g"`

	echo "ChromeMemoryUsage at %$ChromeMemUsage"

	if [ $ChromeMemUsage -ge 50 ] ; then
		echo "Chrome Memory Leak Detected, Stopping Chrome"
		kill -TERM $(pgrep -d " " chrome)
	fi
	sleep 5s
done
```

It's been a while since I've scripted so I'm not really sure how to use a float value with the [] test built-in, so instead I'm using sed to remove the decimal values that 'ps' passes so that it's just an integer percentage to compare.

So far the problem is that sometimes the string

```
ps -eo %mem,stat,args --sort user | grep chrome | grep SLl | cut -d " " -f 2 | sed "s/\.[0-9]//g
```

Won't return anything, and I'm not really sure why.  This isn't entirely problematic since [ ] just complains it was expecting a unary operator when it gets nothing.  I have to grep the "SLl" state so that I know I'm getting the percentage of the top Chrome process and not one of its many threads.

Is there maybe a better way than using 'ps' to get the memory usage?  I'm just concerned with how consistent this will handle things using 'ps'.

Perhaps a better way of going about this?  I don't know if there's any actual applications suited toward this.

---

