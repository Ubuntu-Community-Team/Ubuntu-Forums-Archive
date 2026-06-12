---
title: "Macromedia Flash"
date: 2004-11-01
forum: General Help
---

### Post by thor on 2004-11-01
Hi!

Could someone help me with installing Macromedia Flash plugin for Firefox?  I have installed flashplugin-nonfree package, but it doesn't seem to change anything..

Am I missing something?

Also, I tried to download flash plugin from their site and install it by launching supplied install script, but after that firefox starts in some "frozen" state - I can't access menus or address bar, anything I can do is to shut it down..

Any hints/comments!

Thanks!

---

### Post by im_ka on 2004-11-01
you can install it directly in firefox.

i think it was tools/extensions.

---

### Post by fng on 2004-11-01
instead of installing the flashplugin-nonfree version, you should install flashplayer-mozilla

---

### Post by ubuntu-geek on 2004-11-01
This might help out too..

[http://ubuntuforums.org/showthread.php?t=198](http://ubuntuforums.org/showthread.php?t=198)

---

### Post by tkz on 2004-11-01
I installed flash for firefox this way:

FIrst get the flash player from [here](http://fpdownload.macromedia.com/get/shockwave/flash/english/linux/7.0r25/install_flash_player_7_linux.tar.gz) 

After the file downlowads you need to open it. To uncompress the package in Ubuntu, just click with right mouse button and select *Extract here*.

In the new folder that appers, you will find files *flashplayer.xpt* and *libflashplayer.so*. Select these files and right click + copy them.

Go to folder .mozilla in your home directory. You can find it if you select Show hidden files from the View -menu of nautilus. In the .mozilla -folder there is a folder *plugins* and this is the folder that the two flash plugin files go.

Now start firefox and flash should be working. It worked for me, good luck  8)

---

### Post by Vlammend on 2004-11-02
I did this, but does someone has a flash example, because everything I encounter says the type is application/x-shockwave-flash.

Shockwave can only be plugged into Firefox using Wine (it says on the Firefox plug-ins FAQ) in combination with a commercial program.

---

### Post by jdong on 2004-11-02
install flashplayer-mozilla from Synaptic. No guesswork.

---

### Post by az on 2004-11-02
I installed flashplugin-nonfree from universe.

Try:

[www.thewiggles.com](www.thewiggles.com)

You will know right away if flash is working...

---

### Post by mercurus on 2004-11-03
Quick solution:

sudo apt-get remove flashplayer-nonfree &&
sudo apt-get install flashplayer-mozilla

Restart mozilla, and browse to:
about:plugins

You should get output something like:
```

Default Plugin

    File name: libnullplugin.so
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

MIME Type 	Description 	Suffixes 	Enabled
* 	All types 	.* 	Yes
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 7.0 r25

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
```

If not, flash isn't working or isn't correctly associated with mozilla, try and remove any extraneous packages you may have installed to try and solve the issue.

(sorry, I would attach a screenshot of the above but my png was 62Kb, and too large for the forums to accept)

Cheers
mercurus

---

### Post by vafnord on 2004-12-05
When I try: 

```
sudo apt-get install flashplayer-mozilla
```
I get:

```
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package flashplayer-mozilla
```

---

### Post by WW on 2004-12-05
flashplayer-mozilla is in the **multiverse** component of the Ubuntu repository, so check that you have multiverse enabled.

---

### Post by kermy on 2004-12-06
I'm having problems with text not being displayed in flash. What could be the problem?

---

### Post by zygomatic on 2004-12-17
[QUOTE=tkz]I installed flash for firefox this way:

FIrst get the flash player from [here](http://fpdownload.macromedia.com/get/shockwave/flash/english/linux/7.0r25/install_flash_player_7_linux.tar.gz) 

After the file downlowads you need to open it. To uncompress the package in Ubuntu, just click with right mouse button and select *Extract here*.

In the new folder that appers, you will find files *flashplayer.xpt* and *libflashplayer.so*. Select these files and right click + copy them.

Go to folder .mozilla in your home directory. You can find it if you select Show hidden files from the View -menu of nautilus. In the .mozilla -folder there is a folder *plugins* and this is the folder that the two flash plugin files go.

Now start firefox and flash should be working. It worked for me, good luck  8)[/QUOTE]


This worked for me.  Thank you very much.

---

### Post by melkor on 2004-12-26
when I tried to copy them into the plugins folder it said that I don't have permission to write to this folder.

How do I fix this?

---

### Post by node on 2004-12-26
get [this](http://www.macromedia.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux&P3_Browser_Version=Netscape4). Run the flash-installer and set path /usr/lib/mozilla-firefox.
Works like a charm.

---

### Post by melkor on 2004-12-26
when I open the install file I tell it to run in the terminal (it does not do anything if I tell it to just run it).

after I get to the line where it reminds you to close all browsers, I close my browsers, press enter, and then it quickly writes text in the terminal but then closes the window before I can see what it displayed. It never asks me to enter a path.

Note I just unrolled the folder to my desktop and ran it from there.

Now when I try to view a flash page such as lordoftherings.net i just get that pu8zzle piece sign in the middle of the page and it says I am missing a plugin.

---

### Post by devnull on 2004-12-30
[QUOTE=node]get [this](http://www.macromedia.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux&P3_Browser_Version=Netscape4). Run the flash-installer and set path /usr/lib/mozilla-firefox.
Works like a charm.[/QUOTE]


This worked.  Thanks.  Make sure you have gsfonts and gsfonts-x11 installed.  It'll prompt you for it during the install procedure though incase you forget.

---

### Post by melkor on 2004-12-30
mine is working now also, before I was trying to run it graphically and not from the terminal.

---

### Post by panabar on 2005-02-04
[QUOTE=kermy]I'm having problems with text not being displayed in flash. What could be the problem?[/QUOTE]

I've had the same problem the first thing you should do is install the gsfonts and gsfonts-x11 (I guess these are on the warty main repository).  After this you shoud be able to see some of the text. If some invisible text remains ( which was the case for me), you should install **msttcorefonts** package which installs an installer for some of the widely used fonts, such as    
 "Andale Mono
  Arial Black
  Arial (Bold, Italic, Bold Italic)
  Comic Sans MS (Bold)
  Courier New (Bold, Italic, Bold Italic)
  Georgia (Bold, Italic, Bold Italic)
  Impact
  Times New Roman (Bold, Italic, Bold Italic)
  Trebuchet (Bold, Italic, Bold Italic)
  Verdana (Bold, Italic, Bold Italic)
  Webdings1".
After installing msttcorefonts you shoul run update-ms-fonts to download and install these fonts to your system. 

This should be the solution to your problem ( as it was the solution for mine).

Some links for msttcorefonts package:

[http://volker.dnsalias.net/linux/msttcorefonts.html](http://volker.dnsalias.net/linux/msttcorefonts.html)  

[http://packages.debian.org/unstable/graphics/msttcorefonts.html](http://packages.debian.org/unstable/graphics/msttcorefonts.html)

---

### Post by Azkatro on 2005-06-05
[QUOTE=panabar]I've had the same problem the first thing you should do is install the gsfonts and gsfonts-x11 (I guess these are on the warty main repository).  After this you shoud be able to see some of the text. If some invisible text remains ( which was the case for me), you should install **msttcorefonts** package which installs an installer for some of the widely used fonts, such as    [/QUOTE]

I might just add to this that this uses wget to download the packages, so if you need to specify a proxy use the following at the command line:

```
> export http_proxy="http://proxyurl:port/"
> sudo update-ms-fonts
```

---

### Post by Sweezel on 2005-07-13
Forgive me, I am a newbie female who is struggling...


I have tried flashplayer-mozilla and an install from Macromedia, but it still doesn't work on this page:

[http://www.discounttiredirect.com/direct/brochure/interactive/tmpInteractive.jsp](http://www.discounttiredirect.com/direct/brochure/interactive/tmpInteractive.jsp)


about:plugins shows that it is installed and enabled, but the page says I am missing the plugin. 

BTW - Why doesn't the Firefox plugin installer work?

---

### Post by Paul_M on 2005-08-01
Hi, new to this forum, i appear to have a slight sound problem with Macromedia Flash in firefox, i tested it on a machine running another OS with firefox and the sound was perfectly fine, so that rules out a firefox, and possibly content, problem, so it could be down to some configuration that i may have overlooked, or there is a problem with the flash plug-in for Linux.  has anyone else had this problem and managed to fix it? if so how was it fixed? I would appreciate all the help i can get to fix this problem soon

Thanks

Paul

---

### Post by wmcbrine on 2005-08-08
[QUOTE=Sweezel]I have tried flashplayer-mozilla and an install from Macromedia, but it still doesn't work on this page:

[http://www.discounttiredirect.com/direct/brochure/interactive/tmpInteractive.jsp](http://www.discounttiredirect.com/direct/brochure/interactive/tmpInteractive.jsp)
[/QUOTE]
That page uses Shockwave rather than Flash. They're different, although both are from Macromedia nowadays. There's no Shockwave plugin for Linux, sorry.

Paul, what is the nature of your sound problem?

I've had bad audio/video sync in Flash in the past, but that's all.

---

### Post by DougInKY on 2005-08-09
<<<I've had the same problem the first thing you should do is install the gsfonts and gsfonts-x11 (I guess these are on the warty main repository).>>>  

Thank you for the fix for no text in flash. This has bugged me for a long time. Your posts are very useful.

DougInKY   :)

---

### Post by Paul_M on 2005-10-08
[QUOTE=wmcbrine]Paul, what is the nature of your sound problem?

I've had bad audio/video sync in Flash in the past, but that's all.[/QUOTE]

It isn't playing any sound at all, and on checking the same content I was viewing on another computer using another OS but same browser the audio was working

Sorry it took me so long to reply, i've been busy with other things

---

### Post by movil on 2005-12-21
Is there any way to port the shockwave player (not flash) to linux ?
I did a search:
[http://www.google.es/search?q=shockwave+linux](http://www.google.es/search?q=shockwave+linux)

It seems Macromedia just 've windows version and OSX, but no linux support...

---

### Post by WirelessMike on 2006-04-10
A really fun site to test flash with is [http://www.lordoftherings.net/]("http://www.lordoftherings.net/")

The site is all flash.  If you have a bad version of gplflash, all you will see are black boxes where the pictures should be.  There are plenty of interactive graphics and audio right on the home page, so you can test all of those, too.

---

### Post by arthur on 2006-05-13
I have Firefox 1.5.0.3 installed via Automatix.
The result of
about:plugins is

Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 7.0 r25

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

However, the following page is not properly displayed:
[http://www.parchis.com/juego.php/MzA0Mg](http://www.parchis.com/juego.php/MzA0Mg)

Am I missing something?

---

### Post by MikeDK on 2006-06-27
well it dosnt work on 6.06 LTS

---

### Post by airjunman on 2006-06-27
I am new so my advice may be lame or redundant ... anyways there're probably a few newbies who maaayyy benefit...

When you're checking your installation be sure of the version of flash the site uses.. I was checking mine on a site that used v8, and i think Linux flash player is v7.. so I kept thinking I dont have flash installed...

this is a good site to check the installation based on the version
[http://www.bestflashanimationsite.com/vote/](http://www.bestflashanimationsite.com/vote/)

anyways, thats my cents worth...

---

