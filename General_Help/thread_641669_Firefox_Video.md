---
title: "Firefox Video"
date: 2007-12-15
forum: General Help
---

### Post by Spektyr on 2007-12-15
Okay, yes, there's a bunch of these threads.

Too many.  There's dozens, they all have different solutions, and I'm dizzy from trying to figure out what's going on, what to try next, and everything else.

I just want to be able to watch streaming video on the web.  This should not be complicated and it should not require intimate knowledge of codecs and whatnot.


Is there a checklist somewhere?  A definitive How-To?

All I've found are threads like this one, where someone says "Hey, video doesn't work for me in Firefox" and then a few people come along, offer a few different suggestions, and the thread fades into obscurity with no indication of which - if any- of the answers worked.  It's such a common problem there should be a common answer.

I've installed every codec I could find in Automatix.  I've installed the plugin for Firefox that's supposed to let you open video in a separate viewer.  I've done a few other things that I don't remember.

I'm confused, I'm concerned that trying "everything" will just break things worse than they already are, and I'm tired.

BTW, this is for Gutsy... I haven't updated my profile because absolutely nothing got better when I "upgraded" and several things got worse.


Any help?

---

### Post by randcoop on 2007-12-15
There are, in fact, some how to's available on the forum that can explain the basics of watching various kinds of video.  But your non-specific complaint makes a simple answer virtually impossible.

Some things you haven't said:

