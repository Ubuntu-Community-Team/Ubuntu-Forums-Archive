---
title: "Using cron to help deluge monitor a directory..."
date: 2007-11-07
forum: General Help
---

### Post by commonlyUNIQU3 on 2007-11-07
Hello all...  I've been teaching myself some shell scripting, and this is my first attempt at something functional & that may be worth sharing when I'm done.

I'm working on my ideal setup for my home media server to automatically download new content for me (e.g. Video Podcasts, or .torrents of TV Shows, etc)...

I really love deluge, but I miss the functionality found in some other torrent clients that lets you select a specific directory to monitor (as long as said client is running), and automatically start any torrents it finds there; e.g. point uTorrent at your desktop and let it run in the background, and any .torrent files you save to your desktop are automatically imported into utorrent to start downloading...

I'm 90% of the way there with a cron job right now, but I can't get cron to launch deluge.  I added some logging into the script to see how far it gets, and I can see that deluge is clearly being called, it just won't launch.

I found [THIS]("http://ubuntuforums.org/showthread.php?t=185993") post that seemed to be the answer, but it doesn't work either - even after adapting:

```
export DISPLAY=:0
```

for what my "DISPLAY" variable is set to by default; ":0.0"

```
export DISPLAY=":0.0"
```

I've attempted to put this variable in my crontab job, and also into the script itself - neither of which will work!

Here's the script I have so far - any help is appreciated!

```
#! /bin/bash
# 06.11.2007 by cH
# autorun Deluge when a .torrent file is found in a directory...

export DISPLAY=":0.0" # set which DISPLAY your torrent client should run on; 
					  # you shouldn't need to change this unless you have tweaked with your configuration; 
					  # you can learn your "default" display by opening a terminal and running "echo $DISPLAY" or "export | grep DISPLAY"...

export TORRENTC='deluge' # set a variable to call your TORRENT Client of choice...

export TORRENTC_OPTS='--tray' # set a variable for the TORRENT Client OPTionS you wish to use; 
							  # if none make sure to leave the quotes (e.g. export TORRENTC_OPTS='')...

export TORRENTDIR='/path/to/your/directory' # set the DIRectory the script will check for .TORRENT files...

export LOG='/dev/null' # set the location of a LOG file (for debugging);
					   # otherwise set it to '/dev/null'...

echo "`date --rfc-2822` Checking for any new .torrent file(s) in $TORRENTDIR..." >> $LOG

# is $TORRENTC already running ?
if ps -ef | grep -v grep | grep -v sh | grep $TORRENTC > /dev/null
	then 
		echo "`date --rfc-2822` NOTE: $TORRENTC is already running..." >> $LOG
	else 
		echo "`date --rfc-2822` NOTE: $TORRENTC isn't running yet..." >> $LOG
fi

# are there any .torrent file(s) in $TORRENTDIR ?
if test -e $TORRENTDIR/*.torrent
	then 
		echo "`date --rfc-2822` A .torrent file(s) was found!" >> $LOG 
		export TORRENT_STATUS='something did not work...'
		$TORRENTC "$TORRENTC_OPTS" $TORRENTDIR/*.torrent &&
		echo "`date --rfc-2822` Done." >> $LOG &
	else 
		echo "`date --rfc-2822` No new .torrent file(s) were found..." >> $LOG 
		export TORRENT_STATUS='(because no .torrent file(s) were found)...' 
fi

# how did we do (did we succesfully start $TORRENTC) ?
if ps -ef | grep -v grep | grep -v sh | grep $TORRENTC > /dev/null
	then 
		echo "`date --rfc-2822` $TORRENTC is up and running..." >> $LOG
	else 
		echo "`date --rfc-2822` $TORRENTC isn't running - $TORRENT_STATUS..." >> $LOG # uses $TORRENT_STATUS to tell you if it should have started the torrent client, or not...
fi

```

---

### Post by mpierce on 2007-11-07
I didn't go through your script but since I use deluge, I know that it has a scheduler plugin in feature that will allow it to launch at any time or day that you want. There's also a plugin to allow you to remotely add torrents. You may want to have a play with these features as you can specific where it should get and use torrents.

Hope this helps...

---

