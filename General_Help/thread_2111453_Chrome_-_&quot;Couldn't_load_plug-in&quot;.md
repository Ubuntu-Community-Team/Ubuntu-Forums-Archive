---
title: "Chrome - &quot;Couldn't load plug-in&quot;"
date: 2013-02-02
forum: General Help
---

### Post by 98cwitr on 2013-02-02
Works in Firefox though, so it's not hardware. Chrome version is 24.0.1312.57. Ubuntu 12.04 LTS

Flash version: 11.5.31.138


Other details from about:plugins

Adobe Flash Player (2 files) - Version: 11.5.31.138
Shockwave Flash 11.5 r31
Name:	Shockwave Flash
Description:	Shockwave Flash 11.5 r31
Version:	11.5.31.138
Location:	/home/user/.config/google-chrome/PepperFlash/11.5.31.138/libpepflashplayer.so
Type:	PPAPI (out-of-process)
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/x-shockwave-flash	Shockwave Flash	
.swf
application/futuresplash	Shockwave Flash	
.spl
Name:	Shockwave Flash
Version:	11.2 r202
Location:	/usr/lib/flashplugin-installer/libflashplayer.so
Type:	NPAPI
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/x-shockwave-flash	Shockwave Flash	
.swf
application/futuresplash	FutureSplash Player	
.spl
Disable   Always allowed
libpepflashplayer (10 files)
Name:	
Version:	
Location:	/opt/google/chrome/PepperFlash/libpepflashplayer.so
Type:	NPAPI
 	 Disable

---

### Post by MarcoDePollo on 2013-02-02
This is happening to me too, though flash is working in Rekonq.

edit: I can't remember using flash recently, so I would assume it was the update I installed wednesday that broke it.

---

### Post by garnedi on 2013-02-02
Same problem for me too. It's working fine in firefox, It's not working in chrome.

---

### Post by 98cwitr on 2013-02-02
glad im not the only one :)

---

### Post by garnedi on 2013-02-02
***SOLVED***

goto chrome://plugins/
click on details (top right)
disable adobe flash player

Name:	Shockwave Flash
Version:	11.5.31.138

then restart the browser.

hope this'll work.

---

### Post by Download Descendent on 2013-02-02
There is an earlier thread:

