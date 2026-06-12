---
title: "Flash Plugin"
date: 2012-10-17
forum: General Help
---

### Post by Trumusiate on 2012-10-17
Hi,

I have a problem with Flash. After a fresh installation of Ubuntu Studio (but the same thing happened with Lubuntu) I cannot have Flash working properly on either Chromium or Firefox.

After the installation and the update process, I installed the flash plugin-installer from the Ubuntu Software Center and then the flash plugin can't be loaded anymore because it crashes (the crash icon appears on my top panel).

At this point, in the about : plugins page I can only see one flash plugin for both the browsers.

Without the flash plugin-installer youtube says that my plugin needs to be upgraded. 

Thank in advance for your help.

---

### Post by Trumusiate on 2012-10-22
Ok. 
I'll add some details.
I erased the content of my home directoy (except from pictures and music) and then installed Ubuntu Studio 12.04. 
I tried both with flashplugin-installer and adobe-flashplugin. NOTHING.
It does not work.
What to do?
I touched the ceiling of my desperation process and then removed both firefox and chromium and installed chrome. It doesn'work.
There's only one plugin in about : plugins page and when I try to watch a youtube video, it simply says: could not load plugin
but If I remove the plugin then it says "you need flash player bla bla bla"
What to do?

PLEASE HELP ME.

:'-(

---

### Post by jerrrys on 2012-10-22
Have you tried installing [FONT=monospace]"[/FONT]ubuntu-restricted-extras"; this package contains flash.

