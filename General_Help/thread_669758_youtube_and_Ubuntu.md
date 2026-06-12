---
title: "youtube and Ubuntu"
date: 2008-01-16
forum: General Help
---

### Post by wookietim on 2008-01-16
This is an annoyance, not a fatal flaw, but Youtube is unusable under Ubuntu... I say not fatal because, unlike many other people, I am not completely addicted to that particular site but I do like browsing every now and then.

What happens is that I will click on a video, the applet will show, the video will load and then  Firefox ceases to respond to any click - and the mouse pointer becomes unresponsive if I continue to let the video load.... and this happens every time i try to play a video on the site...

Is there a simple fix for this? I don't understand the intricacies of Linux yet, so a step by step guide for idiots would be my speed...

---

### Post by buntunub on 2008-01-16
Works flawless for me. Unable to reproduce your issue.

---

### Post by wookietim on 2008-01-16
Literally, every single video i try does this.... Firefox is the only app running at the time. I don't even have a second tab open.

---

### Post by Meow27 on 2008-01-16
something similar happends to me on veoh

just dont press refresh or dont do any form of refreshing for a swf video on firefox

---

### Post by wookietim on 2008-01-16
Mine happens even if I don't do a refresh - it happens as soon as the video tries to start playing.

---

### Post by sumguy231 on 2008-01-16
What version of the Flash Plugin are you using? Use [about:plugins]("about:plugins") in Firefox to find out the exact version.

---

### Post by ubuntu-freak on 2008-01-16
Are you using Gnash or Adobe flash? The Adobe one is broken at the mo. Check out my how-to
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
Only install my flash if you have Gnash and not Adobe. Make sure you remove Gnash first.

Nathan

---

### Post by LeDechaine on 2008-01-17
Hmm, gnash is not really (really not) helpful for me. I installed Gnash, but in youtube the only things i saw were grey squares where videos were supposed to be. Worse: *everytime* i closed the page, firefox freezed.
Gnash is still **alpha**. This is the proof. :P

*goes installing flashplugin-nonfree via synaptic*

---

### Post by wookietim on 2008-01-17
My About:Plugins returns this :

