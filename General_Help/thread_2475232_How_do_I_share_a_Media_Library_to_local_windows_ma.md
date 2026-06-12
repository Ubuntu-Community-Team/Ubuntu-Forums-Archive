---
title: "How do I share a Media Library to local windows machines?"
date: 2022-05-19
forum: General Help
---

### Post by daring-t on 2022-05-19
Hello, I recently migrated to Ubuntu and I was wondering if there a way to share your media library with your local Window users. On Windows you can share/stream your media library in Windows Media Player. Is there a way to do this is in Ubuntu? 



Thanks,
Daring_t

---

### Post by TheFu on 2022-05-20
There are 2 main methods.
[LIST]
[*]CIFS/samba disk shares
[*]DLNA stream running the server on Linux and DLNA clients on the other systems.
[/LIST]

DLNA works well for compressed content - h.264 and h.265 videos.  The problem with DLNA is that most DLNA servers don't have any protection to limit access of content to specific people.  Jellyfin is the only DLNA server that I know which allows different users. But we don't segment content by users, so I'm not sure if that matters or not.   For the DLNA controller/client, we use Kodi or OSMC or VLC.  All work well over wired connections.  I've been disappointed with most streaming sticks trying to access my DLNA server.  Chromecasts are completely useless, IME.

CIFS shares can be setup on a per-user basis with read-write and read-only access or no access, as you like.  CIFS does seem to have more stuttering than other methods, like NFS, but NFS really isn't used on Windows.  If you have other Linux/OSX/BSD clients, use NFS.

Of course, wired ethernet is better than wifi for all of this. Massively better. It is hard to explain, but wifi bandwidth is constantly changing in a way that humans don't notice when surfing or emailing, but computers see it when streaming.  Large buffers on each client can only help so much.

Most DLNA servers also have a web interface. Plex, Emby, Jellyfin all do. Typically, this will force transcoding to browser supported codecs, so the server may need to be beefier, especially if multiple clients will be streaming concurrently.

---

### Post by daring-t on 2022-05-22
Sorry for the late response, I'm going to have into how to correctly run a DLNA sever on Ubuntu, but thank you for the pointing me in the right direction!


Thanks,
Daring_t

---

### Post by ajgreeny on 2022-05-22
I still use minidlna as a mediaserver to my Android tablet and smart TV.  I also use Emby and Jellyfin but disable the DLNA server on both of them as it's not needed.

Minidlna is a small and effective system for my needs hut it does need clients that can deal with it easily, something that I will have to let you search for as it has always just worked for me. On other computers vlc always works fine so should be good for a Windows machine.

---

### Post by TheFu on 2022-05-22
> **daring-t said:**
> Sorry for the late response, I'm going to have into how to correctly run a DLNA sever on Ubuntu, but thank you for the pointing me in the right direction! 

No problem. I have no clue about Widows media player.  Even when I was mostly Windows on the desktop, I found that program less than useless. There have always been better choices, IMHO.

These days, my Windows use is limited to running finance and tax software - perhaps 2 hrs every other week.  Everything else happens in Linux (I'm including Android).

My media setup: 
**Servers:**
[LIST]
[*]Plex Media Server (migrating away from it due to crazy levels of tracking)
[*]Jellyfin Media Server (zero tracking)
[*]MiniDLNA (emergency use only; zero tracking) This lacks the transcoding feature that Jellyfin and Plex provide. 
[*]mpd (audio server)
[/LIST]
**Video Clients:**
[LIST]
[*]Jellyfin Web GUI (meh)
[*]VLC on Android
[*]OSMC/Kodi on raspberry Pi computers - they use the DLNA interface - zero tracking
[*]Roku3 - this is pretty old now and does more tracking than Plex, which is actually very hard to believe. I generally only use the Roku for paid internet streams, never to access local DLNA content. 
[/LIST]

**Audio Clients:** These all communicate with the mpd server to control playback on different mpd servers around the house.
[LIST]
[*]MALP (android)
[*]ncmpc - all my linux systems have this to control multiple mpd servers.
[*]mpc - For a quick 'update' command, if new audio files have been added (podcast, new CD)
[/LIST]

I've had problems with VLC on Windows and Linux "finding" the DLNA servers on the network. Sometimes they do, sometimes they don't.

If all your content is natively playable by all the clients, then transcoding doesn't matter. If the clients cannot handle all the content types, you'll want transcoding.  Transcoding needs a server that can support it. A rule of thumb is 3000 passmarks per concurrent hidef stream that requires transcoding.  For years, I used hardware-based playback devices. They supported h.264, divx and mpeg2 video content, but nothing else. The DivX support was what we used pre-h.264 for quality compression.  Now that content is stored as vp9, h.265, AVC1, most of my playback devices just can't handle that video codec and need for the content to be transcoded to h.264.  If all the clients are relatively new computers, this won't matter to you.  But if you have any raspberry pi v3/v2 media players, you'll need transcoding for the newer codecs. If you have a 5 yr old computer, the newer codecs aren't decrypted in hardware and you'll need a mid-tier CPU, not any low-end CPUs for playback.

Jellyfin has great metadata locating stuff and supports recording of TV using HDHR network tuners. The metadata aspect to Jellyfin blows away what Plex does, IME.  Plex is routinely confused.  Jellyfin does lack some things that Plex does. I miss the easy access to "unwatch" content. There's a way to get it in Jellyfin, but it isn't right there in the top menu.

I'm anti-smart devices - they are only smart for the companies doing the tracking. We don't connect any TVs/Projectors to the internet. Just don't agree to be spied on in our own home.

With playback of nearly all video and audio today, there is tracking. It does take effort to minimize, but if you don't care, then you don't care. The ways that internet connected players and TVs spy is really interesting. Even for content they don't get to know directly, they can 'fingerprint' the audio and video to provide the data back to the home trackers ... unless the TV can't talk to the internet.

---

### Post by ajgreeny on 2022-05-22
I would totally agree with TheFu regarding Jellyfin being better than Plex or Emby in many ways, and it is also open source.

Emby used to be open source until a few years ago but then became closed source, since when, in my experience, it has become more annoying in its requests for users to pay for the Premiere membership, not something I want or need.  Jellyfin is a fork of Emby which has moved on from then and is now extremely good except for its lack of a client app for LG TVs.

I use these media servers to stream video, music and photos to my LG smart TV, which always finds my minidlna server and also has an Emby client app available, hence my main use of Emby.  Currently, as mentioned, there is no available Jellyfin client app for LG TVs.  In theory you can use the web-browser app on the TV but in practice this is simply too clunky and difficult to use and far too long winded to consider as a practical method.  As soon as Jellyfin manages to get a client app on LG TVs my use of Emby will be quickly replaced by Jellyfin.

---

