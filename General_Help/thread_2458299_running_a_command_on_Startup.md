---
title: "running a command on Startup"
date: 2021-02-21
forum: General Help
---

### Post by pjstock on 2021-02-21
For some reason, each time I restart my system (Ubuntu 20.04.2 LTS) I don't have any Sound and so have to run a command line in Terminal to get sound working.

sudo alsa force-reload

This is not onerous but I have to go hunting for that command each time I reboot.

I tried adding it to the Startup Applications GUI thing but on a test reboot, the sound did not automatically reinstall.

It maybe be because in Terminal I am prompted each time to manually enter  my Password. 

I am wondering if there is a better way to run that command automatically on Reboot. (and my password if necessary. though that would seem to negate the value of a password, having it be entered automatically.)

Many thanks

Peter

---

### Post by schragge on 2021-02-21
Have you tried other commands like **alsactl init**?

Finding out why sound doesn't work and fixing it is probably the right way to do.

 But barring this, [dex]("https://manpages.debian.org/unstable/dex/dex.1.en.html") is a nice tool to generate an autostart DesktopEntry file. It only takes the command name as argument though. You'll have to edit the generated **.desktop** file and add the **force-reload** argument, then put it under **/etc/xdg/autostart**. I guess the autostart files put  in there would be executed with root privileges (correct me if I'm wrong). [The spec]("https://specifications.freedesktop.org/autostart-spec/autostart-spec-latest.html") says only
> the application will be       automatically launched during startup of the user's desktop environment after the user       has logged in.
If that not works, you probably will have to write a systemd unit file for this.

---

### Post by HermanAB on 2021-02-21
The Olde Skool rc.local will always be my favourite.

---

### Post by TheFu on 2021-02-21
I haven't touched any alsa stuff in a long time. Pulse is the interface to be used on Ubuntu for about the last 5 yrs. Alsa is still there, but controlled by Pulse now.  Pulse-Audio can be run in either *system-mode* or *user-mode*.  User-mode is the default.  It requires a user session to work, however and it is somehow tied to the GUI session. About once every week or two, my pulseaudio daemon crashes. That has been common the last 5 yrs.  The solution, in user-mode, is to 
```
/usr/bin/pulseaudio --kill  # kill it, if it is still running
/usr/bin/pulseaudio --start  # start it in daemon-ized mode
```
You can place a script file (be certain it is marked with execute permissions) into your session startup programs. No sudo needed.

From the pulseaudio manpage:
```
       --start
              Start PulseAudio if it is not running  yet.  This  is  different
              from  starting PulseAudio without --start which would fail if PA
              is already running. PulseAudio is guaranteed to  be  fully  ini&#8208;
              tialized when this call returns. Implies --daemonize.

       -k | --kill
              Kill  an  already  running PulseAudio daemon of the calling user
              (Equivalent to sending a SIGTERM).
```
Firefox only works with pulseaudio on Ubuntu from the repos. Before that change, I was fighting pulseaudio completely.

Using pulseaudio in system-mode brings some challenges and isn't recommended by the pulse audio team.  There is some information about this mode at the FreeDesktop website where the Pulse project is. They certainly do write a bunch of documentation. Pulse is a complex system that can do 100 things, 90 of which most end users don't care.

The only tweak I needed which changed the pulseaudio crashes from once every 2 hrs to about once each week or two was in the ~/.config/pulse/client.conf file - added this:
```
enable-shm = no
shm-size-bytes = 0
```
For me, that changed stability.  If there are multiple users, there is a system-wide client.conf file in /etc/ somewhere.

Because I reboot after a new kernel is installed (eventually), I haven't noticed pulse audio crashing nearly as much since moving my desktop to 18.04 from 16.04. There are many more kernel updates with newer releases.

Not that this matters, but Fedora is looking to replace PulseAudio with some new-fangled sound system soon. I don't know anything about it. [https://en.wikipedia.org/wiki/PipeWire](https://en.wikipedia.org/wiki/PipeWire) is the wikipedia article. Looks like it was needed to support restrictions in flatpaks and Wayland. Of course, the people who love it are all in on Wayland.

---

