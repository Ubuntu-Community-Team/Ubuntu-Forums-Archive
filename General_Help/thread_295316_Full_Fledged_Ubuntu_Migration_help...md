---
title: "Full Fledged Ubuntu Migration help.."
date: 2006-11-07
forum: General Help
---

### Post by alisemail on 2006-11-07
Hey so i tried Ubuntu before and some how it got corrupted. I lost patience and switched back to Windows. I am back and this time am tired of Windows despite having kept it immaculately clean slowing to a crawl.

So my general Ubuntu plan and questions:

1. Primarily the PC will be used for Media Playing, Graphics/Web Development and occassionally gaming. (Internet is an obvious one I hope?)

2. Loading SAMBA - Question: Other PCs (Windows) will be connecting to play media (Mp3s, WAVs, WMAs, AVIs, MPEGs, DivX Files) that are stored on the Server. They also must copy or save files from Windows (NTFS Formatted) to or from the Ubuntu box. What do I need to format my Ubuntu drive etc as for this?

3. Primarily Dreamweaver and Photoshop are used in combination along with Trillian on my Windows PC, I know GIMP is good to replace Photoshop and I believe Trillian and GAIM are covered with Ubuntu. Now any recommendations for Dreamweaver replacements? I like it primarily for the Syntax Highlighting in PHP and ColdFusion.

4. I will need to load ColdFusion server onto this Ubuntu Box. I am thinking a Tomcat/ColdFusion combination along with MySQL. Is there anything I need to know before loading these things together or guides out there?

So far these are my only questions before I make the migration to an Ubuntu box. if anyone could help answer these questions or point me to forums/guides that answer that'd be great.

---

### Post by alisemail on 2006-11-07
Quick addon: THe machine in question is an AMD X2 4400 with 2GB RAM and uses an NVIdia 7800GT Graphics card. Are there any compatability issues or specific builds I need to download?

---

### Post by reclusivemonkey on 2006-11-08
> **alisemail said:**
> 
1. Primarily the PC will be used for Media Playing, Graphics/Web Development and occassionally gaming. (Internet is an obvious one I hope?)

Can't remember the last time I couldn't play any media in Linux. I have had a much easier time that I did in Windows. Between MPlayer and VLC, there shouldn't be anything you can't play other than DRM'ed music. There is a project to get DRM working on Linux as a Gstreamer plugin. I forget the name of the project now. You won't be able to play all games on Linux. I would keep XP on dual boot for gaming. This is what I do.

> **alisemail said:**
> 2. Loading SAMBA - Question: Other PCs (Windows) will be connecting to play media (Mp3s, WAVs, WMAs, AVIs, MPEGs, DivX Files) that are stored on the Server. They also must copy or save files from Windows (NTFS Formatted) to or from the Ubuntu box. What do I need to format my Ubuntu drive etc as for this?

Reading from NTFS is fine. Writing to it not so simple. There is a project to get NTFS writing, not sure how stable it is. To make things easy, use a FAT32 drive to share items between Linux/Windows. I would dedicate a HD to this, or at least a partition.

> **alisemail said:**
> 3. Primarily Dreamweaver and Photoshop are used in combination along with Trillian on my Windows PC, I know GIMP is good to replace Photoshop and I believe Trillian and GAIM are covered with Ubuntu. Now any recommendations for Dreamweaver replacements? I like it primarily for the Syntax Highlighting in PHP and ColdFusion.

I'm strictly a code man when it comes to HTML and CSS. I don't think you will find anything that holds your hand as much as Dreamweaver, but nvu, Screem and Bluefish will offer some features that Dreamweaver has. As pretty much anyone will tell you, Gimp is not Photoshop. But its the closest you'll get. You also might want to take a look at the Open Source version of Xara; its looking pretty nice and was stable last time I tried it. Gaim will do almost everything Trillian can; at very least it will support any IM protocol you care to use (although maybe not all the features).

For anything else, search the forums then google. You will find all your questions have been asked and answered before :-) Feel free to ask me anything else.

I would keep a dual boot while you attempt to switch. Not everything will go swimmingly.

---

### Post by handy on 2006-11-08
Forget Dreamweaver, there are other free replacements that ex Dreamweaver user's are very happy with. Photoshop can work, how well I can't tell. Internet is cooler & more secure.

A huge amount of codecs work, though I think Shockwave might still be a problem? I don't use it.

You will find good  news & bad news in your transition, like all other transitions I suppose?

I would recommend the Dapper 6.06 version of Ubuntu, to start with, it is more stable for more people.

Have a look at [Codeweavers]("http://www.codeweavers.com/") for windoze application support.

---

### Post by bsussman on 2006-11-08
For web development, quanta+ is very good

It is not deramweaver but that is probably a very good thing... :)

---

### Post by ubuntu27 on 2006-11-08
[Bluefish]("Bluefish")
[URL="http://www.screem.org/"]
Screem[/URL]

[Quanta]("http://quanta.kdewebdev.org/")

[NVU]("http://www.nvu.com/")

Are the most commun WYSIWUG web editors in GNU/Linux.



Looks like DreamWeaver **4** can bi installed in Linux under [Wine]("http://www.winehq.com/") but I bet you don't want that old version of Dw.

There has been rumors that there were some people that were able to run Dreamweaber MX with Wine.


You can also try: Aptana: [http://www.aptana.com/](http://www.aptana.com/)


I just found a guide for Installaing DreamWeaver 8 with Wine: [This]("http://blog.publicidadpixelada.com/2006/09/04/how-to-dreamweaver-and-flash-8-running-on-ubuntu-dapper/") or [this]("http://blog.publicidadpixelada.com/2006/07/30/how-to-dreamweaver-running-on-ubuntu-in-10-easy-steps/").


Another EDIT: Looks like DreamWeaver MX can be installed using [CroosOverOffice]("http://www.codeweavers.com/")

CrossOver is a Commercial App though, so you will have to pay for that. :)

---

### Post by handy on 2006-11-09
Crossover unlike Cedega (windoze games support) is really quite reasonably priced, & they have a really good reputation for actually doing what they say they can do, unlike Cedega.

Wine may or may not be more time & trouble than you are prepared to put in, it depends on your geek level?

---

### Post by alisemail on 2006-11-09
Thanks for all the quick tips. I'll be trying this on a secondary computer first and set it up as a test server. If everything goes smoothly ill convert the second computer. I'll reformat a secondary HD as FAT32 and keep the primary to whatever linux default format is. Im guessing this should help with the read/write problems.

---

### Post by strabes on 2006-11-09
for help with mounting window$ partitions check out [http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows)

Assuming you're using edgy. if not then it's pretty easy to find the dapper guide on that wiki...

---

### Post by handy on 2006-11-09
> **alisemail said:**
> Thanks for all the quick tips. I'll be trying this on a secondary computer first and set it up as a test server. If everything goes smoothly ill convert the second computer. I'll reformat a secondary HD as FAT32 and keep the primary to whatever linux default format is. Im guessing this should help with the read/write problems.

Apparently there is a reliable way to read & ***write*** to ntfs, if you prefer to use that filesystem (larger file size & more secure than fat32) it shouldn't take much of a search to find it.

Someone may post the info' in this thread for you?

---

