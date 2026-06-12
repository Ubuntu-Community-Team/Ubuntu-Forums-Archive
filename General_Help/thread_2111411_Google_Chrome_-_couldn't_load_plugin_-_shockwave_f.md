---
title: "Google Chrome - couldn't load plugin - shockwave flash"
date: 2013-02-01
forum: General Help
---

### Post by Download Descendent on 2013-02-01
Ok, this might be useful for people.

When I used Chrome in Ubuntu 12.04 when I went to watch a video on youtube (and then any similar site) an error message of couldn't load plugin.

After re-installing Chrome which didn't work and checking around previous threads etc, I went into Tools-Task Manager noticed the Plug-in Shockwave flash was N/A.

I then typed chrome://plugins/ in the address bar, extended the libpepflashplayer and disabled /opt/google/chrome/PepperFlash/libpepflashplayer.so

And then it worked again?

Anyone know why?  It was fine until tonight.

---

### Post by Download Descendent on 2013-02-01
There appears to be a conflict due to an update to Chrome flash plugin with Adobe flash plugin

---

### Post by Kow on 2013-02-01
Refer to [http://code.google.com/p/chromium/issues/detail?id=173790](http://code.google.com/p/chromium/issues/detail?id=173790)

---

### Post by Download Descendent on 2013-02-01
Edited to avoid confusion - see below

---

### Post by Download Descendent on 2013-02-01
> **Kow said:**
> Refer to [http://code.google.com/p/chromium/issues/detail?id=173790](http://code.google.com/p/chromium/issues/detail?id=173790)

Thank you - I will read it.

---

### Post by Mungo85 on 2013-02-01
same thing happened with me overnight. Performed a software update yesterday, chrome was one of the updates (as was opera). reloaded machine to complete update & everything was fine. Went to use Chrome this morning & got the "couldn't load plugin" message. Tried clearing the cache, etc & still the same problem. Followed your suggestion of disabling 

/opt/google/chrome/PepperFlash/libpepflashplayer.so

& it now works. Re-enabled the plugin & got the same "couldn't load plugin" message. I've left it disabled & works OK now. I read somewhere that chrome includes the flash plugin in the build. Must be a conflict if the adobe plugin is already installed. (I'm sure someone could explain this better than me).

Anyway, thanks for your suggestion.

---

### Post by Download Descendent on 2013-02-01
I can confirm from the link given by Kow that one suggestion from yippz seems to allow both to work:

Going into chrome://plugins and disabling 11.5.31.138 and enabling 11.2 r202, then closing Chome and restarting Chrome enables both flash versions. Disabling 11.5.31.135 is impossible unless you don't close or restart the browser.
Today (9 minutes ago)

---

### Post by Marzata on 2013-02-01
Same here.

---

### Post by Morderwurst on 2013-02-01
This works, thanks.

---

### Post by AdvancedNewbie on 2013-02-01
Thank you.

---

### Post by vasa1 on 2013-02-01
> **Kow said:**
> Refer to [http://code.google.com/p/chromium/issues/detail?id=173790](http://code.google.com/p/chromium/issues/detail?id=173790)

Thanks for the link. Many of the posters there are not providing much detail. The OP there is on **13**.04 and feels it started after upgrading the kernel to **3.8** and is using Chrome **dev**.

---

### Post by ernestj on 2013-02-01
thank you. did the first thing in the opening thread and worked!!!

solved. i love Ubuntu forums.

---

### Post by jajodo on 2013-02-02
Hope this helps someone.  I was having trouble inactivating the problematic flash 11.5.31.138 and enabling 11.2 r202.  Each time I restarted chrome 11.5.31.138 was reactivated and the flash error persisted.

Closing all extra tabs including Gmail allowed successful inactivation.  I suspect Gmail was reactivating the built in flash or blocking inactivation.

---

### Post by as8 on 2013-02-02
I tried this and now it says:

"Adobe Flash player has been disabled"

any ideas?

---

### Post by as8 on 2013-02-02
> **as8 said:**
> I tried this and now it says:

"Adobe Flash player has been disabled"

any ideas?

I figured it out by expanding the individual plugin files and disabling some combination of them.

---

### Post by Frogs Hair on 2013-02-02
This happened last night after playing one video. I deleted the  entire profile folder and re-installed with no joy. I went back to Iron which is a Chromium based browser like Chrome and it plays fine. Iron doesn't use Pepper Flash so I don't know if that is a factor or not.

---

### Post by deadflowr on 2013-02-02
> **Frogs Hair said:**
> This happened last night after playing one video. I deleted the  entire profile folder and re-installed with no joy. I went back to Iron which is a Chromium based browser like Chrome and it plays fine. Iron doesn't use Pepper Flash so I don't know if that is a factor or not.

You're most likely using flash 11.2.

Sadly, the pepperflash has been problematic ever since adobe dropped support for regular flash on linux.
Every version of chrome I've run on Ubuntu (since pepperflash 11.3), I eventually have to disable that plugin because something goes boink, yet ver 11.2 has never had a problem.

Of course, when a new version of chrome comes, I re-enable it, then it works great for a couple of days then stuff like audio syncing goes plop.
It's been a vicious circle.

---

### Post by Horbo on 2013-02-02
Just delete (or rename if you're paranoid/cautious) ~/.config/google-grome/PepperFlash/

Restart chrome.

Problem fixed.

---

### Post by bishop__ on 2013-02-03
> **Download Descendent said:**
> Ok, this might be useful for people.

When I used Chrome in Ubuntu 12.04 when I went to watch a video on youtube (and then any similar site) an error message of couldn't load plugin.

After re-installing Chrome which didn't work and checking around previous threads etc, I went into Tools-Task Manager noticed the Plug-in Shockwave flash was N/A.

I then typed chrome://plugins/ in the address bar, extended the libpepflashplayer and disabled /opt/google/chrome/PepperFlash/libpepflashplayer.so

And then it worked again?

Anyone know why?  It was fine until tonight.

This helps alot! 

Thanks! :)

---

### Post by awebtech on 2013-02-04
Worked for me. Thanks !

---

### Post by PJs Ronin on 2013-02-04
Two days of googling Google/Chrome/Flash/Video/Facebook all to no result.   I come back to my fav forum and the first things I read about is "video not working in Chrome" and here's how to fix it.

Ty Sir.

---

### Post by FirstByté on 2013-02-04
+1

uri: [chrome://plugins/]("chrome://plugins/")

> **Mungo85 said:**
> ...
 Followed your suggestion of disabling 

/opt/google/chrome/PepperFlash/libpepflashplayer.so

...


Thanks.

---

### Post by jajodo on 2013-02-06
Today Chrome updated for me to Version 25.0.1364.68 beta

This update pushed:
Description:	Shockwave Flash 11.5 r31
Version:	11.5.31.139
Location:	/opt/google/chrome/PepperFlash/libpepflashplayer.so

Flash is now working again.

---

### Post by washakie on 2013-02-07
Should be marked Solved, disabling:
```

Name:	Shockwave Flash
Description:	Shockwave Flash 11.5 r31
Version:	11.5.31.139
Location:	/opt/google/chrome/PepperFlash/libpepflashplayer.so
Type:	PPAPI (out-of-process)

```

Worked for me.

---

### Post by tthtlc on 2013-02-15
I had problem getting everything right, finally I found the solution:

a.   In chrome, enter "chrome://plugins" as the URL.
b.   Look up at the right side upper corner : "details", a "+" sign, click on it to expand out the details.
c.   In flash (as per the attached picture) there will be three different flash plugin:   first two are pepper flash (with different name) and third one is just "/usr/lib/flashplugin-installer/libflashplayer.so" - disable the first two pepper flash, but let the last libflashplayer.so be enabled.
d.   Create a new tab and load your youtube URL into that tab - NO closing or restarting of the entire chrome browser is needed.

Cool.

---

### Post by Jonaz77 on 2013-03-08
Hi all ubuntu fans:)


Google Chrome does not support adobe flash !!!  On Ubuntu and Linux machines Google Chrome does not work so good like on Windows!

Google Chrome has it own flash (pepper-flash) built in the browser!

THE SOLUTION

Unsintall Adobe Flash latest plugin on Ubuntu  go to Software Central in ubuntu, Reboot!! 
Install firefox 19 and install an older version of Adobe Flash example version 10.3.183.67 , you have to google
Then copy libflashplayer.so from the older version of your flash plugin you download to your firefox plugin folder

---

### Post by moonport on 2013-04-10
I had the same problem. Thanks for your help.

---

