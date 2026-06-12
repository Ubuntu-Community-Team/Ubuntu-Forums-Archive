---
title: "Alsa or Oss,12.04.2 LTS server, no GUI."
date: 2015-04-11
forum: General Help
---

### Post by Cool_Javelin on 2015-04-11
I installed MPD on my server, (Ubuntu 12.04.2 LTS server, no GUI) but it won't start.

I think I do not have sound card drivers installed, can someone help me find that out?
I read [here]("http://en.wikipedia.org/wiki/Open_Sound_System#OSS_in_relation_to_ALSA") a little about OSS, and that mentioned "/dev/dsp". I do not have that device.

I also think the basic drivers are either ALSA or OSS. I also read something about Pulse, do I really need both?

I really don't care for much in the way of features, I don't need mixers, equalizers, surround, I only want stereo.

If ALSA and OSS are the drivers, I would prefer the smallest install. Of course reliability is an issue.

Is there a good tutorial for explaining and installing the drivers?

Perhaps someone can suggest the basic steps needed to get only music from the MPD daemon.

Thanks, Mark.

---

### Post by Holger_Gehrke on 2015-04-11
ALSA (Advanced Linux Sound Architecture) and OSS (Open Sound System) are the low-level drivers that talk to the hardware. They are part of the Kernel. If you have the 'snd' module loaded (lsmod), they are available. Pulse sits on top of them. Applications "talk" to Pulse without having to know anything about each other or the sound hardware. mpd can talk directly to the low-level drivers, so Pulse is not strictly needed. 

The 'd' in 'mpd' stands for 'daemon', so it's a server running in the background, controlled by some client. Without a client it will just sit there and do nothing. Try installing 'mpc', putting some music in /var/lib/mpc/music, running 'mpc update' to make the server update its database with the files. Then 'mpc ls' will show you the files mpd knows about, 'mpc add "filename"' will add a file to the playlist and 'mpc play' will start playback.

In my opinion, if you don't want or need remote control of playback from across the network -- perhaps even streaming and or recoding, mpd is overkill. For just playing some music on a system without a gui there are easier solutions like mpg321 or mp3blaster.

---

### Post by Cool_Javelin on 2015-04-24
Well, I gave up.

I found audio worked just fine on the desktop live CD, so I just installed it instead of the server.

Gotta wonder why it's so hard to get audio working on the server.

Oh, well, I'll mark as solved.

Mark.

---

