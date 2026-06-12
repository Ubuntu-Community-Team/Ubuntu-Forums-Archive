---
title: "Does this video play in your PC?"
date: 2006-11-23
forum: General Help
---

### Post by Dual Cortex on 2006-11-23
[http://www.wftv.com/video/10380340/detail.html](http://www.wftv.com/video/10380340/detail.html)

I have the mozilla-mplayer plug-in as well as the non-free w32codecs installed.
Using FF2 (edgy)

So, does this work to you guys or am I the only one having the problem?
Am I missing any other plug-ins, libs, etc.?

---

### Post by groggyboy on 2006-11-23
nada here too.

---

### Post by gjtoth on 2006-11-23
Nope... just loops a load sequence

---

### Post by Dual Cortex on 2006-11-23
What are you guys using to play the video?
I mean, mplayer doesn't even load up. Just a gray rectangle on my screen.

---

### Post by TigerWolf on 2006-11-23
It works somewhat better in IE in wine. I HATE people that have things that only work in IE.

---

### Post by Dual Cortex on 2006-11-23
Yeah, video plays fine in my Windows PC.

---

### Post by d3v1ant_0n3 on 2006-11-23
i get an intriguing purple rectangle in the player window, then an error from totem that I couldn't copy/paste (it couldn't negotiate the .swf, apparently).

---

### Post by Dual Cortex on 2006-11-23
I believe its a wmv video, but I'm sure it's not flash.

---

### Post by voodoonirvana on 2006-11-23
Nope, just a black screen.

---

### Post by TigerWolf on 2006-11-23
I dont think your going to get it to work. Email the website and request that they support firefox/linux etc.

Try running this in totem - mms://wms.ibsys.com:80//2006/1122/10382757.56k.wmv

View source - search for wmv and find the required video.

---

### Post by bigken on 2006-11-23
worked for me (kubuntu edgy)

---

### Post by TigerWolf on 2006-11-23
How? What browser? Flash 7 or 9?

---

### Post by bollix47 on 2006-11-23
Worked here in mplayer using Firefox 2.0.

---

### Post by bigken on 2006-11-23
mplayer plugin firefox 2.0

---

### Post by Dual Cortex on 2006-11-23
Seriously? I can't get it working on FF2 with mozilla-mplayer 3.31-1

---

### Post by TigerWolf on 2006-11-23
So then whats the solution to get it to work for Dual Cortex? I assume he is running mplayer and firefox 2.0

---

### Post by bollix47 on 2006-11-23
If you have Totem installed (and I think it's installed by default) then the two plugins could be conflicting in Firefox.

Anytime I get an update that involves Totem I remove it's plugins from Firefox.

Close Firefox.

sudo rm /usr/lib/firefox/plugins/libtotem*

You could try that to see if it solves your problem.

---

### Post by Dual Cortex on 2006-11-23
Thanks bollix, that was it. I guess I should have mentioned I had just installed mplayer, how would I get totem back though?

---

### Post by Grog140 on 2006-11-23
Its working for me using mplayer plugin.

---

### Post by NeoChaosX on 2006-11-23
No, it doesn't. From my experience, Windows Media content and mozilla-mplayer plugin has been very flaky in Edgy on my system - it will repeatedly connect to the media, attempt to play for a split second before trying to reconnect again then stop after a few tries.

---

### Post by claydoh on 2006-11-23
it didn't load for me at first, but then i right-clicked on the video  window, chose "configure" and tried different video outputs. xv seemed to work best, tho sometimes playback was flaky on different tries. You can also adjust min cache size and other adjustments from there. this is in Kubuntu Edgy & Firefox 2, tho I doubt that has any real bearing :)

In Konqueror using kmpalyer, the video played back automagically. As both browsers are using different mplayer plugins, it is probably just the initial settings in mozilla-mplayer that prevent the video to be played back correctly, at least in my case

---

### Post by mexlinux on 2006-11-23
It works perfect in konqueror! (kubuntu edgy)

---

### Post by bollix47 on 2006-11-24
> **Dual Cortex said:**
> Thanks bollix, that was it. I guess I should have mentioned I had just installed mplayer, how would I get totem back though?

You're welcome.  Glad it worked for you.

You still have totem on your setup.  The procedure I gave you just removed the links to the plugin for Firefox.  If you want them back just reinstall the plugin using synaptic.

---

### Post by ShadowVlican on 2006-11-24
haven't read much of this thread other than the OP's

but this video plays back fine on firefox in windows

it's a WMV stream...

---

### Post by junkalam on 2006-11-26
Working perfectly here on firefox....

I have the following installed:
w32codecs
Xine-ui
mplayer
mozilla-mplayer

I also removed totem, totem-gstremer, totem-mozilla

---

### Post by tomcheng76 on 2006-11-26
mplayerplug-in fails
even ies4linux failed, it shows a yellow javascript error icon on the buttom left corner

---

### Post by chetroia on 2006-11-27
No luck on my Edgy. I cant seem to get windows media stuff to play at all. CNN never works for me. I have spent so much time with mplayer plugin trying to get work on Fed 5 too. More testing needs to be done to get this to work

---

### Post by Cynical on 2006-11-27
Strange, works for me. I'm using the mplayer firefox plugin with opengl output.

---

