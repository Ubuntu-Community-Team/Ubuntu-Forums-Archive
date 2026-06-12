---
title: "suspending X with a Firefox client"
date: 2022-01-08
forum: General Help
---

### Post by Skaperen on 2022-01-08
i hope you understand how X can be suspended and detached from the console, allowing the use of text mode (kernel emulated) or a 2nd instance of X which would attach to the console and resume from when it detached or simply start another instance of X.

prior to a few months ago, when i had Firebox play music, and then i switched to a different instance of X, it would just keep on playing forever (at least for a couple days).  then after some Ubuntu upgrade i got a new version of Firefox and it would stop playing music a few seconds after switch to a different instance of X.

when i run other programs, such as Mplayer to play music, everything works as before, so i don't believe it is a change in X.  it sees to be a change in Firefox.

does anyone know anything about this aspect of Firefox like if there is a setting to keep it playing?

i am running Xubuntu 18.04.6 now, with Firefox version 95 and lightdm 1.20 and pulseaudio 11.1.  i do not remember when this happened because i did not recognize the nature of the issue for quite a while.  i run PulseAudio in system mode so music keeps playing as i switch between users on different instances of X.

---

### Post by TheFu on 2022-01-09
Going a completely different way .... would using mpd work, which isn't tied to any user or any GUI?
I'm happy to help with the 3-5 config settings to get mpd working quickly to play local content.  No idea about streamed content so that would likely prevent mpd from being viable. Sorry.

---

### Post by Skaperen on 2022-01-11
```

lt2a/forums /home/forums 4> man mpd
No manual entry for mpd
lt2a/forums /home/forums 5> 

```
i don't know of mpd.  can you describe what it does?  does it replace lightdm?  is it a VNC client that can easily switch around multiple servers?  is it a web browser to replace Firefox?

---

### Post by TheFu on 2022-01-11
mpd is a music/audio server that can be controlled by different clients on many different platforms. It runs as a daemon, not tied to any userid.  The audio is output to the connected speakers on the system, not to the clients controlling playback.

mpd is the daemon.
mpc is the client to control it. There are many, many, other compatible clients. On Linux, I use ncmpc. On Android I use M.A.L.P.  [https://f-droid.org/en/packages/org.gateshipone.malp/](https://f-droid.org/en/packages/org.gateshipone.malp/) (I'm not a fan of google's appstore).  

There are 3 different mpd servers in the house. Each is connected to different speakers. Some day, I'll get them all working together so the same music is played on each concurrently and they share the same DB, but for now, they are separate systems.

sudo apt install mpd ncmpc

There are a few settings to modify in the mpd.conf file and it is likely you'd want to make the client config file connect to your server automatically.  On android, there are different profiles - 1 per mpd server. Very handy.

---

### Post by Skaperen on 2022-01-12
so mpd is effectively a replacement or substitute for pulseaudio?  if so, how do general applications play audio?  is there an alsa stub library?

my understanding (not why i use pulseaudio) is that pulseaudio was designed to have very low lag between application play and sound in the output d/a conversion.  that would be for gamers that need the low reaction time.  i can understand the need even though i am not a gamer.  so i can see a use case to continue to have pulseaudio, but, maybe something else needs to be is use for all but gamer distros (like gubuntu). which would have a timing-tuned pulseaudio.

---

### Post by TheFu on 2022-01-12
> **Skaperen said:**
> so mpd is effectively a replacement or substitute for pulseaudio?  

No.  mpd is a music server.  The audio device used is whatever the system has configured.  It is possible to override this.  mpd needs a pointer to the audio files.

Pulse audio is a service on-top-of OSS or ALSA to add flexibility and simplify stuff for end users.  That's the theory.

---

### Post by Skaperen on 2022-01-12
is mpd being a server in the same sense that X is a server for graphical applications, but just for sound/audio?  if yes then each of it clients is a source of sound?  mpc can be told to play a file in a format it understands?  is there a library to enable my application to play sound?  if yes then what languages?  C?  Python?  is its API compatible with any other?  ALSA?  does it use TCP?  UDP?  SCTP?

---

### Post by TheFu on 2022-01-12
[https://www.musicpd.org/](https://www.musicpd.org/)

---

### Post by Skaperen on 2022-01-12
it says it is powerful.  power is measured in watts.  but they don't say how many watts.

seriously they don't give a specific and detailed description of what it does.  it's not worth me following up with mpd.

---

