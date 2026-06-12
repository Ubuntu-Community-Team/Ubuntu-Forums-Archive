---
title: "Have to kill pipewire to play videos and hear sounds"
date: 2023-07-29
forum: General Help
---

### Post by dangillmor on 2023-07-29
Ubuntu 22.04.2 on Thinkpad X1 Carbon 9.

History: I installed pipewire, hoping to get better sound from the notoriously lousy sound PulseAudio provides on this machine. I had multiple problems, and removed pipewire, or tried to. The uninstall also removed some key Gnome functionality, and I had to reinstall the desktop UI. Meanwhile, pipewire appears to have been re-installed in some update.

The current issue: When I play a video (streaming from almost any source) I have to go into Activity Monitor and kill pipewire. Otherwise the video won't play. 

However, the pipewire process keeps restarting, forcing me to do this routine pretty much every time I start a video from a new source. Frustrating.

Wondering if anyone has any suggestions on how to deal with this.

UPDATE: Now every time I kill the pipewire process it restarts immediately (as in a second or two later)...

---

### Post by TheFu on 2023-07-30
```
sudo systemclt disable pipewire
sudo systemclt mask pipewire
```
or something similar. I don't know the name of the daemon process for pipewire, so you'll need to figure that out and there could be multiple daemon process to disable and mask.

