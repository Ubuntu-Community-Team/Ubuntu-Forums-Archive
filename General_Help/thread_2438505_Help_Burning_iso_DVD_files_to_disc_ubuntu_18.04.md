---
title: "Help Burning iso DVD files to disc ubuntu 18.04"
date: 2020-03-13
forum: General Help
---

### Post by Marcus Aurelius on 2020-03-13
Hello,

I am familiar with the rip and burn process.  I have kids always scratching my new DVD's.  So I rip them to .iso files on my HD using the dd if=/dev/sr0 of=/ method from ubuntu terminal.  I have no problem doing this.  But when I try to burn them to a 8.5gb DVD+R DL disc, it seems to burn fine.  But when I try and play the disc back with VLC, all I see is a black screen with the VLC Cone, and I hear the audio which is choppy and no video is shown at all.  I have tried this disc on different computers, different drives, including my DVD player for my tv and the result is the same.  So I took one of these discs that don't play and decided for the hell of it, I'd rip the bad DVD back to .iso using the above method.  When I do this, the iso I ripped from the "bad" DVD, plays 100% perfect in iso format.  Thus I assume nothing is wrong with the DVD...but yet I can't play it anywhere correctly, I can only rip it.  I've also tried burning the iso's in both ubuntu and windows 10 with the same result. I also tried to play with kodi (black screen no sound); also mpv player which has sound and video out of sync but blotchy and pixelated. SMPlayer is a grey screen and does nothing. And Bomi is the same result as MPV.

Any help is greatly appreciated. 

Thank you

---

### Post by TheFu on 2020-03-14
Welcome to DRM.  Some DVDs place DRM stuff outside the normal, expected, approved, DVD data locations.  Disney and ABC get the "best" DRM.  Start here: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by SeijiSensei on 2020-03-14
Maybe you should consider dumping the discs.

Can you play the .iso files with VLC after you've ripped the DVDs?  If so, you should consider streaming solutions like DLNA.  I run [minidlna]("https://help.ubuntu.com/community/MiniDLNA") on my home server, and can use DLNA clients like the Roku Media Player app, my TV's native DLNA client, BubbleUPnP+MXPlayer on Android, or VLC on computers.  (The Roku and TV apps are not as comfortable with ASS subs in the MKV container as VLC or MPV are. FLAC audio tracks are also an issue. Most TVs and other hardware are happiest with AAC or MP3 audio in the .mp4 container.) 

As TheFu says, though, some media, especially Disney films, have restrictions. The fact that you can play the content on the "bad" DVDs after converting them to an .iso tells me you should be able to play the original rips as well. If so, you might consider not using physical media after ripping.

---

### Post by TheFu on 2020-03-14
+1 for using streaming, not discs.  No fingers all over the media that way.

---

### Post by oldrocker99 on 2020-03-15
There are several DVD ripping apps, which extract the data on the DVD into a playable video file and are able to get past DRM, which then can be burned to that big DVD and should work fine.

[https://www.cyberciti.biz/tips/linux-dvd-ripper-software.html](https://www.cyberciti.biz/tips/linux-dvd-ripper-software.html)

---

