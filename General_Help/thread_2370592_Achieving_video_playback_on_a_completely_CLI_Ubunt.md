---
title: "Achieving video playback on a completely CLI Ubuntu?"
date: 2017-09-05
forum: General Help
---

### Post by xathian2 on 2017-09-05
Let me preface this by saying I am pretty new to Linux so I will do my best to explain what's wrong with my very inexperienced terminology.

So recently I've gotten a Raspberry Pi and I've undertaken a little project where I want to turn it into a lightweight player for Youtube and Twitch.tv. Now I've opted to try to do this using Ubuntu Server because I would like to avoid a desktop environment because it is very slow (even Raspbian) to boot and using a browser + videos/streaming + the whole linux environment just eats up way too much resources. Also I would just love the very quick and simple access I could have with a fast boot to CLI and just typing an alias command like "shroud" (aliasing "Streamlink twitch.tv/shroud best --player mpv ") and having the video directly pop up, no frills.

I've gotten the basic things set up such as Ubuntu Server 16.04 itself, MPV (VLC is also an option) along with youtube-dl to stream youtube videos and Streamlink to stream from Twitch.tv. The problem comes when trying to playback any form of video. Be it using Youtube-dl/Streamlink or just trying to playback a local mp4 file on the Pi to test. The problem comes from what I can guess to be some sort of disconnect between running a CLI only environment and trying to launch an actual video player from it (since there's no desktop environment, I assume this means no way to "render" something like a video). I can get VLC to locally playback a test MP4 in some funky ASCII video thing but I cannot for the life of me find a way to get these players to open into an actual usable video playback.

I'm assuming there is something I need to do where I tell MPV/VLC to run a proper environment (or whatever, the term I see a lot in vague posts I find with google mentions "xserver" and "framebuffer", but not real instructions) where video playback is possible but after several days of Googling I just can't find any answers at all. I found a post from 1 year ago on reddit where a user claims to run video from a CLI-only Arch install with MPV (For use playing advertising videos on a TV at a Kiosk) so I assume it's definitely possible but the old thread can't be replied to and the user didn't reply to my message so I can't ask how he did it.

---

### Post by TheFu on 2017-09-05
You are doing this the hard way.
If you have a r-pi v2 or v3, then shove OSMC onto the SD card, boot it, run kodi. Be happy. There are probably addons for twitch.tv. I know there is a youtube addon.  OSMC is designed to run on r-pi devices.

I find the default OSMC theme to be slow and suck. That only matters when a video isn't playing.  I swap the default theme for the old default, Confluence, and things are better, even good.  On a pi-v3, things are excellent, very fast.  For a remote control, I use an RC6 remote, but there are Android apps too or a web frontend if you want to use a computer on the network.

[https://osmc.tv/](https://osmc.tv/) - you don't need their funny copy tool to put the OS onto an SD card.  I just **dd** the image file.  At first boot on the Pi, it repartitions the SD and at 2nd reboot, there is a guided setup.  Probably easier if you have a keyboard connected. I never do.  I'm not exactly a noob with Linux.

Don't do things the hard way and you'll be happier.

---

