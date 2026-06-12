---
title: "pepper flash in chromium freezes when I change resolution setting in youtube"
date: 2014-02-16
forum: General Help
---

### Post by finny388 on 2014-02-16
I recently installed pepper flash for chromium:
```
sudo add-apt-repository ppa:skunk/pepper-flash
sudo apt-get update
sudo apt-get install pepflashplugin-installer

```
Then add this last line to /etc/chromium-browser/default
> # Default settings for chromium-browser. This file is sourced by /bin/sh from
# /usr/bin/chromium-browser

# Options to pass to chromium-browser
CHROMIUM_FLAGS=""
. /usr/lib/pepflashplugin-installer/pepflashplayer.sh

Intermittently youtube videos:
a) load properly as usual
or b) load and play but if resolution setting is changed, video pauses and goes black, play button doesn't respond.
  also I can tell when this will happen by going full screen: the navigation bar is not scaled properly. it is a blown up version of the small screen version (as if you took a screenshot of the small video version in youtube and zoomed it to fullscreen

I do have html5 enabled so maybe the intermittence is just that a) is html5 and b) is flash videos

Anyone know how this can be fixed? and as an aside, how do you know what format a youtube video is?

---

### Post by finny388 on 2014-02-18
I've been trying to search for a solution to this and I wanted to start with knowing whether html5 or flash were involved.

It turns out to be a diffucult question to coin in search terms. "how to know if a youtube video is playing with flash or html5 player"
most results are on how to upload or a rundown of what formats youtube offers.

[this discussion]("https://productforums.google.com/forum/#!topic/youtube/09SUZOge91s")

is the closest I came to

Can anyone offer any help on this issue?

---

### Post by OrangeCrate on 2014-02-18
> **finny388 said:**
> I've been trying to search for a solution to this and I wanted to start with knowing whether html5 or flash were involved.

It turns out to be a diffucult question to coin in search terms. "how to know if a youtube video is playing with flash or html5 player"
most results are on how to upload or a rundown of what formats youtube offers.

[this discussion]("https://productforums.google.com/forum/#!topic/youtube/09SUZOge91s")

is the closest I came to

Can anyone offer any help on this issue?

I can only offer a bit of back door advice, I don't have a plug and play solution for you. I use Chrome to gain access to Pepperflash. When I check "about : plugins", there are two instances of flash, pepper, and the Linux version that is installed with the restricted packages. I once read, moons ago, a recommendation to disable the Linux version (currently 11.2 something), and use just pepper, because of random freezes possibly caused by having both enabled at the same time. I can't seem to find the article that I read back then, that offered the solution, but hopefully, there is something in my response that will head you off in the right direction to solve your problem.

Edit:

Had to change "about : plugins" to read like this. If you type it normally, it ends up looking like this:

about:plugins

LOL

---

### Post by finny388 on 2014-02-18
Thanks OrangeCrate

In chromium
I saw in chrome : plugins after clicking on Details that there are two enabled versions.
I disabled 11.2 and tested a youtube video, same problems.

I copied that url, opened chrome, pasted it in and it worked fine.
chrome has the same two flash files and both are enabled
But then I opened another video and the problem returned

So then I tried disabling v12. These results are also hit and miss but the navigation bar scales properly (but the video still freezes to black when res is changed)

So at least two things are clear: it is not dependent on the source video and it happens in chrome or chromium

---

### Post by finny388 on 2014-02-18
Here is my plugin page flash contents. is it identical to yours? is the same file in the same location? (under Location: )
> Adobe Flash Player (2 files) - Version: 12.0.0.44
Shockwave Flash 12.0 r0
Name:	Shockwave Flash
Description:	Shockwave Flash 12.0 r0
Version:	12.0.0.44
[COLOR="#FF0000"]Location:	/usr/lib/pepflashplugin-installer/libpepflashplayer.so[/COLOR]
Type:	PPAPI (out-of-process)
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/x-shockwave-flash	Shockwave Flash	
.swf
application/futuresplash	FutureSplash Player	
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


