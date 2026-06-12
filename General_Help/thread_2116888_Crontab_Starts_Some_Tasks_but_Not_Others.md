---
title: "Crontab Starts Some Tasks but Not Others"
date: 2013-02-17
forum: General Help
---

### Post by Xplorer4x4 on 2013-02-17
I have a lucid vps and want to run rtorrent at stat up. I have an auto download script running in combination with rtorrent, and it runs on start up just fine. rtorrent does not.

My crontab looks like this:
```
@reboot screen -dmS rtorrent -n -o import=/home/user/pathto/.rtorrent.rc
@reboot screen -dmS autoscript ./loop
```

I used this same exact crontab on a precise/quantal box with no issues, so I can't figure out why the download script still starts fine, but rtorrent does not. I tried making the .rtorrent.rc file executable for testing sake, and did a reboot. Still no luck. Also, if I enter:
```
screen -dmS rtorrent -n -o import=/home/user/pathto/.rtorrent.rc
```
directly over ssh, it launches rtorrent fine. It only fails to launch when I use crontab to start it.

---

### Post by sudodus on 2013-02-17
Cron uses a very limited environment, so you should be prepared to enter the full path and also other environment variables explicitly.

You can find the path with which. For example
```
$ [COLOR="RoyalBlue"]which screen[/COLOR]
/usr/bin/screen
``` and find the path for rtorrent the same way
```
[COLOR="Royalblue"]which rtorrent[/COLOR]
```

---

### Post by Xplorer4x4 on 2013-02-17
Thank you very much! Sure enough that did the trick. Any particular reason this was needed on lucid but not precise/quantal? Is it because I used a ppa on Precise/Quantal?

---

### Post by sudodus on 2013-02-17
> **Xplorer4x4 said:**
> Thank you very much! Sure enough that did the trick. Any particular reason this was needed on lucid but not precise/quantal? Is it because I used a ppa on Precise/Quantal?
I'm glad it works for you now. I don't know why it works in precise/quantal, but somehow cron gets information about the path.

---

### Post by papibe on 2013-02-17
Hi Xplorer4x4.

I just want to point out that you are missing something in your screen command.

The -S parameter is for a session name that should be immediately after it.

So it should be:
```
screen -dmS **[COLOR="Red"]ANY_NAME[/COLOR]** rtorrent -n -o import=/home/user/pathto/.rtorrent.rc
```
Regards.

---

### Post by Xplorer4x4 on 2013-02-17
> **sudodus said:**
> I'm glad it works for you now. I don't know why it works in precise/quantal, but somehow cron gets information about the path.
Thanks anyways! Actually, i think it just needed the path to rtorrent because the screen for the script launched fine with out a path making me curious if the fact screen was installed via apt while rtorrent was compiled from source. Plus the script was launching fine via a relative path, rather then full path. The script is located in the home dir and is just a set of scripts(php/bash) that don't require any compiling or anything.

> **papibe said:**
> Hi Xplorer4x4.

I just want to point out that you are missing something in your screen command.

The -S parameter is for a session name that should be immediately after it.

So it should be:
```
screen -dmS **[COLOR="Red"]ANY_NAME[/COLOR]** rtorrent -n -o import=/home/user/pathto/.rtorrent.rc
```
Regards.

Sorry, that was just a typo. It was set up properly in my crontab all along. Good catch though!

---