[http://ubuntuforums.org/showthread.php?t=2111411](http://ubuntuforums.org/showthread.php?t=2111411)

---

### Post by deadflowr on 2013-02-02
> **garnedi said:**
> ***SOLVED***

goto chrome://plugins/
click on details (top right)
disable adobe flash player

Name:	Shockwave Flash
Version:	11.5.31.138

then restart the browser.

hope this'll work.

No need to restart, just reload the page.

---

### Post by vasa1 on 2013-02-02
> **download descendent said:**
> there is an earlier thread:

[http://ubuntuforums.org/showthread.php?t=2111411](http://ubuntuforums.org/showthread.php?t=2111411)

+1.

---

### Post by rcentros on 2013-02-02
This is an issue with Flash 11.5.31.138. Since 11.5.31.137 worked fine (and for me much better than 11.2.xx.xxx), and since 11.5.31.137 is probably still on your computer (under /opt/...), a better work-around is detailed at:

[http://code.google.com/p/chromium/issues/detail?id=173790](http://code.google.com/p/chromium/issues/detail?id=173790)

Look at Message #31. Instead of deleting the ~/.config/google-chrome/PepperFlash directory, I just renamed it to PepperFlash2. 

After restarting Chrome, under chrome://plugins you'll then see that Chrome is using Flash 11.5.31.137 -- and all is back to what it was before Google pushed out the update (and this is nothing anyone did, no regular updates -- it's a "push update" done by Google).

---

### Post by Horbo on 2013-02-02
Just delete (or rename if you're paranoid/cautious) ~/.config/google-grome/PepperFlash/

Restart chrome.

Problem fixed.

---

### Post by TheChristianHippie on 2013-02-02
> **garnedi said:**
> ***SOLVED***

goto chrome://plugins/
click on details (top right)
disable adobe flash player

Name:	Shockwave Flash
Version:	11.5.31.138

then restart the browser.

hope this'll work.

Did this and just refreshed the page as per deadflowr suggestion. WORKED FOR ME ):P Thanks guys!

---

### Post by thagoat on 2013-02-02
Awesome! Worked like a charm. Thanks

---

### Post by gerowen on 2013-02-02
That fix worked for a minute, but then after a few minutes and watching a few YouTube videos I started getting "Adobe Flash Player is not installed" messages on YouTube.

---

### Post by gerowen on 2013-02-02
Figured it out.  I just had to disable Chrome's "PepperFlash" plugin so it would use the Adobe plugin.  The videos I were able to watch after disabling Adobe Flash altogether just happened to be ones that supported HTML5.  It's all working fine now, and I've attached a screenshot showing which one I disabled for those that aren't sure which one worked for me.

---

### Post by 98cwitr on 2013-02-02
Disabled pepperflash...working now.

---

### Post by monkeybrain2012 on 2013-02-03
In other words pepper flash is still not working. Kind of ironic that many people install chrome because of updated flash.

BTW, go to about://plugins and see that beside the entry of pepper flash there is a note "out of process", what does that mean?

---

### Post by Navyairtech on 2013-02-03
> **garnedi said:**
> ***SOLVED***

goto chrome://plugins/
click on details (top right)
disable adobe flash player

Name:	Shockwave Flash
Version:	11.5.31.138

then restart the browser.

hope this'll work.

--------------------------

Worked like a charm! Thank you!

---

### Post by SPMcKinney on 2013-02-04
> **monkeybrain2012 said:**
> In other words pepper flash is still not working. Kind of ironic that many people install chrome because of updated flash.

BTW, go to about://plugins and see that beside the entry of pepper flash there is a note "out of process", what does that mean?

That was my main reason for it and I was curious about that too, found something about the two different processes (in-process and out-of-process) but its about the gnome panel but it should still give an answer.

[INDENT]*"In-process applets do offer a slightly better performance when the applet is loaded, but this should not affect much the user experience. However, an in-process applet can potentially affect the whole behavior of the panel, especially in case of crashes or memory corruptions: a crash in an in-process applet will crash the whole panel."*[/INDENT]

What I get is its just a safety thing to keep from Chrome crashing every time pepper flash doesn't load, hence the "Could not load plugin" message. I could be wrong have to have someone confirm it, if anyone can.

But anyway its a massive pain I hope Google sorts it out soon gonna try the "reverting" to the last version [_rcentros mentioned_]("http://ubuntuforums.org/showpost.php?p=12488879&postcount=9").

---

### Post by carl4926 on 2013-02-04
I have
```
Version: 11.5.31.137
Shockwave Flash 11.5 r31
Name:	Shockwave Flash
Description:	Shockwave Flash 11.5 r31
Version:	11.5.31.137
Location:	/opt/google/chrome/PepperFlash/libpepflashplayer.so
Type:	PPAPI (out-of-process)

```

Using : Version 24.0.1312.57 of chrome

All is good

---

### Post by wewa on 2013-02-04
> chrome://plugins/ then disable libpepflashplayer

Rebooted computer.
Did this but still problematic. I am on Linux Mint 12 LXDE 'Lisa'.

Now every flash page says at the top:

Adobe Flash Player was blocked because it is out of date.
[Run This Time]   [Update plug-in...]


Choosing
[Run This Time]
option results in:

When Adobe Flash Player has finished updating, reload the page to activate it.


Choosing
[Update plug-in...]
results in:

[http://get.adobe.com/flashplayer/?no_redirect](http://get.adobe.com/flashplayer/?no_redirect)

If you are using the Google Chrome browser, Adobe® Flash® Player is built-in but has been disabled. To enable Flash Player, follow the steps in this TechNote
To learn more about the enhanced support for Flash Player in Chrome, including information for developers, see this TechNote.
If you are using the open source Chromium browser, please download and install the Flash Player plug-in below.
To learn more about Flash Player and Chromium, see this TechNote.
Download Adobe Flash Player
Adobe Flash Player version 11.2.202.261
Your system: Linux 32-bit, Chrome
Different operating system or browser?
Learn more  |  System requirements  |  IT/OEM Admins - Distribute Flash Player

NOTE: Adobe Flash Player 11.2 will be the last version to target Linux as a supported platform. Adobe will continue to provide security backports to Flash Player 11.2 for Linux.

Select version to download:
YUM
.tar.gz
.rpm
APT



On Sunday, February 3, 2013 2:45:39 AM UTC-10, mehdi.qoreishi wrote:
> in the chrome address bar type: chrome://plugins/ then disable libpepflashplayer. restart the chrome. done!

---

### Post by elimisteve on 2013-02-04
Disabling/re-enabling Flash didn't work for me.

I just moved the PepperFlash directory with

    mv ~/.config/google-chrome/PepperFlash/ ~/.config/google-chrome/PepperFlash.bak

as suggested here [http://askubuntu.com/a/250483/125596](http://askubuntu.com/a/250483/125596) and that worked perfectly.

Thanks, all!

---

### Post by carl4926 on 2013-02-04
chrome has been patched now

---

### Post by z987k on 2013-02-05
> **carl4926 said:**
> chrome has been patched now

The version in the ubuntu repositories or some latest build?

---

### Post by carl4926 on 2013-02-05
The update fed thru last night on the stable version
Version 24.0.1312.68

---

### Post by aaronLund on 2013-02-05
> **garnedi said:**
> ***SOLVED***

goto chrome://plugins/
click on details (top right)
disable adobe flash player

Name:	Shockwave Flash
Version:	11.5.31.138

then restart the browser.

hope this'll work.

Thanks!  Worked!

---

### Post by hypernihl on 2013-02-05
Just downloaded the most recent stable version of Chrome, and it fixed nothing. Not a big deal, some of the fixes given in this thread worked.

---

### Post by carl4926 on 2013-02-05
> **hypernihl said:**
> Just downloaded the most recent stable version of Chrome, and it fixed nothing. Not a big deal, some of the fixes given in this thread worked.

If you had used the broken Chrome then you would still need to clear up the ~/.config/google-chrome/PepperFlash/
Which contains the problem 11.5.31.138

---

### Post by vasa1 on 2013-02-06
> **carl4926 said:**
> If you had used the broken Chrome then you would still need to clear up the ~/.config/google-chrome/PepperFlash/
Which contains the problem 11.5.31.138
Oddly, I didn't have the "couldn't load plug-in" error with the previous version when so many others were seeing it. Then, on updating to the latest (24.0.1312.68), the error surfaced. So I had to delete ~/.config/google-chrome/PepperFlash/ and restart to get Pepper Flash to work. In other words, IMO, the bug hasn't been fixed in the latest version but, fortunately, the same fix works.

---

### Post by raymondvillain on 2013-02-06
Thanks so much garnedi very simple very effective.  solved everything.

---

### Post by aaronLund on 2013-02-11
The plot thickens........

I was having problems with _*specific*_ youtube videos.  (At least, that's the way it seemed.)

For instance, this one wouldn't play:
[http://www.youtube.com/watch?v=TpDswaM_CJo](http://www.youtube.com/watch?v=TpDswaM_CJo) 

And instead of the "Couldn't load plug-in" message, I was getting "The Adobe Flash Player is required for video playback.....Get the latest Flash Player".

However, this one will play:
[http://www.youtube.com/watch?v=JjeOxKeXKr0](http://www.youtube.com/watch?v=JjeOxKeXKr0)

So then I do an update:
```
Preparing to replace google-chrome-stable 24.0.1312.68-r180326 (using .../google-chrome-stable_24.0.1312.69-r180721_i386.deb) ...
```

....and the same message.

So then I go into 'about://plugins' and have to *_ENABLE_* 'Adobe Flash Player' (Version 11.5.31.139)

....and here I thought that the advice in this thread was all about DISABLING things in 'about://plugins'. 

Things change fast around these parts.  

Hope this helps someone else.

---