[https://help.ubuntu.com/community/UbuntuStudioPreparation#The_basics](https://help.ubuntu.com/community/UbuntuStudioPreparation#The_basics)

---

### Post by Trumusiate on 2012-10-22
First of all: THANK YOU for your answer.
I installed the package, I went to youtube and it said: "you need to upgrade..." 
After that I enabled the plugin from the about: plugins page in chrome and again the browser, while in the youtube page, says "could't load plugin".

---

### Post by pqwoerituytrueiwoq on 2012-10-22
```
sudo apt-get purge flashplugin-installer adobe-flashplugin adobe-flash-properties-*;sudo apt-get install flashplugin-installer
```

---

### Post by Trumusiate on 2012-10-22
> **pqwoerituytrueiwoq said:**
> ```
sudo apt-get purge flashplugin-installer adobe-flashplugin adobe-flash-properties-*;sudo apt-get install flashplugin-installer
```

Thank you for your answer. I executed the command, it removed the plugins and then downloaded and installed the flashplugin but, again, on youtube page it says "could't load plug-in"...

:confused:

This is what is flash-related on about : plugins page:


Flash - Version: 11.2 r202
Shockwave Flash 11.2 r202
Name:	Shockwave Flash
Version:	11.2 r202
Location:	/usr/lib/flashplugin-installer/libflashplayer.so
Type:	NPAPI
 	 
MIME types:	
MIME type	Description	File extensions
application/x-shockwave-flash	Shockwave Flash	
.swf
application/futuresplash	FutureSplash Player	
.spl


before the flash entry I have Chrome Remote Desktop Viewer, Native Client and Chrome PDF Viewer. 
Even if I disable all of them the behaviour of my browser on youtube doesn't change.

---

### Post by Lyfang on 2012-10-22
Google Chrome includes Pepper Flash and Chrome Pepper Flash Player is always fully updated when you update Chrome. I use Chromium (without Installation-ID & RLZ-Tracking) for better privacy. Read this: [Re: Chromium Flash Pepper on precise, how?]("http://ubuntuforums.org/showpost.php?p=12307769&postcount=16") (Quantal Ubuntu 12.10 guide) 

My Chromium Version 22.0.1229.94 Ubuntu 12.10 (161065) web browser's about : plugins page:

Flash - Version: 11.4.31.203
Shockwave Flash 11.4 r31
Namn:	Shockwave Flash
Beskrivning:	Shockwave Flash 11.4 r31
Version:	11.4.31.203
Plats:	/usr/lib/chromium-browser/libpepflashplayer.so
Typ:	PPAPI (utanför process)
 	 Inaktivera
MIME-typer:	
MIME-typ	Beskrivning	Filtillägg
application/x-shockwave-flash	Shockwave Flash	
.swf
application/futuresplash	FutureSplash Player	
.spl

---

### Post by Trumusiate on 2012-10-22
> **Lyfang said:**
> Google Chrome includes Pepper Flash and Chrome Pepper Flash Player is always fully updated when you update Chrome. I use Chromium (without Installation-ID & RLZ-Tracking) for better privacy. Read this: [Re: Chromium Flash Pepper on precise, how?]("http://ubuntuforums.org/showpost.php?p=12307769&postcount=16") (Quantal Ubuntu 12.10 guide) 

My Chromium Version 22.0.1229.94 Ubuntu 12.10 (161065) web browser's about : plugins page:

Flash - Version: 11.4.31.203
Shockwave Flash 11.4 r31
Namn:	Shockwave Flash
Beskrivning:	Shockwave Flash 11.4 r31
Version:	11.4.31.203
Plats:	/usr/lib/chromium-browser/libpepflashplayer.so
Typ:	PPAPI (utanför process)
 	 Inaktivera
MIME-typer:	
MIME-typ	Beskrivning	Filtillägg
application/x-shockwave-flash	Shockwave Flash	
.swf
application/futuresplash	FutureSplash Player	
.spl

Thank you but I do not think that my problem is related to the flash version I am using, also I experienced the exact same issue with Opera, Firefox and Chromium.

---

### Post by pqwoerituytrueiwoq on 2012-10-22
[https://addons.mozilla.org/en-us/firefox/addon/flash-aid/](https://addons.mozilla.org/en-us/firefox/addon/flash-aid/)
try this in firefox
its changes will be applied to all browsers using adobe flash

---

### Post by Lyfang on 2012-10-23
> **Trumusiate said:**
> Thank you but I do not think that my problem is related to the flash version I am using, also I experienced the exact same issue with Opera, Firefox and Chromium.
Why don't you try Pepper Flash?

Google Chrome (and also Chromium)
I'm using Pepper Plugin API (PPAPI) Pepper Flash libpepflashplayer.so 11.4.31.203
Pros: New releases with Pepper Flash.
Cons: Only PPAPI compatible.

Opera, Firefox, Chromium and others
Netscape Plugin Application Programming Interface (NPAPI) adobe-flashplugin 11.2.202.243-0quantal1 (Quantal repository 2012-10-23)
Pros: Multiple browser support. Still five years of security updates and bug-fixes.
Cons: No new features. No new releases.

See also: [http://www.youtube.com/html5](http://www.youtube.com/html5)

---

### Post by Ace..... on 2012-10-23
> **pqwoerituytrueiwoq said:**
> [https://addons.mozilla.org/en-us/firefox/addon/flash-aid/](https://addons.mozilla.org/en-us/firefox/addon/flash-aid/)
try this in firefox
its changes will be applied to all browsers using adobe flash

I agree.
I had similar probs, and flash-aid solved them completely (what a relief it was).  
That was until pepper flash came along.

I couldn't highlight stuff or write in text fields.
So if you get flash sorted with flash-aid, and you experience the probs stated, you may need to disable pepper flash.
There's a link at the bottom that has worked for a few people, including me. :)

---

### Post by Abhinav Kumar on 2012-10-27
You can also try out this
Go to adobe site 
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
and download flash player as tar file.

Now extract the contents of tar file using archive manager.

say you extracted and you created folder named install_flash at the Desktop.
You can see there will be a file named libflashplayer.so in install_flash folder.
execute the following command in terminal
sudo cp ~/Desktop/install_flash/libflashplayer.so /usr/lib/mozilla/plugins/
give the password.
restart firefox

---

### Post by ventsyv on 2012-10-27
I also can't get the flash plugin to work. I tried everything I could think off:

1. Installed ubuntu-restricted-extras, ubuntu-restricted-addons
2. Installed flash-plugin-installer
3. Then I tried installing the plugin from adobe.com
4. Then I tried purging everything and re-installing
5. Then I tried installing chrome, that didn't work either
6. Tried installing flash-aid
7. Tried installing Chromium
8. Installed hal at some point.

I even tried installing the previous version from adobe... Nothing works. How come it's so difficult to get something simple as flash working??????

I also followed the Comprehensive Multimedia How-to here:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by Ace..... on 2012-10-29
What I did was install flash-aid into Firefox.

It appears in the top right hand corner.

Doubleclick on it (the icon), and follow its recommendations.

This will install the correct flash into firefox, and at the same time, it will install the correct flash for google chrome.

But remember - flash-aid is installed into firefox, not chrome.

Also (and this may not apply to you), I would suggest not trying everything (file changes etc.) at high speed.

You can easily end up not knowing what exactly you've done.

Very often you need time to reflect on what you are doing/have done, and time to reflect on forum advice, and your next question.

Flash-aid usually sorts this problem out - some people don't even click on it! :wink:

---

### Post by Lyfang on 2012-10-29
> **Ace..... said:**
> I agree.
I had similar probs, and flash-aid solved them completely (what a relief it was).  
That was until pepper flash came along.

I couldn't highlight stuff or write in text fields.
So if you get flash sorted with flash-aid, and you experience the probs stated, you may need to disable pepper flash.
There's a link at the bottom that has worked for a few people, including me. :)
Do you have an example of a website having problems with "highlight stuff or write in text fields"?

---

### Post by Ace..... on 2012-10-30
> Do you have an example of a website having problems with "highlight stuff or write in text fields"?

It's a big problem - just google it and it's everywhere.
Quite a few on Ubuntu - if I see them I will step in, but the forum moves so quickly these days. Posts just a few hours old can be 3 pages away

The difficulty I had was configuring the search to get the answer I needed, that I'd found a couple of months earlier, and lost during a re-install.

moral of the story - always bookmark the great fixes. :wink:

This is why I detailed the fix and put it in my sig.
I now regret that I didn't make the title more relevant to the problem.

People who have this problem often don't know the cause is pepper flash.

This was one chaps question:

Migrated to Linux (Ubuntu).. Need help
[http://ubuntuforums.org/showthread.php?t=2071304](http://ubuntuforums.org/showthread.php?t=2071304)

By chance I read it, and here was his no1 prob:

1. When surfing on Chrome, there are several webpages that do not function properly and seem broken (scroll bars do not work, cannot fill in forms etc.) and there are glitches while watching Youtube.


Here is a reasonable search for google. At least this takes you to pepper flash probs:

[INDENT]"google chrome disable pepper flash"[/INDENT]

Bizarrely, I'm experiencing the same problems right now.

I downloaded WebHTTrack, which loads chrome itself ie. bypassing my created launcher that includes the disable command.

Which means I can recreate the problem (and eliminate it) at will.

:)> 

---

### Post by realbanda on 2013-02-03
> **Trumusiate said:**
> Hi,

I have a problem with Flash. After a fresh installation of Ubuntu Studio (but the same thing happened with Lubuntu) I cannot have Flash working properly on either Chromium or Firefox.

After the installation and the update process, I installed the flash plugin-installer from the Ubuntu Software Center and then the flash plugin can't be loaded anymore because it crashes (the crash icon appears on my top panel).

At this point, in the about : plugins page I can only see one flash plugin for both the browsers.

Without the flash plugin-installer youtube says that my plugin needs to be upgraded. 

Thank in advance for your help.

1. Go to chrome://plugins/
2. There u will find libpepflashplayer and Adobe Flash Player
3. Allow only one of them and disable the other
4. Done.
Enjoy

---

### Post by andril on 2013-02-05
> **realbanda said:**
> 1. Go to chrome://plugins/
2. There u will find libpepflashplayer and Adobe Flash Player
3. Allow only one of them and disable the other
4. Done.
Enjoy

This was the solve for me - I had to disable /opt/google/chrome/PepperFlash/libpepflashplayer.so
=D>

---

