---
title: "RSS feeds in Thunderbird from Firefox"
date: 2007-01-01
forum: General Help
---

### Post by Lunar_Lamp on 2007-01-01
Is it possible to add RSS feeds into Thunderbird whilst in Firefox?  I haven't been able to work out how, nor have I been able to find an extension for Firefox that does this.

---

### Post by Lunar_Lamp on 2007-01-05
Does anyone have any ideas on this?  I'm sure there must be a simple way of doing this...

---

### Post by Aranel on 2007-01-05
Under Firefox's preferences, go to Feeds and select the "Subscribe to the feed using:" radio button. Then click "Choose Application" and direct it to /usr/bin/thunderbird, and you should be all set.

Edit: If you're using Ubuntu's build of Thunderbird, rather than the universal binary from Mozilla, you'll need to make that /usr/bin/mozilla-thunderbird instead.

---

### Post by Lunar_Lamp on 2007-01-05
I have tried that, but it doesn't appear to work.  They don't get added to my RSS feeds in thunderbird.

---

### Post by Lunar_Lamp on 2007-01-10
Well, I couldn't find a way to do it, so I've started using liferea to view my feeds, and just used /usr/bin/liferea_add_feed as the pathway - which works just great.

---

### Post by atraeyu on 2007-03-16
I told firefox to open rss feeds using '/usr/bin/mozilla-thunderbird" but it doesn't work.  Nothing happens when I try to subscribe in firefox.

---

### Post by washeck on 2008-02-20
There is a bug in either Firefox or Thunderbird (or both; see [bugzilla discussion]("http://bt2ws.central.sun.com/CrPrint?id=6582797")).

I made a quick-and-dirty for myself using a simple shell script:

[LIST=1]
[*] Make a script subscribe-rss.sh with the following content:
```

#!/bin/sh
command="/usr/bin/thunderbird -mail feed:$1"
$command

```
[*] In Firefox, open about:config and set browser.feeds.handler.application to the the script (/home/washeck/bin/subscribe-rss.sh in my case)
[/LIST]

**Warning:** I don't know if Firefox checks for special characters in the URL of the feed. If not, specially crafted URL can lead to arbitrary code execution vulnerability. Use at your own risk.

---

### Post by rakudave on 2008-03-30
works great for me, thx
(firefox won't listen to arguments behind "thunderbird")

---

