---
title: "Xorg disconnects - Ctrl+Alt+F1"
date: 2023-01-24
forum: General Help
---

### Post by Skaperen on 2023-01-24
when pressing Ctrl+Alt+F1, Xorg disconnects or detaches from the physical console, allowing the kernel to use it (for console text mode) or allowing another process to use it, such as another instance of Xorg.  what i am looking for is terminology Xorg uses for this kind of thing.  i am search for more info about how Xorg works with this, or at least is supposed to.  there seems to be a bug introduced in the last couple of years that causes it to hang under this condition.

---

### Post by TheFu on 2023-01-25
For a long time, Ubuntu used CA-F7 as the GUI console and all others were for PTTYs.  I don't recall when, perhaps around 18.04, they moved the default GUI boot to CA-F1.

TTYs are pure text. Good for serial connections.
PTTYs are for pseudo-ttys, which I'm guessing is why a GPU is needed for Ubuntu Server to boot.  There's a way to switch from ptty to tty, so headless servers will work.

I know some poster here have setup serial consoles with no GPU installed.  In the old days, we'd have a no-graphics entry in grub that worked.  Can't remember seeing that in at least a decade.
[https://help.ubuntu.com/community/SerialConsoleHowto](https://help.ubuntu.com/community/SerialConsoleHowto) 

Then there is a multi-seat/multi-head config, where different GPUs are connected to different monitors and each is controlled by a different connected keyboard and mouse. [https://www.x.org/wiki/Development/Documentation/Multiseat/](https://www.x.org/wiki/Development/Documentation/Multiseat/)  

When using the same GPU, the DISPLAY variable could be 
DISPLAY=:0  and for the other user, DISPLAY=:1  <---- that would usually be 2 different GPUs

or they can be 

DISPLAY=:0.0 and for the other user, DISPLAY=:0.1   The last number is the "head" controlled by the same GPU.

Doubt I was any help.

---

### Post by MAFoElffen on 2023-01-25
do 
```

loginctl

```
That will produce results such as:
```

mafoelffen@lunar-module-00:~$ loginctl
SESSION  UID USER       SEAT  TTY 
      2 1000 mafoelffen seat0 tty2

1 sessions listed.

```
Which will tell you which tty is being used, with which session and seat...

---

### Post by Skaperen on 2023-01-25
i'm on 20.04 and different values of DISPLAY= are all the same one gpu.  they are all different instances of X server started by LightDM.  each is working through a different virtual tty has it in graphics mode.  when a tty switch away from a tty in graphics mode happens the kernel informs the process in control of that tty by some means.  then the X server (X11,Xorg) releases its access to the gpu hardware, and presumably tells the kernel when that is done.  then the kernel can establish text mode control for itself or give hardware control to the process that i supposed to have it (typically a different instance of an X server).

long ago i ran 9 sessions of text mode (F1-F9) and 3 X servers (F10-F12) with each running in a different video mode so i could deal with small video RAM.  i switch directly between instances of X running in different processes with just Ctrl+Alt+F10/1/2 with no trouble.  i did change that design around a few times.  today i have LightDM doing the switching for me by name via the command "dm-tool switch-to-user '${username}'".  i have a script to do that named "stu".  but i can do a switch the old way with Ctrl+Alt+somekey.  it is possible to map other keys to do a tty switch (i've also done this in the past with most of they keys on the keyboard).

the issue i am investigating is that recently (2-3 years ago) something changed in Xorg that when Xorg is in a detached state it blocks running and client requests get frozen.  when i am playing a music video and switch to a different user ... a different instance of Xorg leaving the previous one in that frozen state, now ... i no longer hear the music.  if i play the music without involving X at all, i continue to hear it just fine when i switch users.  so, now, i have download the music i want to hear and cannot play the live radio stations on youtube across users.  i want to find out why Xorg did this before i consider it a bug.

---

### Post by Skaperen on 2023-01-25
> **MAFoElffen said:**
> do 
```

loginctl

```
That will produce results such as:
```

mafoelffen@lunar-module-00:~$ loginctl
SESSION  UID USER       SEAT  TTY 
      2 1000 mafoelffen seat0 tty2

1 sessions listed.

```
Which will tell you which tty is being used, with which session and seat...
when i run this on my system, i get nothing for tty.  here is a run with confidential info intentionally cut out:
```

lt1a/forums/1 /home/forums 9> loginctl|cut -c22-
 SEAT  TTY
 seat0    
 seat0    
 seat0    
 seat0    
 seat0    
 seat0    
 seat0    
 seat0    
 seat0    
 seat0    


lt1a/forums/1 /home/forums 10>

```
there are specific ttys.  i can switch to the first one (user admin) with Ctrl+Alt+F7 although i have a keyboard shortcut of Alt+A set to run "dm-tool switch-to-user admin" (Alt+F is "dm-tool switch-to-user forums" to go to user forums where i login to ubuntuforums.org).

---

### Post by TheFu on 2023-01-25
Could audio be tied to the audio chip being used?  My systems have 2 different audio chips - the one on the GPU, which is usually connected to the HDMI output (digital) and the one on the motherboard which supports spdif and analog audio?

I don't use the HDMI audio ever, so my audio is connected to the motherboard.   Pulse audio seems to use the DISPLAY environment variable to decide which user session to connect audio with.  When I want to play music on a system that I'm not actually logged into except over ssh, I have to force the DISPLAY to be :0 just prior to using mpv for playback.  The exact command I use is:
```
DISPLAY=:0 /usr/bin/mpv --no-audio-display --vo=null --volume=50 "$M3U"
```
I was getting X errors before telling it never to output video, since I don't always connect with X11forwarding enabled.

The Pulse guys seem to concentrate only on audio tied to a user session.  [https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/Network/](https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/Network/)  That wasn't/isn't needed with ALSA audio.  I can see why they'd want that as the default, but it messes with my needs and perhaps yours?
> If connecting back to the pulse daemon running on the computer that has the X display is not desired, you can either set PULSE_SERVER=localhost from the SSH connection (make sure module-native-protocol-tcp is loaded though) or run pax11publish -r before SSHing to the remote computer to remove the properties on the root window.


I should check out whether the PULSE_SERVER=localhost actually works ...  Nope.  Lots of errors, no audio.  There might be other setup needed that I didn't do. The pulseaudio server is running with:
```
pulse       1694       1  0 Jan14 ?        00:03:38 /usr/bin/pulseaudio --daemonize=no --system --realtime --log-target=journal
```
So it is setup as a system dæmon, not per user. I specifically want any user in the audio group to be able to play audio on the system, not just my user.
I'm not using the X/Server on that host.  Just X/client stuff.

---

### Post by Skaperen on 2023-01-26
since you mention audio and consoles. i have wondered if there is any remote desktop protocol that includes support for audio in both directions.  ideally, if you have the bandwidth and the right hardware on the client side, you should be able to run a browser on the server side connected to youtube to watch a video and hear the sound.

---

### Post by TheFu on 2023-01-26
There are paid VDI solutions that do it, but what they do is have the video/audio codecs on the client side and transfer the stream to the client directly.  If you want to do that, you can setup a SOCK5 proxy using ssh.

x2go does have video and audio, but it converts both to highly compressed versions not specific for video/audio processing, so it would only be satisfactory over very fast links with high-powered servers.  Here's a youtube video claiming to be x2go showing a 4k video: [https://www.youtube.com/watch?v=cBBfKTiB8OI](https://www.youtube.com/watch?v=cBBfKTiB8OI)  I don't know the setup, but I doubt they are crossing continents or province lines.

PulseAudio and Jack definitely support remote audio.  I've heard people in the music business mixing music live over the internet using a Jack server.  I don't know anything about pipewire, but expect it can do it too.  Might try running Fedora, which has had pipewire for a few releases now.  Fedora seems to get audio right. They didn't have the issues with pulse that Ubuntu has been plagued with the last decade.  I still run into issues with pulse audio, so in my world, **anything** is better.

Remote audio should be relatively easy around the world, since 256Kbps for extreme quality is easy for most modern connections.  Video is much harder, since they go from 2500Kbps to 20Mbps and stable connections of that type aren't available everywhere.

---