---

### Post by monkeybrain20122 on 2014-02-19
Well do you experience freezing with flash 11.2 and Firefox? Do you have hardware acceleration forcibly enabled in Chromium(check about:gpu)?

---

### Post by OrangeCrate on 2014-02-19
> **finny388 said:**
> Here is my plugin page flash contents. is it identical to yours? is the same file in the same location? (under Location: )

It's the same. I'm not having a problem watching videos on YouTube, with the setup I described. All the features are working correctly. Currently this computer has Ubuntu 13.10, but, it has had Xubuntu 13.10 on it in the recent past, and I don't remember there being a problem with that install either. I have not attempted to install pepper flash on Chromium. If I were experiencing the same problems as you are, I'd probably just go with a standard Chrome or Chromium install, and forget about trying to add pepper flash to Chromium. As said earlier, I'm sorry I don't have a ready solution for you.

---

### Post by finny388 on 2014-03-01
I tried creating
> /etc/adobe/mms.cfg and put this in it:

EnableLinuxHWVideoDecode=1but that didn't change anything

chrome://gpu shows:> Graphics Feature Status
Canvas: Software only, hardware acceleration unavailable
3D CSS: Hardware accelerated
Compositing: Hardware accelerated
CSS Animation: Accelerated
Flash 3D: [COLOR="#FF0000"]Unavailable. Hardware acceleration unavailable[/COLOR]
Flash Stage3D: [COLOR="#FF0000"]Unavailable. Hardware acceleration unavailable[/COLOR]
Flash Stage3D Baseline profile: [COLOR="#FF0000"]Unavailable. Hardware acceleration unavailable[/COLOR]
WebGL multisampling: Hardware accelerated
Texture Sharing: Hardware accelerated
Video: Software only, hardware acceleration unavailable
Video Decode: Software only, hardware acceleration unavailable
WebGL: Hardware accelerated

Yes, this was working before. Not sure exactly what flash version it was. How do I try different versions? Go into synaptic and install/uninstall from there?

---

### Post by finny388 on 2014-03-01
I remembered I had 11.2 installed before

with 11.2 enabled the navigation bars scale properly
with v 12 enabled the navigation bars don't
but in either case the screen goes black and stops playing when resolution is changed.

So I'm stuck watching youtube in 360p. It is depressing

---

### Post by monkeybrain20122 on 2014-03-01
It has to do with your graphic driver.
Try this:
Go to about://flags and enable "override software rendering list" (the first item) then restart the browser.
You can try different versions of flash in about:plugins, click show details and scroll down to adobe flash player, it will show two versions of flash (11.2 and pepper), disable pepper flash.

P.S. I think the mms.cfg thing only works on system flash (11.2) and when it works it apparently only works on Youtube. I don't know about Chromium but in Chrome pepper flash is accelerated and it is controlled by browser settings (not sure if flash acceleration is Youtube only, haven't checked, I mostly use FF)

---

### Post by finny388 on 2014-03-01
Thanks
I enabled "override soft.." and restarted (type chrome://restart by the way)
Went into plugins and things flash was hw accelerated

eagerly I went to youtube and launched a video. I went to full screen and the nav bar scaled properly. nice.
So I go to increase the resolution and same deal. It goes black. I can hover over the progress bar and see the frames of the video. I can press pause and play and the button will respond but the video stays black and silent.
I cannot adjust the position of the progress bar. I will drag the circle, let go and it reverts back to the position where it froze.

but I went into chrome and tried this and it works. I didn't know that flag needed enabling.
I guess I'll just use chrome. weird

---

### Post by monkeybrain20122 on 2014-03-01
Glad you have your problem solved. Well Chromium is neither here nor there IMO, it is perpetual alpha, not up to date and lack features. I would either go with Firefox or Chrome. I never understand the mindset of installing Chromium because it is open source and then jumping through the hoop to get the proprietary features of Chrome while it is much easier to just install Chrome. On the other hand Firefox is the flagship open source browser and 100 times more feature completed than Chromium.

---