### Post by CatKiller on 2021-02-21
> **TheFu said:**
> Not that this matters, but Fedora is looking to replace PulseAudio with some new-fangled sound system soon. I don't know anything about it. 

PulseAudio was an improvement on ALSA's dmix: it did things the things dmix could do better than dmix did, and could do a bunch of things that dmix couldn't - unfortunately also including exposing bugs in ALSA. It wasn't an improvement on JACK, though, since the user-friendly buffering adds latency, and you can't wire up an arbitrary path through applications for your audio stream. It also only handles audio.

PipeWire is planned to fix those: it's to handle audio and video streams, so they stay in sync, allow secure routing between applications, including containerised ones, and have low latency. If it works, it should be useful.

---

### Post by #&amp;thj^% on 2021-02-22
> **TheFu said:**
> 
Not that this matters, but Fedora is looking to replace PulseAudio with some new-fangled sound system soon. I don't know anything about it. [https://en.wikipedia.org/wiki/PipeWire](https://en.wikipedia.org/wiki/PipeWire) is the wikipedia article. Looks like it was needed to support restrictions in flatpaks and Wayland. Of course, the people who love it are all in on Wayland.

Route all Audio to PipeWire
&#55357;&#56599; Summary

This change proposal is to route all audio from PulseAudio and JACK to the PipeWire Audio daemon by default.
&#55357;&#56599; Owner

    Name: Wim Taymans
    Email: wim.<Snip>

&#55357;&#56599; Current status

    Targeted release: Fedora 34
    Last updated: 2021-02-17
    FESCo issue: #2508
    Tracker bug: #1906086
    Release notes tracker: #611
Installed on Arch Install Looks like:
```
Name            : pipewire
Version         : 1:0.3.22-1
Description     : Low-latency audio/video router and processor
Architecture    : x86_64
URL             : https://pipewire.org
Licenses        : LGPL
Groups          : None
Provides        : libpipewire-0.3.so=0-64
Depends On      : rtkit  alsa-card-profiles  libdbus-1.so=3-64  libncursesw.so=6-64  libsndfile.so=1-64  libudev.so=1-64  libasound.so=2-64  libsystemd.so=0-64  libbluetooth.so=3-64  libsbc.so=1-64  libldacBT_enc.so=2-64  libopenaptx.so=0-64  libfdk-aac.so=2-64
Optional Deps   : pipewire-docs: Documentation
                  pipewire-alsa: ALSA configuration
                  pipewire-jack: JACK support
                  pipewire-pulse: PulseAudio replacement [installed]
                  gst-plugin-pipewire: GStreamer support [installed]
Required By     : gst-plugin-pipewire  pipewire-pulse
Optional For    : None
Conflicts With  : None
Replaces        : None
Installed Size  : 5.75 MiB
Packager        : Jan Alexander Steffens (heftig) <heftig@archlinux.org>
Build Date      : Thu 18 Feb 2021 16:00:53 MST
Install Date    : Mon 22 Feb 2021 11:09:31 MST
Install Reason  : Installed as a dependency for another package
Install Script  : Yes
Validated By    : Signature

```
Been Testing it for a couple of days now>>>>Sure Beats LP's first offering of PulseAudio. LOL
I think the majority will like it. Not all of us are all in on Wayland. ;) (In fact more than you would think are not)

---

### Post by CatKiller on 2021-03-05
> **TheFu said:**
> Not that this matters, but Fedora is looking to replace PulseAudio with some new-fangled sound system soon. I don't know anything about it. 

There's some more information and history [here](https://lwn.net/SubscriberLink/847412/d7826b1353e33734/), if you're interested.

---

### Post by SeijiSensei on 2021-03-05
> **HermanAB said:**
> The Olde Skool rc.local will always be my favourite.

Since 18.04 /etc/rc.local no longer exists in Ubuntu distributions. However, if you create the file and put commands there, they will work. Under systemd, they want us to create "unit" files.  

See "man systemd-rc-local-generator" for details.

I still use /etc/rc.local, too. Most commands I put there are a single line. Sometimes I'll put static routes in there.  Why I'd want to construct a "unit file" for these purposes escapes me.

One important thing to know.  /etc/rc.local is not run "last" under systemd. Read the man page for details.

---

