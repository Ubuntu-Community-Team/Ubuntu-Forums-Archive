---
title: "Why won't mplayer restart as this script tells it to?"
date: 2008-05-22
forum: General Help
---

### Post by chariscomp on 2008-05-22
Hello,

I am trying to figure out why this script doesn't work as I expect:

```
#!/usr/bin/perl
#

$pids=`pidof mplayer`;
if ($pids=="") {
#print "launching mplayer because it wasn't started\n";
launchmplayer();
} else {
#print "killing mplayer!\n";
($pid1,$pid2)=split(" ",$pids);
$kill1=`kill -9 $pid1`;
$kill2=`kill -9 $pid2`;
#print "starting mplayer again!\n";
launchmplayer();
}

sub launchmplayer() {
$cmd="/home/jdcook/holdmusic.sh";
system($cmd);
}

```

It calls the following script:
```
#!/bin/bash
/usr/bin/amixer set "Analog Front" 54% < /dev/null
/usr/bin/mplayer -shuffle -noconsolecontrols -loop 0 -playlist /home/jdcook/all\ music.m3u < /dev/null
```


The purpose behind this is to create a Music on Hold system. It is supposed to restart mplayer every night via a crontab entry that looks like: ```
0 4 * * * /home/jdcook/holdmusic.pl &
```

This *does* work the first time it runs. However, the next night, it never seems to run, leaving me with no mplayer playing anything at all. Does anyone have any suggestions on what I am doing wrong here? Why doesn't this code restart mplayer every night? 

Thanks in advance for any help anyone can give.

Additional info: I just tried running this as root from the command line back to back and it works as it should! So now the mystery is even greater! Why does it work this way, but not from cron?

---

