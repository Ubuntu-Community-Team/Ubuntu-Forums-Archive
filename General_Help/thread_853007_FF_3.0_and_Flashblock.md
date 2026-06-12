---
title: "FF 3.0 and Flashblock"
date: 2008-07-08
forum: General Help
---

### Post by peakshysteria on 2008-07-08
In the past I found Flashblock to be one of the most reliable, stable and most useful. But even though it should be compatible with the latest version of FF it's not. I'm running Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9) Gecko/2008061017 Firefox/3.0 and Flasblock 1.5.6 crashes rapidly once I visit any newspaper site (they have tons of flash).

From [https://addons.mozilla.org/en-US/firefox/addon/433](https://addons.mozilla.org/en-US/firefox/addon/433) I'm told:
> *************************************
All RECENT crashes on Ubuntu have been traced to one of two problems (this may apply to gentoo and other debian based distros).

1. You are using the Firefox version from the Ubuntu repositories.

Install the official tarball from mozilla.com Most people on Unbuntu report that the official release from mozilla doesn't crash in the same circumstances that Ubuntu Firefox crashes. Also the official tarball is reported to be much more stable.

2. You are using Flashplayer 10 beta on Ubuntu.

Users have reported that Flashplayer 9.0 r124 don't crash for those specific pages. Unfortunately Flashplayer 9.0 r124 crashes with RealPlayer streams and 10 Beta doesn't crash in this case. So I guess it's one crash or the other.
*************************************

Why is the tarball different than the FF I've installed? Can someone verify that this works? And if I install it will this mess with my updates?

I really do miss flashblock since it was my main addon beside Tabmix plus.

---

### Post by pedro_orange on 2008-07-08
Since it's open source, Ubuntu devs can tweak FF for Ubuntu, hence why its in our repos and thats why it is possibly different.

You don't have to update FF or install it from the repo. Install whichever version you like. 
I'm not sure if it will effect your updates, but you can just choose not to update it!

---

### Post by peakshysteria on 2008-07-09
Flashblock is an essential addon. It should be enabled by default (if they could make it more stable that is). On windows I've never had any problems with it. But now it's not possible to use it at all. Not sure why. It might have something to do with java as well as flash on x64 (which still is poorly supported). Let's hope they push out an update soon.

__________________

Got an update for FF today (july 29). Giving Flashblock another go. Actually FF seems faster with Flashblock enabled. Maybe since the large flash boxes are reduced to a neat, small flasblock/play button. I love this addon. To bad it's so unstabel at the moment. I also gave a go on my brotheres brand spanking new iMac/OSX Leopard. But no luck there. News sites loaded with flash seemed to crash FF.

After running FF with Flashblock enabled for a coupla days it seems stable enough. Crashes are less frequent than before. FF crashes if we load several pages (with a lot of flash content) at once rapidly. Also if a lot of links are opened at once while closing other tabs we can experience crashes. Our problem pages seemed to be (in random orther):

[http://www.last.fm](http://www.last.fm)
[http://www.dagbladet.no/](http://www.dagbladet.no/)
[http://www.vg.no/](http://www.vg.no/)
[http://adressa.no/](http://adressa.no/)

Overall Flashblock actually seem to increase loading speed of pages. 

My Firefox Information

Last updated: Thu, 31 Jul 2008 13:19:05 GMT
User Agent: Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1

**Extensions** (enabled: 16, disabled: 0; total: 16)
[list]
[*][DownloadHelper](http://www.downloadhelper.net) 3.2 
[*][FireFTP](http://fireftp.mozdev.org) 1.0 
[*][Flashblock](http://flashblock.mozdev.org/) 1.5.6 
[*][Forecastfox](http://forecastfox.mozdev.org/) 0.9.7.7 
[*][Greasemonkey](http://www.greasespot.net/) 0.8.20080609.0 
[*][InfoLister](http://mozilla.doslash.org/infolister) 0.10 
[*][last.fmCode](http://mll2.free.fr/?p=42) 0.7a 
[*][Linkification](http://yellow5.us/firefox/linkification/) 1.3.5 
[*][Nightly Tester Tools](http://www.oxymoronical.com/web/firefox/nightly) 2.0.2 
[*][Norsk Bokmål ordliste]() 2.0.10.0 
[*][Norsk Nynorsk ordliste]() 2.0.10.0 
[*][Tab Mix Plus](http://tmp.garyr.net) 0.3.6.1.080416 
[*][Text Link](http://piro.sakura.ne.jp/xul/_textlink.html.en) 2.0.2008052801 
[*][Tiny Menu](http://trac.arantius.com/wiki/Extensions/TinyMenu) 1.4.9 
[*][Ubuntu Firefox Modifications]() 0.5 
[*][Update Channel Selector](http://www.oxymoronical.com/web/firefox/updatechannel) 1.0.3 
[/list]

**Themes** (2)
[list]
[*]Default [selected]
[*]PitchDark 
[/list]

**Plugins**
[list]
[*]Default Plugin
[*]Demo Print Plugin for unix/linux
[*]DivX® Web Player
[*]GCJ Web Browser Plugin (using IcedTea) 1.0
[*]Helix DNA Plugin: RealPlayer G2 Plug-In Compatible (compatible; Totem)
[*]iTunes Application Detector
[*]QuickTime Plug-in 7.2.0
[*]Shockwave Flash
[*]Totem Web Browser Plugin 2.22.1
[*]VLC Multimedia Plugin (compatible Totem 2.22.1)
[*]Windows Media Player Plug-in 10 (compatible; Totem)
[/list]

---

### Post by peakshysteria on 2008-09-25
Had to disable Flashblock. Just now today I've got an update to Firefox. Also FF 3.0.2 (Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.2) Gecko/2008092213 Ubuntu/8.04 (hardy) Firefox/3.0.2) seems to crash with Flashblock enabled.

Edit:

New update got me:
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.3) Gecko/2008092510 Ubuntu/8.04 (hardy) Firefox/3.0.3
No status change on Flasblock. Still crashing.

---

### Post by peakshysteria on 2008-10-14
Reinstalled Ubuntu last night. Changed from 64 bit to 32 bit (since my better half the bank manager couldn't go to our bank because of the damn java applets not loading). As it turns out a lot of things are smoother. And flashblock is behaving like in the old days. Working smoother than ever:

Last updated: Tue, 14 Oct 2008 09:32:33 GMT
User Agent: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.3) Gecko/2008092510 Ubuntu/8.04 (hardy) Firefox/3.0.3

**Extensions** (enabled: 15, disabled: 0; total: 15)
[list]
[*][Dictionary Switcher](http://en.design-noir.de/mozilla/dictionary-switcher/) 1.0 
[*][Dictionary Tooltip](http://www.rjonna.com/ext/dictionarytip.php) 1.3 
[*][DownloadHelper](http://www.downloadhelper.net) 3.3 
[*][Flashblock](http://flashblock.mozdev.org/) 1.5.6 
[*][Forecastfox](http://forecastfox.mozdev.org/) 0.9.7.7 
[*][Greasemonkey](http://www.greasespot.net/) 0.8.20080609.0 
[*][InfoLister](http://mozilla.doslash.org/infolister) 0.10 
[*][last.fmCode](http://mll2.free.fr/?p=42) 0.7a 
[*][Linkification](http://yellow5.us/firefox/linkification/) 1.3.5 
[*][Nightly Tester Tools](http://www.oxymoronical.com/web/firefox/nightly) 2.0.2 
[*][Tab Mix Plus](http://tmp.garyr.net) 0.3.7.2 
[*][Text Link](http://piro.sakura.ne.jp/xul/_textlink.html.en) 2.0.2008052801 
[*][Tiny Menu](http://trac.arantius.com/wiki/Extensions/TinyMenu) 1.4.9 
[*][Ubuntu Firefox Modifications]() 0.5 
[*][Update Channel Selector](http://www.oxymoronical.com/web/firefox/updatechannel) 1.0.3 
[/list]

**Themes** (1)
[list]
[*]Default [selected]
[/list]

**Plugins**
[list]
[*]Default Plugin
[*]Demo Print Plugin for unix/linux
[*]DivX® Web Player
[*]Helix DNA Plugin: RealPlayer G2 Plug-In Compatible (compatible; Totem)
[*]iTunes Application Detector
[*]Java(TM) Plug-in 1.6.0_07-b06
[*]QuickTime Plug-in 7.2.0
[*]Shockwave Flash
[*]Totem Web Browser Plugin 2.22.1
[*]VLC Multimedia Plugin (compatible Totem 2.22.1)
[*]Windows Media Player Plug-in 10 (compatible; Totem)
[/list]

---

### Post by peakshysteria on 2008-11-13
Two days ago I updated my Flash to Shockwave Flash 10.0 r12 since I lost my sound in 9.0. After rebooting I had lost my sound once again. Didn't havetime to look for a fix. Just this morning I got an update for Flashblock. Sound is working once again. At first look all seems smooth again.

Edit:

Sound has vanished once again. Not sure why. For some strange reason it seems like flash works after a reboot of the machine. But once I have played a flash clip (with working sound) the next clip will only show image and no sound.

---

