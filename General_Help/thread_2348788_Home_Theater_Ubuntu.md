---
title: "Home Theater Ubuntu"
date: 2017-01-07
forum: General Help
---

### Post by enzodad on 2017-01-07
Hello everyone - ive been searching for about a week now to no avail. 

Im tyring to switch over from windows- ive installed various versions of Linux- I was told ubuntu would be best but ive yet to get it working correctly.

I need to be able to Bitstream- from what i understand i cant use Pulseaudio i have to use ASLA- our computer is used for normal web browsing and work but 90% duty is HTPC.
we need to be able to bitstream audio and video. Our receiver will handle all audio-Dolby TrueHD-DTS-HD/Atmos/DTSX/AURO-3D, and will passthrough Video to our 4K tv. We just need a way to do so like we do in windows. How can we use ASLA system wide- OR make a easy swap between them

Currently do not have Ubuntu installed because i dont want to go through a headache if i cant get it to work.
we were told using pavucontrol would allow this option but last time we tried id did diddly squat.
i like most people use windows because although its a pile of garbage and unsecure it works-

we have 12TB of full(1/1) blu-ray rips and dont want to lose audio and video quality.

specs are i3 4360 3.7Ghz
16Gb ram
Nvidia GTX950 HDMI 2.0

even our motherboard has HDMI but we dont use that because unable to perform as good as 950

---

### Post by TheFu on 2017-01-07
Expecting Linux to behave like Windows is a huge mistake.  There are huge, large, extremely different architectural differences and design philosophies.  So - to avoid as many early issues as possible, about the only thing you can reuse is directories and files.  Permissions are core to Unix-like systems. It is multi-user from the start, even if only 1 person uses the system.  Linux uses different file systems too. When sharing files, that is a difference from what most Windows users are used to and often causes unexpected (to them) issues.  For simplistic sharing, using NTFS for data isn't an issue, but if any strange, newer, techniques that Microsoft has added in the last 5 yrs are used with the storage, problems can arise.  For example, if that storage has been merged into a single volume, then linux won't be able to use it without some hassles, if at all.

You don't need to be an expert, but a minimal set of knowledge is required. For your specific requirements, it comes down to drivers for the hardware that you have.

Not sure what you mean by "bitstream" - I've only heard that term related to fonts from the early 1990s. [https://en.wikipedia.org/wiki/Bitstream_Inc](https://en.wikipedia.org/wiki/Bitstream_Inc).

Short of posting exact chips used by your system audio and looking at the drivers that uses for support of the things you care about, I really doubt anyone here can help.

I don't keep a PC near my projector or in the room with any audio equipment. That is what networking is for.  My front-ends are all small, silent, devices like a roku, chromecast, raspberry pi, any android device or any remote PC (that I control).  My "back-end" holds all the media and provides either direct access to the contained data or transcodes it on the fly as necessary for the specific front-end.

So ... I don't have any high-end GPUs anymore. My back end is a G3258 (about  2/3rds of the performance).  Perhaps my ears aren't a good as yours, but it sounds great on my older THX receiver.

Ok, so Ubuntu is just the general purpose OS. It is not a media center.  The way you have your media on the machine (how it is stored and how it was "ripped") will determine which media center software is best for you.  I've only used XBMC/KODI/MiniDLNA/PlexMS and direct playback methods using network storage.  I've seen "passthru" in the menus for both Plex and Kodi. 

Getting TV-recording to work with these things is usually non-trivial. It depends on the type of signal, any DRM involved, and the tuners used. I'm using HD-Homerun "Connect" tuners for OTA TV, commonly known as HDHR4. Also have a few HDHR3 models, but those aren't as easy to use with Linux.  Pretty much any Linux machine can use the HDHR4 tuners to capture broadcast TV in N. America.  Kodi is working on PVR addons.  I don't have those working here, but can watch live TV through my R-Pi just fine and can manually capture a TV steam on a specific channel for a specific time easily on the R-pi. It requires minimal CPU - basically, just enough to store the file onto disk.

If you do have to use a network to push the content around, then don't use wifi. For Bluray bandwidth, most wifi just isn't stable enough in most install locations. Even powerline networking works better, without huge fluctuations in bandwidth.

Unfortunately, if you are looking for "100% it will work", nobody can say that.  
* Make a backup of everything you can't afford to lose
* make room for 2 partitions - a) 10G-20G for the OS and b) 4G for swap (no hibernation allowed)
* Install the version of Ubuntu Desktop you want - I like the Mate version with is most like Windows, IMHO. You'll need to "do something else" at the storage setup
* The media will need to be in a specific layout as commonly dictated by XBMC, Plex, Kodi for the last 5+ years.  Movies, TV, Home videos, Music, Photos all need to be separate.  Multiple directories can be added to each type.  I have 3 "movie" disks. No need to merge a file system from multiple disks, if that makes sense.

And before you start, read this: [http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html)
and this: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Once you get things setup, just normal backups are necessary.  Besides that, it pretty much runs itself for a desktop.  No need to reinstall the OS every year either. Cruft just doesn't happen all that much on Linux.

nvidia has a Linux-specific forum: [https://devtalk.nvidia.com/default/board/98/linux/](https://devtalk.nvidia.com/default/board/98/linux/) might ask a specific question there.  I'm just a Linux generalist and media center guy, not looking for audio beyond 99% great. That last 1% is probably where you are.

---

