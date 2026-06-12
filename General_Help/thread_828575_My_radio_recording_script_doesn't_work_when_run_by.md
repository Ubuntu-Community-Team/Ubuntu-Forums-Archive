---
title: "My radio recording script doesn't work when run by CRON"
date: 2008-06-13
forum: General Help
---

### Post by ChadNickBok on 2008-06-13
Hello.

I have made a little script to wrap MPlayer and LAME. Its purpose is to record a radio program, so I can listen to it on my iPod. 

It takes three arguments; the time to record for in minutes, the media to record (ie. a radio stream), and the name to give it. It then outputs the file as date-name.mp3.

```

#!/bin/bash
rm /tmp/outpipe.wav
rm /tmp/inpipe
mkfifo /tmp/outpipe.wav
mkfifo /tmp/inpipe
lame /tmp/outpipe.wav "/home/nick/recordings/`date +'%F'`-**$3**.mp3" &
mplayer -input file=/tmp/inpipe -quiet -ao pcm:file=/tmp/outpipe.wav "**$2**" & 
{
sleep "**$1**m"
echo quit
} >> /tmp/inpipe

```

I then try to add this to my crontab, using crontab -e. What I put in there goes something along the lines of;

**00 * * * * /home/nick/recordradio.sh 10 rtsp://someradiostation/blah.rm Radio**

Unfortunately, whilst the previous command works fine when I run it in the shell, when trying to schedule it with CRON, it seems to run the script (I can see it in system manager), but no recordings are made :(

Any help greatly appreciated!

Regards,
Nick

ps. the exact station I'm wanting to record is rtsp://media1.abc.net.au/broadcast/rn.rm - Radio National in Australia

---

### Post by HalPomeranz on 2008-06-14
I'm wondering if it's a problem that the PATH in your interactive shell is different from the default PATH used by the cron daemon.  Maybe one of the programs your script is calling isn't being found as a result.  Fix by adding an explicit "export PATH=..." statement at the top of your script (generally a good idea anyway).

You might also think about turning on cron logging to help you debug this problem.  Edit your syslog.conf file ("sudo vi /etc/syslog.conf") and uncomment the line that looks like:

```

#cron.*				/var/log/cron.log

```

Then restart your syslogd ("sudo /etc/init.d/sysklogd restart").  If you look at /var/log/cron.log after your cron job runs you might see some helpful error messages.

---

### Post by andrew.46 on 2008-06-15
Hi:

> **ChadNickBok said:**
> 
I then try to add this to my crontab, using crontab -e. What I put in there goes something along the lines of;

**00 * * * * /home/nick/recordradio.sh 10 rtsp://someradiostation/blah.rm Radio**

Good to see a fellow ABC fan! I do something a little bit different to catch an ABC stream:

[http://www.andrews-corner.org/ftgws.html](http://www.andrews-corner.org/ftgws.html)

The script is near the base of the page. You can see from that this that I use cron quite differently, perhaps this approach might work?

    Andrew

---