What Firefox are you using (version number)?
What plugins are installed (type about:config in the address bar of Firefox to see which ones you've got)?
What kinds of video do you want to watch (you can say Windows Media Player, RealPlayer, Quicktime, Flash, or all of those, or you can say the file extension types, such as .rm, .ram, .asx,.asp...etc.)?


Understand that virtually all video (except for Quicktime for Apple) available on the Web was created for users of Windows operating systems.  So Linux users are always playing catch-up.

The solutions for Linux users are myriad, as you rightly point out.  One reason for that is simply that open source development leads to this hodgepodge that is sometimes infuriating.  Another reason, though, is that there are so many different computers with so many different video cards and so many different sound cards.  Here again, it is essential to remember that all the makers of those cards work to have them compatible with Windows, not Linux.  In some cases, they produce no drivers at all for Linux users, in which case the Linux developers have to do it themselves.

You say that you've installed the plugin that supposed to work in Firefox by opening a separate viewer.  I'm not familiar with such a plugin, though there is a Firefox extension (perhaps more than one) that does that.

Anyhow, consider providing the information about your situation that will make it possible for people to help you.  You say that a common problem should have a common answer.  Perhaps the understanding about the different computers and video files will help you to understand why a common answer is not really possible.

---

### Post by Spektyr on 2007-12-15
I've got Firefox 2.0.0.9 on one machine and 2.0.0.11 on the other.

I meant "extension" when I said "plugin", refering to the thing that is supposed to let me open the video in another player.  I think it's called MediaPlayer Connectivity or something.

I know for certain that I have a lot of trouble with Flash movies - that's the one that probably causes the most trouble.  I've got the latest Shockwave installed, but I either get no video and audio, a still picture that never does anything (and no audio), or a little bit of the beginning video and audio that then stops.

Here's a site that I can't watch the video from:
[http://www.cnn.com/video/#/video/health/2007/12/14/stout.skorea.glowing.cats.ytn](http://www.cnn.com/video/#/video/health/2007/12/14/stout.skorea.glowing.cats.ytn)

It's .swf type.


Basically I'd like to not have to hunt down the XP laptop or close what I'm doing and reboot my desktop in XP just because there's a video in the page I need to see.  Another type of site I know I have trouble with is pretty much any major automotive manufacturer's site.  Saturn and Honda I know for sure - they've got what I think is a flash center picture "thing" that makes the drop down menus at the top useless, because they default behind that picture rather than in front of it - so I can't use the menus at all.

My ultimate goal is to be able to do whatever I want in Ubuntu Firefox and not have to simply "miss out" because I didn't boot in Microsloth.

---

### Post by eapache on 2007-12-15
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by randcoop on 2007-12-16
The previous post explains how to install the flash program.  But you say that it's already installed.  To verify, enter about:plugins as a URL in Firefox.  On the page that opens, look for Shockwave Flash.  If it's there then the plugin is installed.  If not, then it's not.

MediaPlayerConnectivity is great for Windows Media files, Real Player files, and even Quicktime files.  But it doesn't deal well with Flash.  If you've got MediaPlayerConnectivity configured to deal with Flash files, it might be hurting your ability to run Flash.  In MediaPlayerConnectivity's Configure window, uncheck the Flash box, so that it no longer tries to run it.  Then revisit the site and see if it works.

I just looked at the site you identified; it ran without incident. But I have MediaPlayerConnectivity disabled for Flash and  I'm using a newer version of Flash than you get with the Ubuntu repositories (the latest version is 9.0 r115).   If you aren't using that version, you might want to install it, but installing it is not just a simple matter of a one line command.  Instead, you need to download a zipped file, unzip it, and then run the Flash installer (which is a one line command).  If you have Flash, but want to upgrade, we can give you a step by step process for doing that.

---

### Post by Spektyr on 2007-12-16
Yeah, I've got Flash.  The upgrade seems like a good idea, go ahead with the instructions.

Thanks!

---

### Post by eapache on 2007-12-16
First, download this file from Adobe:

[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz")

Right-click and select "Extract here".

Open a terminal (Applications > Accessories > Terminal) and type```
cd Desktop/install_flash_player_9_linux
sudo ./flashplayer-installer
```Follow the provided instructions.

---

### Post by dondad on 2007-12-16
> **Spektyr said:**
> Okay, yes, there's a bunch of these threads.

Too many.  There's dozens, they all have different solutions, and I'm dizzy from trying to figure out what's going on, what to try next, and everything else.

I just want to be able to watch streaming video on the web.  This should not be complicated and it should not require intimate knowledge of codecs and whatnot.


Is there a checklist somewhere?  A definitive How-To?

All I've found are threads like this one, where someone says "Hey, video doesn't work for me in Firefox" and then a few people come along, offer a few different suggestions, and the thread fades into obscurity with no indication of which - if any- of the answers worked.  It's such a common problem there should be a common answer.

I've installed every codec I could find in Automatix.  I've installed the plugin for Firefox that's supposed to let you open video in a separate viewer.  I've done a few other things that I don't remember.

I'm confused, I'm concerned that trying "everything" will just break things worse than they already are, and I'm tired.

BTW, this is for Gutsy... I haven't updated my profile because absolutely nothing got better when I "upgraded" and several things got worse.


Any help?

Are you running the 64 bit version of Gutsy? I understand that there are flash problems with that.

---

### Post by chadridesabike on 2007-12-17
synaptics package manager.  java-package.  should take care of it.

---

### Post by sirdilznik on 2007-12-17
If you're talking flash and java stuff then the fixes already suggested should work.  If you want to see different video formats (.avi, .mov, .wmv) there is the mplayerplugin for firefox.  Also there is my personal favorite, the Media Player Connectivity extension.  It allows you play different media types from any available standalone player.  In my case I use mplayer for videos.  This way I don't have to watch it embedded in the page in a small window, I can watch it full screen or whatever size I want.

---

### Post by Spektyr on 2007-12-17
I've installed the flash player update and I tried the java-package.  Still getting the same problem with flash.

This is on the 32-bit Gutsy, btw.


One possible problem is that I'm not sure where to install the flash player update (it asks for the path to the browser, but I'm not sure exactly where to send it - I just gave it /usr/lib/firefox and it seemed to think that was okay.)  In windows I'd just right click on the shortcut and tell it to show me to the target.  I have no idea how to do that in Linux.

---

### Post by randcoop on 2007-12-17
Install Flash to ~/.mozilla/plugins/ (the ~ is your home directory).

This plugin directory overrides any other plugin directories under Mozilla (Firefox).

---

### Post by Spektyr on 2007-12-17
> **randcoop said:**
> Install Flash to ~/.mozilla/plugins/ (the ~ is your home directory).

This plugin directory overrides any other plugin directories under Mozilla (Firefox).

I have this directory, it has a file called "flashplayer.xpt" in it, but the installer will not accept this as a valid directory.  I entered "/home/username/.mozilla/plugins/" and "/home/username/.mozilla/plugins" to no avail.

---

### Post by eapache on 2007-12-17
If you've already installed it into /usr/lib/firefox, don't bother installing it again. Go to /usr/lib/firefox/plugins and copy the file 'libflashplayer.so' to your ~/.mozilla/plugins

---

### Post by Spektyr on 2007-12-17
I think Ubuntu hates me...

I'm still not getting flash videos to work.

---

### Post by randcoop on 2007-12-18
I'm beginning to think you may be right about Ubuntu.  Still, let's not give up.  What does about:plugins say?  Is Flash there?  The version you installed?  With the .so file named?

---

### Post by Spektyr on 2007-12-19
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r115

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

---

### Post by randcoop on 2007-12-19
At this point, I think we may be looking at the wrong problem. Flash pages often use javascript.  I think it's possible that you haven't got javascript properly implemented.  

Do you know if you have javascript?  Have you tested to see if it works?

---

### Post by Spektyr on 2007-12-20
I've got Java listed (huge list) on the about: plugins page.  As far as I know it works, but maybe some little corner of it is broken.  I also see a "Default Plugin" that is not enabled, but I'm not sure if it's even supposed to be.  This is what it says:

Default Plugin

    File name: libnullplugin.so
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

MIME Type 	Description 	Suffixes 	Enabled
* 	All types 	.* 	No

---

### Post by eapache on 2007-12-20
Are you using a dev release of Firefox 3? 'cause the default plugin shouldn't be there if you're using 2.

---

### Post by Spektyr on 2007-12-20
Nope, this is on 2.0.0.11

---

### Post by randcoop on 2007-12-21
Test javascript here: [http://www.bom.gov.au/weather/radar/about/clickme.shtml]("http://www.bom.gov.au/weather/radar/about/clickme.shtml")

---

### Post by Spitphire on 2007-12-22
you don't really need to read about glowing cats anyway.. its your computers way of telling you no.

;-)

Sorry, watched the video too funny

---

### Post by Tosa on 2007-12-22
Yeah, you're right 'bout those cats...

Now, a bit more serious: I've seen that page, and I've got  Shockwave Flash 9.0 r48, so it obviously works.

But I don't have any java plugin listed in Firefox (2.0.0.11) !? It seems that Flash doesn't need it after all?

---

### Post by Spektyr on 2007-12-22
The Java test passed.

---

### Post by randcoop on 2007-12-26
I'm responding one last time for two reasons.  First, to tell you that I'm sorry that nothing helped.  Flash works perfectly on most Ubuntu/Kubuntu installs, but something has happened that makes it fail on yours.

Second, but putting another response, it bumps your thread to the top of the forum list again.  Perhaps someone will read the thread and be able to help.

---