BTW, [https://ubuntuhandbook.org/index.php/2022/04/pipewire-replace-pulseaudio-ubuntu-2204/](https://ubuntuhandbook.org/index.php/2022/04/pipewire-replace-pulseaudio-ubuntu-2204/)

---

### Post by guiverc on 2023-07-30
You mention Ubuntu 22.04.3 ??

Are you sure that's what you're running, a quick look at ubuntu-updates base-files and it looks to me

- base-files | 12ubuntu4.3    | jammy-updates   | source, amd64, arm64, armhf, i386, ppc64el, riscv64, s390x
- [https://packages.ubuntu.com/jammy-updates/base-files](https://packages.ubuntu.com/jammy-updates/base-files)
- [https://changelogs.ubuntu.com/changelogs/pool/main/b/base-files/base-files_12ubuntu4.3/changelog](https://changelogs.ubuntu.com/changelogs/pool/main/b/base-files/base-files_12ubuntu4.3/changelog)

and I'd not expect you to have 22.04.3.   Note: I'm not running *jammy* or 22.04 myself, so I've not checked except via the online detail I looked at (*terminal & links I pasted*) are slightly outdated, as 22.04.3 is expected *momentarily* anyway (*ie. momentarily ~= next few days I suspect*)

FYI: I did ask on IRC & someone running *jammy* confirmed 22.04.2 is what they have when fully-upgraded too.

---

### Post by dangillmor on 2023-07-30
Whoops, typo -- you're right, it's 22.04.2. (Will edit original.)

---

### Post by dangillmor on 2023-07-30
Thanks, tried these (it's systemctl) and am told they don't exist, yet pipewire continues to show up as a running process. Absolutely bonkers.

---

### Post by TheFu on 2023-07-30
> **dangillmor said:**
> Thanks, tried these (it's systemctl) and am told they don't exist, yet pipewire continues to show up as a running process. Absolutely bonkers.

I knew systemctl was correct ... it is the pipewire-something stuff that you need to figure out.  Or am I misunderstanding?

New is the enemy of stable.  Always remember that.  PulseAudio is just starting to become stable for my use ... and I think it was started around 15 yrs ago.  On that timeframe, pipewire will become stable some time after 2030.

---

### Post by #&amp;thj^% on 2023-07-30
> **dangillmor said:**
> Thanks, tried these (it's systemctl) and am told they don't exist, yet pipewire continues to show up as a running process. Absolutely bonkers.

It should show if running with
```
systemctl --user status pipewire 
&#9679; pipewire.service - PipeWire Multimedia Service
     Loaded: loaded (/usr/lib/systemd/user/pipewire.service; enabled; preset: >
     Active: active (running) since Sun 2023-07-30 09:51:29 MDT; 19min ago
TriggeredBy: &#9679; pipewire.socket
   Main PID: 2320 (pipewire)
      Tasks: 2 (limit: 18931)
     Memory: 21.8M
        CPU: 10.114s
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/pipew>
             &#9492;&#9472;2320 /usr/bin/pipewire

Jul 30 09:51:29 kaisen-lvm2 systemd[2251]: Started pipewire.service - PipeWire>

```
Maybe check that it is running first.
Nor do I consider "new as an enemy", but the path forward .

---

### Post by TheFu on 2023-07-30
> **1fallen said:**
> Nor do I consider "new as an enemy", but the path forward .

All OT follows:

I didn't say that new was the enemy. I said:
> New is the enemy of stable.
Completely different meanings.  When people do things that are non-default, with new software, they should expect issues.  The list that proves this is very long and changes over time as things become less "new" and more stable.

I expect developers to nearly always run new software. That's the nature of software development.  OTOH, end-users really should stick with LTS only software and try to stay with the defaults as much as possible, unless they just like hassles and pain.

I spent a decade where we absolutely had to get the newest Linux code to have a working system. That isn't the situation today.  Canonical is known for pushing "new" too early for the last 10 yrs.  About 10 yrs ago, Canonical discovered that if they didn't make something the default, then very few people would try it. This is why Canonical inflicts non-stable software onto all of us BEFORE it is ready.  I'll offer up systemd, pulseaudio, Wayland, netplan, network-manager, avahi, and many systemd modules like resolved, timed, mount, automount and snaps as proof.  Each of these things was inflicted onto Ubuntu users prematurely. I suppose that's a matter of opinion and the way any specific software is used.

Booting and upgrading ZFS is still an issue with Ubuntu.  For use on data-only storage, it has been stable for a long time.  ZFS on 20.04 was so bad iniitally, I had it for the OS just 20 minutes before wiping.

Pipewire isn't even being pushed by Canonical, so expecting it to be marginally "stable" is unrealistic, IMHO.  Jack would be a better choice if problems with Pulseaudio are being experienced, though, if I understand it, Jack is just a layer over Pulse which is a layer over ALSA.  The only reason we have pulse audio mandated is because Firefox decided to only support the pulseaudio interface on Linux.

---

### Post by tea for one on 2023-07-30
> **TheFu said:**
> The only reason we have pulse audio mandated is because Firefox decided to only support the pulseaudio interface on Linux.

Pipewire as default in Ubuntu 23.04 has a nice feature where you can record audio while playing it in Firefox i.e. Record what you hear.
```
pw-record --target Firefox file.mp3
```

---

### Post by #&amp;thj^% on 2023-07-30
> **tea for one said:**
> Pipewire as default in Ubuntu 23.04 has a nice feature where you can record audio while playing it in Firefox i.e. Record what you hear.
```
pw-record --target Firefox file.mp3
```
+1
It's funny how many have problems with both pulseaudio and pipewire, I find the later very stable and fix's some of the audio problems on my end, especially my X1 Carbon 7th Gen And my Legion5 AMD Bluetooth. (very happy with my pipewire/wireplumber set-up)
@ TheFu I always expect new is the enemy of stable, and never truer words spoken, but some newer hardware requires a New Look or View, you need to relax a bit, not everyone subscribes to your ways or methods.
That is said with a great respect for your background and knowledge, but everything in moderation is good as well.
Audio and Linux has been back and forth a hit or miss in my 15+ years...we just do the best we can.

---

### Post by dangillmor on 2023-08-02
Yes, it's running:

&#9679; pipewire.service - PipeWire Multimedia Service
     Loaded: loaded (/usr/lib/systemd/user/pipewire.service; disabled; vendor preset>
     Active: active (running) since Tue 2023-08-01 18:21:20 PDT; 19h ago
TriggeredBy: &#9679; pipewire.socket
   Main PID: 159330 (pipewire)
      Tasks: 3 (limit: 38026)
     Memory: 6.6M
        CPU: 72ms
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/pipewire.se>
             &#9492;&#9472;159330 /usr/bin/pipewire

---

### Post by #&amp;thj^% on 2023-08-03
How is the sound issue now? (with video's)

---

### Post by dangillmor on 2023-08-03
Videos don't play until I kill the pipewire process, which immediately respawns, requiring me to kill it again before I can play another video. Just bonkers.

---

### Post by #&amp;thj^% on 2023-08-03
Pipewire is a touchy install, will you take a look here: [https://gist.github.com/the-spyke/2de98b22ff4f978ebf0650c90e82027e?permalink_comment_id=4321083](https://gist.github.com/the-spyke/2de98b22ff4f978ebf0650c90e82027e?permalink_comment_id=4321083)
Maybe follow that install method, also in that link is a PPA that provides some missing codecs. (License issues)
The PPA is your choice but I strongly recommend it for completeness.
```
apt policy pipewire
pipewire:
  Installed: 0.3.65-4~glasgall1
  Candidate: 0.3.65-4~glasgall1
  Version table:
 *** 0.3.65-4~glasgall1 500
        500 https://ppa.launchpadcontent.net/aglasgall/pipewire-extra-bt-codecs/ubuntu lunar/main amd64 Packages
        100 /var/lib/dpkg/status
     0.3.65-3 500
        500 http://us.archive.ubuntu.com/ubuntu lunar/main amd64 Packages

```
I'll keep checking in on your progress with it. ;)
Also would mind telling me the Video App used, VLC Mplayer MVP?

---

### Post by ajgreeny on 2023-08-03
I'm not sure if this will help (I suspect not) but on my Xubuntu 22.04 running the command ***ps aux | grep pipewire*** show two processes running
```
128:128:user      1732  0.0  0.0  39848  4660 ?        Ssl  Jul28   0:00 /usr/bin/pipewire
129:129:user      1733  0.0  0.0  23612  4224 ?        Ssl  Jul28   0:00 /usr/bin/pipewire-media-session
```
If you run the same command and get the same output try stopping each process or both to see if that helps.
PS:
I have no problems on either of my machines with sound output so I may be leading you up a bad path with this suggestion.

---

### Post by #&amp;thj^% on 2023-08-03
On Lunar 23.04 and XFCE DE:
```
ps aux | grep pipewire
me          5046  0.0  0.0  47744 12160 ?        S<sl 10:29   0:00 /usr/bin/pipewire
me          5050  0.0  0.0  29428  9092 ?        S<sl 10:29   0:00 /usr/bin/pipewire-pulse
me        117139  0.0  0.0   9072  2304 pts/1    S+   11:55   0:00 grep pipewire
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>

```
ajgreeny are you running it globally or user called? Mine is the later.

---

### Post by ajgreeny on 2023-08-03
Not sure what you mean by "globally" but I don't start it manually, it starts with the system at boot as far as I'm aware.

I do not have **pipewire-pulse** installed at all so I presume it is not a default in 22.04

---

### Post by #&amp;thj^% on 2023-08-03
Easy to see which one with:
```
systemctl status pipewire
Unit pipewire.service could not be found.
```
```

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> systemctl status pipewire --user
&#9679; pipewire.service - PipeWire Multimedia Service
     Loaded: loaded (/usr/lib/systemd/user/pipewire.service; enabled; preset: e>
     Active: active (running) since Thu 2023-08-03 10:29:08 MDT; 1h 46min ago
TriggeredBy: &#9679; pipewire.socket
   Main PID: 5046 (pipewire)
      Tasks: 2 (limit: 18733)
     Memory: 4.5M
        CPU: 49ms
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/pipewi>
             &#9492;&#9472;5046 /usr/bin/pipewire

```
The reason i ask is it just might help here. :)

---

### Post by ajgreeny on 2023-08-03
OK- here you go
```
systemctl status pipewire
Unit pipewire.service could not be found.
```
```
systemctl status pipewire --user
&#9679; pipewire.service - PipeWire Multimedia Service
     Loaded: loaded (/usr/lib/systemd/user/pipewire.service; enabled; vendor preset: enabled)
     Active: active (running) since Fri 2023-07-28 19:11:57 BST; 6 days ago
TriggeredBy: &#9679; pipewire.socket
   Main PID: 1732 (pipewire)
      Tasks: 2 (limit: 9325)
     Memory: 1.7M
        CPU: 81ms
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/pipewire.service
             &#9492;&#9472;1732 /usr/bin/pipewire

Jul 28 19:11:57 Xubuntu-2204 systemd[1725]: Started PipeWire Multimedia Service.
```

---

### Post by #&amp;thj^% on 2023-08-03
And you probably know with that, it's user called.
Thanks ajgreeny ;)

---

### Post by ajgreeny on 2023-08-03
Yes, user-called but not manually, it starts at session startup but is not listed in the Application Autostart list.

---

### Post by #&amp;thj^% on 2023-08-03
> **ajgreeny said:**
> Yes, user-called but not manually, it starts at session startup but is not listed in the Application Autostart list.

Agreed your install went very well then by all appearance using the "--user" instead of without the "--user" flag which would install Global.
Oh My this poor thread, i can see the OP's head just a spinning, trying to make sense of it all.

---

### Post by ajgreeny on 2023-08-03
Mine is also spinning a bit as I am no expert in sound nor sound problems as my sound systems have always worked right after installing the OS.

Am I just lucky that I have simple hardware using Intel sound systems?

---

### Post by #&amp;thj^% on 2023-08-03
> **ajgreeny said:**
> 
Am I just lucky that I have simple hardware using Intel sound systems?

Yes, you have a very good head for this, New hardware is always a hit or miss, and providing the kernel team has the drivers to go along with it.

---

### Post by #&amp;thj^% on 2023-08-04
> **dangillmor said:**
> Videos don't play until I kill the pipewire process, which immediately respawns, requiring me to kill it again before I can play another video. Just bonkers.

@  dangillmor for some reason the firmware dose not get installed by default please check if installed.
```
apt policy firmware-sof-signed

```
It is needed for X1 Carbons, and a reboot.

---

### Post by dangillmor on 2023-08-12
No change; have to kill the process every time.

---

### Post by dangillmor on 2023-08-12
Both show up after reboot. I kill both, and the first keeps restarting.

---

### Post by dangillmor on 2023-08-12
At this point I'm trying to remove it, not install it! 

This occurs with pretty much all videos including streaming.

---

### Post by #&amp;thj^% on 2023-08-12
> **dangillmor said:**
> At this point I'm trying to remove it, not install it! 

This occurs with pretty much all videos including streaming.
Nothing will change, but as you wish:
```
systemctl --user unmask pulseaudio
systemctl --user --now disable pipewire-media-session.service
systemctl --user --now disable pipewire pipewire-pulse
systemctl --user --now enable pulseaudio.service pulseaudio.socket
```
Now this one be very careful about what is removed, watch it close.
```

sudo apt remove pipewire-audio-client-libraries pipewire
```
The above code might not be nessacary.
I'm on a XFCE4 session here is a preview of what take place with the single line of code:
```
sudo apt remove pipewire-audio-client-libraries pipewire -s
[sudo] password for me: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libpipewire-0.3-modules libwireplumber-0.4-0 pipewire-bin
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  pipewire pipewire-alsa pipewire-audio-client-libraries pipewire-jack
  pipewire-pulse wireplumber
0 upgraded, 0 newly installed, 6 to remove and 1 not upgraded.
Remv pipewire-pulse [0.3.65-4~glasgall1]
Remv pipewire-audio-client-libraries [0.3.65-4~glasgall1]
Remv pipewire-jack [0.3.65-4~glasgall1]
Remv pipewire [0.3.65-4~glasgall1] [wireplumber:amd64 pipewire-alsa:amd64 ]
Remv pipewire-alsa [0.3.65-4~glasgall1] [wireplumber:amd64 ]
Remv wireplumber [0.4.13-1]

```

---

### Post by dangillmor on 2023-08-13
Definitely not using that last command, because here's what will happen:

The following packages will be REMOVED:
  gdm3 gnome-control-center gnome-remote-desktop gnome-session gnome-shell
  gnome-shell-extension-appindicator gnome-shell-extension-desktop-icons-ng
  gnome-shell-extension-ubuntu-dock gstreamer1.0-pipewire pipewire
  pipewire-bin pipewire-pulse ubuntu-desktop ubuntu-desktop-minimal
  ubuntu-session wireplumber
0 upgraded, 0 newly installed, 16 to remove and 0 not upgraded.
After this operation, 15.5 MB disk space will be freed.
Do you want to continue? [Y/n] n
Abort.

Removing Pipewire (on this machine, at any rate) wipes out lots of gnome stuff, too...

---

### Post by #&amp;thj^% on 2023-08-13
> **dangillmor said:**
> Definitely not using that last command, because here's what will happen:

The following packages will be REMOVED:
  gdm3 gnome-control-center gnome-remote-desktop gnome-session gnome-shell
  gnome-shell-extension-appindicator gnome-shell-extension-desktop-icons-ng
  gnome-shell-extension-ubuntu-dock gstreamer1.0-pipewire pipewire
  pipewire-bin pipewire-pulse ubuntu-desktop ubuntu-desktop-minimal
  ubuntu-session wireplumber
0 upgraded, 0 newly installed, 16 to remove and 0 not upgraded.
After this operation, 15.5 MB disk space will be freed.
Do you want to continue? [Y/n] n
Abort.

Removing Pipewire (on this machine, at any rate) wipes out lots of gnome stuff, too...
Yep That's why the warning.
I'm a bit confused by this  "Removing Pipewire (on this machine," I don't recall that as one of suggestions, if your referring to dropping in Puseaudio for pipewire, then that part is all it will do. They are merely session managers for audio related.
Please clarify?
At any rate a well thought bug-report might help get things looked at and a possible fix.

---

### Post by dangillmor on 2023-08-14
I'm pretty lost at this point, and will take your suggestion (to try a bug report). I appreciate everyone's feedback.

---