Installed plug-ins
Find more information about browser plug-ins at mozilla.org.
Help for installing plug-ins is available from plugindoc.mozdev.org.
Shockwave Flash

    File name: libgnashplugin.so
    Shockwave Flash 8.0 r99. Gnash 0.8.1, the GNU Flash Player. Copyright © 2006 Free Software Foundation, Inc.
    Gnash comes with NO WARRANTY, to the extent permitted by law. You may redistribute copies of Gnash under the terms of the GNU General Public License. For more information about Gnash, see [http://www.gnu.org/software/gnash](http://www.gnu.org/software/gnash). Compatible Shockwave Flash 8.0 r99.

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
Totem Web Browser Plugin 2.20.0

    File name: libtotem-basic-plugin.so
    The Totem 2.20.0 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/ogg 	Ogg multimedia 	ogg 	Yes
audio/ogg 	Ogg Audio 	ogg 	Yes
audio/x-ogg 	Ogg Audio 	ogg 	Yes
video/ogg 	Ogg Video 	ogg 	Yes
video/x-ogg 	Ogg Video 	ogg 	Yes
video/mpeg 	MPEG video 	mpg, mpeg, mpe 	Yes
audio/wav 	WAV audio 	wav 	Yes
audio/x-wav 	WAV audio 	wav 	Yes
audio/mpeg 	MP3 audio 	mp3 	Yes
application/x-nsv-vp3-mp3 	NSV video 	nsv 	Yes
video/flv 	Flash video 	flv 	Yes
Windows Media Player Plug-in 10 (compatible; Totem)

    File name: libtotem-gmp-plugin.so
    The Totem 2.20.0 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-mplayer2 	AVI video 	avi, wma, wmv 	Yes
video/x-ms-asf-plugin 	ASF video 	asf, wmv 	Yes
video/x-msvideo 	AVI video 	asf, wmv 	Yes
video/x-ms-asf 	ASF video 	asf 	Yes
video/x-ms-wmv 	WMV video 	wmv 	Yes
video/x-wmv 	WMV video 	wmv 	Yes
video/x-ms-wvx 	Playlist 	wmv 	Yes
video/x-ms-wm 	ASF video 	wmv 	Yes
application/x-ms-wms 	WMV video 	wms 	Yes
application/asx 	Playlist 	asx 	Yes
DivX® Web Player

    File name: libtotem-mully-plugin.so
    The Totem 2.20.0 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	AVI video 	divx 	Yes
QuickTime Plug-in 7.2.0

    File name: libtotem-narrowspace-plugin.so
    The Totem 2.20.0 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QT video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	Macintosh Quickdraw/PICT drawing 	pict, pict1, pict2 	Yes
video/x-m4v 	MPEG-4 video 	m4v 	Yes

---

### Post by Sef on 2008-01-17
> File name: libgnashplugin.so
Shockwave Flash 8.0 r99. Gnash 0.8.1, the GNU Flash Player. Copyright © 2006 Free Software Foundation, Inc.
Gnash comes with NO WARRANTY, to the extent permitted by law. You may redistribute copies of Gnash under the terms of the GNU General Public License. For more information about Gnash, see [http://www.gnu.org/software/gnash](http://www.gnu.org/software/gnash). Compatible Shockwave Flash 8.0 r99.


I would remove Gnash, and see it that does the trick.  Applications > Add/Remove > search : Gnash > unclick check next to Gnash > apply changes > apply > close.

---

### Post by c0met on 2008-01-17
if your computer has a 64 bit processor, this is how I got Flashplayer 9 to work.
[LIST]
[*]Using Synaptic Package Manager (System >> Administration), I checked to see that nspluginwrapper was installed.
[*]I downloaded the tar.gz file for flashplayer 9 from
[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz")
[*]I extracted the tar.gz file to my desktop. This put a directory in my desktop called “install_flash_player_9_linux”.
[*]I opened terminal and navigated to the above flashplayer directory and copied the libflashplayer.so file to my /usr/lib/firefox/plugins directory using
sudo cp ./libflashplayer.so /usr/lib/firefox/plugins/libflashplayer.so
[*]Then I used the command,
[*]sudo nspluginwrapper -i /usr/lib/firefox/plugins/libflashplayer.so
[/LIST]
Flashplayer 9 was then installed and worked fine. I am told that a patch is needed, though, and I am yet to install that. Information about it is at
[http://ubuntuforums.org/showthread.php?t=476924]("http://ubuntuforums.org/showthread.php?t=476924")

**[COLOR="Red"]_NOTE_[/COLOR]**
Since your about/plugins shows that Flash is already installed, you might simply try copying the libflashplayer.so file that was extracted from the tar.gz to your plugins directory (/usr/lib/firefox/plugins or /usr/lib/mozilla/plugins)

---

### Post by timboellis on 2008-01-17
If it is of any help I am a noob but I have the exact same issue however one wayi found it worked perfectly was to install flash manually by downloading and dumping the files into firfox

---

### Post by wookietim on 2008-01-17
I just tried it - no luck...

---

### Post by timboellis on 2008-01-17
Forgot to add something I know its not what you want to hear just to see if it worked but it did nor me.

Was I struggled getting lots of things working graphics apps etc.even youtube trying to install then trying to do it manually but once i had a rough jist of it I done a fresh install did not to the auto install but manualy installed it even before opening up firefox and it worked.


OHH.. one other suggestion have you tried Firefox 3 yes it is beta but works perfectly for me and you tube works as well this may be an option to try before you loose the plot i know i have lots of times.

I done it from here [http://www.ubuntugeek.com/howto-install-firefox-3-beta-2-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/howto-install-firefox-3-beta-2-in-ubuntu-710-gutsy-gibbon.html)

let us know how you get on

---

### Post by wookietim on 2008-01-17
OMG!! I have no idea what I just did, but all of a sudden, youtube is working great...

I went to the "Add/Remove programs and checked the box to uninstall the flash plugin, then installed the same plugin along with the "Ubuntu restricted" stuff - I got two dialogs that said it failed, then went to youtube and now it works great.

I am scared. I feel like I shouldn't touch the computer too much (Sort of like that scene in "Spinal Tap" with the guitar collection - "Don't touch it. Don't point at it. Don't even look at it!")

---

### Post by timboellis on 2008-01-17
Cool at least it works a bit of a bugger that you do not know why though for you next install just turn the volume up to 11 now

---

