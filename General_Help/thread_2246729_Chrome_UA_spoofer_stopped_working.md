---
title: "Chrome UA spoofer stopped working"
date: 2014-10-02
forum: General Help
---

### Post by jason13 on 2014-10-02
[COLOR=#000000]I was using the extension Chrome User Agent Spoofer to spoof primarly windows Firefox v.15 for some sites that don't work normally (including netflix). I have the extension icon locked next to the address bar and no amount of configuring and restarting the system can get it to work. Normally after I change the browser agent it reloads all my open tabs, I can access the menus from the icon but it doesn't change the browser agent anymore. Anyone got a fix?[/COLOR]

---

### Post by Habitual on 2014-10-03
I use this for netflix:
```
Google Chrome [COLOR=#303942][FONT=DejaVu Sans]Version 37.0.2062.120 (64-bit)[/FONT][/COLOR]

 [COLOR=#303942][FONT=DejaVu Sans]User-Agent Switcher for Chrome[/FONT][/COLOR][COLOR=#303942][FONT=DejaVu Sans] [/FONT][/COLOR][COLOR=#303942][FONT=DejaVu Sans]1.0.36[/FONT][/COLOR]

 Mozilla/5.0 (Windows NT 6.3, Win64, x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/38.0.2114.2 Safari/537.36
```
and it works as of 1m ago.

---

### Post by jason13 on 2014-10-07
I'm using the exact same extension with a slightly older version of chrome. even after restarts, the extension fails to initialize the spoof of the UA. How should I go about fixing it?

---

### Post by yancek on 2014-10-08
If you are referring to using Netflix with Chrome, you need version 37 or newer which should be in the repositories.

---

### Post by myacct on 2014-10-10
It didn't work for  me.  When attempting to start playing a video I'm prompted to download  and install Silverlight.

Netflix preferences:
1) Playback settings: Prefer HTML5 instead of Silverlight

System info:
1) ubuntu 14.04 - packages up to date
2) nss3 version:  2:3.17.1-0ubuntu0.14.04.1 
3) google-chrome-stable : 38.0.2125.101-1 
5) User agent settings:

[TABLE="class: cms_table_ua_list_sub_table, width: 800"]
[TR]
[TD]Netflix Linux
[/TD]
 [TD]Mozilla/5.0 (Windows NT 6.3, Win64, x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/38.0.2114.2 Safari/537.36 [/TD]
 [TD]Replace  IE9[/TD]
 [/TR]
 [TR]
[TD][/TD]
 [TD][/TD]
 [TD][/TD]
[/TR]
[/TABLE]

---

### Post by sammiev on 2014-10-10
Did you download libnss3 files and install them?

Read more info [here]("http://www.omgubuntu.co.uk/2014/08/netflix-linux-html5-support-plugins").

---

### Post by myacct on 2014-10-10
This article [http://alturl.com/xjv8u](http://alturl.com/xjv8u) indicates that we need libnss3 >= 3.16.2.  Recently Ubuntu updated to 3.17.1 so I don't think that's the issue.  Do you have Netflix up and running?

---

### Post by yancek on 2014-10-10
The info in your last post is exactly what I have and no problems with Netflix.  Are you sure you have the User Agent Switcher enabled and selected the user agent you created for Netflix?  Can't see any other reason it would not work.

---

### Post by jawilljr2 on 2014-10-11
[User Agent no longer needed for Netflix.]("http://www.omgubuntu.co.uk/2014/10/psa-netflix-ubuntu-now-working-box")

> **Netflix now works on Ubuntu out of the box — no hacks, plugins or [user-agent switching]("http://www.omgubuntu.co.uk/2014/08/netflix-linux-html5-support-plugins") workaround required.**

All you need is the latest Chrome stable and libnss (3.17 or later).

---

### Post by myacct on 2014-10-11
Thanks jawilljr2,  after disabling user agent it worked.  It seems to only prompt to install silverlight when user agent is enabled.

---

### Post by jason13 on 2014-10-11
I re installed libnss3 packages and disable netflix from my permanent spoof list, everything is working there. But Chrome UA spoofer still isn't.

---

