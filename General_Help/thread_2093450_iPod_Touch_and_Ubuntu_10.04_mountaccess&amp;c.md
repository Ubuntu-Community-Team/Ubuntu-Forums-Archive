---
title: "iPod Touch and Ubuntu 10.04 mount/access/&amp;c"
date: 2012-12-10
forum: General Help
---

### Post by jamesisin on 2012-12-10
I have a brand new iPod Touch (32 GB).  I have done nothing to it except to log in and attach it to my home wireless network.

I can attach it to my Ubuntu machines and (after sorting out an issue with a shorted cable) nothing comes of it.

On my iPod classic I had to convert it initially to a WinPod (rather than a MacPod), but I believe that is no longer necessary.  Also on that device I turned on the so-called Disk-Mode which I also believe is no longer necessary.

Nonetheless, I cannot make this device mount and become folder-accessible so that I can fill it with flac music goodness.

Suggestions?

---

### Post by Mister08 on 2012-12-10
> **jamesisin said:**
> I have a brand new iPod Touch (32 GB).  I have done nothing to it except to log in and attach it to my home wireless network.

I can attach it to my Ubuntu machines and (after sorting out an issue with a shorted cable) nothing comes of it.

On my iPod classic I had to convert it initially to a WinPod (rather than a MacPod), but I believe that is no longer necessary.  Also on that device I turned on the so-called Disk-Mode which I also believe is no longer necessary.

Nonetheless, I cannot make this device mount and become folder-accessible so that I can fill it with flac music goodness.

Suggestions?

With the new iPod touches (I own a 32GB 4th gen) there is no longer a disc mode that CAN be enabled. Apple did their best to force you to use iTunes to manage music and files. The most I have been able to do is mount my ipod and pull pictures off of it. Also, iOS 6 is not supported by Amarok or any other software usually used to sync music to iPods at the moment. Your best bet would be to make a Windows virtual machine and install itunes within that, and manage your music that way until upgrades have been made

---

### Post by jamesisin on 2012-12-10
Well...

My music is all FLAC.

So I guess this is the big "fork you" from Apple to folks like us.

Any further suggestions are appreciated.

---

### Post by Mister08 on 2012-12-11
> **jamesisin said:**
> Well...

My music is all FLAC.

So I guess this is the big "fork you" from Apple to folks like us.

Any further suggestions are appreciated.

Well, depending on what generation of iPod you are using (I don't THINK it will work on the gen 5...if those have even been released yet) and what iOS version you are running.

What I would recommend is jailbreaking your device. The only disadvantage of this, is the newest generation devices cannot be jailbroken; and iOS 6 is only in a tethered jailbreak forcing you to connect it to a computer to reboot your device back into it's full functionality after the battery dies or if you are forced to shut it down.
If you are willing to do this however there is a good guide located at:
[http://www.redmondpie.com/jailbreak-ios-6-with-official-cydia-on-iphone-and-ipod-touch-a4-using-redsn0w-0.9.15b1/](http://www.redmondpie.com/jailbreak-ios-6-with-official-cydia-on-iphone-and-ipod-touch-a4-using-redsn0w-0.9.15b1/)

You may be able to find a patch for the system or a new music app with FLAC support, but as I have not jailbroken my device since 4.2.1 I can't tell you with any level of certainty.

What I have resorted to; for high end audio is converting them to 320kbps mp3's; they are smaller and the audio difference is very small and nearly undetectable to the untrained ear. I don't particularly enjoy mass converting hundreds of files; but when you are dealing with a money hungry company like Apple, it often forces you to go the extra mile to get your device to work like you wish it would.

Hope I was some help!

---

### Post by jamesisin on 2012-12-13
They really have this new generation locked down.  I found a free app for playing FLAC (FLAC Player + or similar), but it's rather shockingly clunky for uploading music.

You visit a Web page (yep, the iTouch is capable of Web serving) and load, wait for it, one file at a time--over wireless.  Ugh.

I don't like the idea of stacking hacks so I may just abandon Apple's music players and choose another.  This is just not beginning well.

---

### Post by apochry on 2012-12-13
The [Spotify Linux Client]("http://www.spotify.com/uk/download/previews/") claims to be able to manage music on iPods and iPhones. If it uses libraries other than 'libimobiledevice' which is used by all the open player out there such as Amarock, Rhytmbox, etc.
I haven't tried it personally since I got rid of all Apple devices I had, but I think it's worthed giving it a shot.

---

### Post by Kirk Schnable on 2012-12-13
One possible way to get the music on your device might be to use Subsonic and iSub.  I personally have more music than I could fit on my 64GB iPod Touch, or my iPad for that matter.  If you have a Subsonic server running ([www.subsonic.org](www.subsonic.org)) it can transcode your FLAC to MP3 right on the fly, and your iPod will be able to listen to it with an app like iSub ([www.isubapp.com](www.isubapp.com)).

iSub has offline caching functionality, so you can keep your "mp3 transcodes" on your iPod memory and having a constant Internet connection is not needed if you're going to listen out of cache.

I don't sync my music with iTunes, but I don't listen to my own FLACs directly, I listen to them using a web browser and my Subsonic server, or my iPod\iPad and iSub app.

Not necessarily the best route to take, but this is an option you should be aware exists.

---

