---
title: "Problem with Flash in Chromium"
date: 2016-11-07
forum: General Help
---

### Post by renardrusse on 2016-11-07
Hello,

I justed switch from ubuntu mate 15.10 to mate 16.04

I install chromium and pepper flash from synaptic. 

When I start chromium there is some videos that I can't read and I get this message : Click here to download the new adobe flash player. 

I'm sure I have the most rescent version install and when I was on 15.10 I had no problem to see all videos after installing pepperflash the same way.

I checked too in usr/lib/chromium-browser/plugins
I have 0 item in the folder. 

I tried to download the libpepflashplayer.so from adobe site to copy it in the pugins floder, but it says that I don't have priviledge to do that. I could'nt go further.

I also look at : [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/),
it says could'n load plugin

I typed : chrome://plugins/ in the toolbar and here what I can find:

Adobe Flash Player - Version: 11.2.999.999
Shockwave Flash 11.2 r999
Name:    Shockwave Flash
Description:    Shockwave Flash 11.2 r999
Version:    11.2.999.999
Location:    /usr/lib/pepperflashplugin-nonfree/libpepflashplayer.so
Type:    PPAPI (out-of-process)
     Disable
MIME types:    
MIME type    Description    File extensions
application/x-shockwave-flash    Shockwave Flash    
.swf
application/futuresplash    FutureSplash Player    
.spl
Disable   Always allowed to run (check)



I spent many hours reading about it, I'm getting a little bit upset with this LTS version, that give me more bugs than 15.10. and no forum yet that could help me.

I'm begging for some help, I'm not very advanced in linux, but if feel I read all I could find and I don't see anymore solutions than going back too 15.10.

Thank you!

Olivier Légaré

---

### Post by CantankRus on 2016-11-08
[**[COLOR="#B22222"]Getting-Flash[/COLOR]**]("https://wiki.ubuntu.com/Chromium/Getting-Flash")
> As of 2015-05, the old "pepperflashplugin-nonfree" is deprecated in favor of an official, maintained, 
one-step package called adobe-flashplugin, which works for Firefox and Chromium and derivatives

Check the Canonical Partner repository is enabled...
```
software-properties-gtk --open-tab 1
```
[ATTACH=CONFIG]272030[/ATTACH]


If you don't have a "Canonical Partner" entry you can add it to sources.list.... 
```
sudoedit /etc/apt/sources.list
```

Copy and paste this line into the file(use arrow keys to move the cursor in nano)...
```
deb http://archive.canonical.com/ubuntu xenial partner
```
Then hit ctrl+x, then y followed by Enter to save.



Update sources and install...
```
sudo apt update
sudo apt install adobe-flashplugin
```

---

