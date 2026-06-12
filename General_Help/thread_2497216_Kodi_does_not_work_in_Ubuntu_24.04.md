---
title: "Kodi does not work in Ubuntu 24.04"
date: 2024-04-27
forum: General Help
---

### Post by elpere31 on 2024-04-27
Hello Good morning:

Does kodi work in ubuntu 24.04?

I have tried and it is imposible.... any addon works ok...

thanks you

---

### Post by TheFu on 2024-04-27
Welcome to the bleeding edge.  

Did you upload the kodi logs to the Kodi website as suggested to get help there?
[https://forum.kodi.tv/showthread.php?tid=288153](https://forum.kodi.tv/showthread.php?tid=288153)   thread explains.

---

### Post by hong-xu on 2024-04-29
Did you install from the PPA? [https://kodi.wiki/view/HOW-TO:Install_Kodi_for_Linux?https=1#Installing_Kodi_on_Ubuntu-based_distributions_with_Team_Kodi_PPA](https://kodi.wiki/view/HOW-TO:Install_Kodi_for_Linux?https=1#Installing_Kodi_on_Ubuntu-based_distributions_with_Team_Kodi_PPA)

The Kodi package in the Ubuntu default repo is in the universe component, which is not supported by neither [Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu") nor Kodi officially.

---

### Post by TheFu on 2024-04-29
+1 on using the PPA!  Good catch Hong-Xu.

---

### Post by irbyjm on 2024-04-30
Team Kodi has officially announced their retirement of the PPA:
[https://kodi.tv/article/ubuntu-team-kodi-ppa-officially-retired/](https://kodi.tv/article/ubuntu-team-kodi-ppa-officially-retired/)

And per the HOW-TO:
[COLOR=#202122][FONT=sans-serif]"Please note that currently the Team Kodi PPA is not maintained due to the previous sole maintainer stepping away from the responsibility.F[/FONT][/COLOR][COLOR=#202122][FONT=sans-serif]or now the only options are building from source, using Flatpak or a distro such as Debian which includes Kodi in their distribution."[/FONT][/COLOR][COLOR=#202122][FONT=sans-serif]
[/FONT][/COLOR]
[COLOR=#202122][FONT=sans-serif]I don't think the PPA has been usable since Kinetic. I see Wolfgang pushed some changes a couple of weeks ago, but they were for Jammy and Focal.
[/FONT][/COLOR]

---

### Post by TheFu on 2024-04-30
I don't actually use Kodi directly.  I run OSMC (a specialized Kodi install) on a Raspberry Pi3/Pi4.  Works great almost always.

---

### Post by #&amp;thj^% on 2024-04-30
Kodi here works just as good as it ever has:
```
 apt policy kodi
kodi:
  Installed: 2:20.5+dfsg-1build2
  Candidate: 2:20.5+dfsg-1build2
  Version table:
 *** 2:20.5+dfsg-1build2 500
        500 http://us.archive.ubuntu.com/ubuntu noble/universe amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by jeremielapuree on 2024-05-01
Unfortunately this bug is well documented (and for commenters saying it does not exist, please refrain to tell such things)
Here is the issue in Kodi github: [https://github.com/xbmc/xbmc/issues/24069](https://github.com/xbmc/xbmc/issues/24069)

Since Ubuntu Noble uses Python 3.12, we are facing to the problem. The solution: noble is updated to use another python version (I don't believe it will happen)
Better solution; Universe repo update to Kodi Omega (unfortunately since Noble is LTS, I don't believe it will happen too)

So, we will have to wait Ubuntu 24.10 for a working deb Kodi in Ubuntu

Otherwise, you can download flatpak Omega kodi in the kodi official site :sad::sad: .

---

### Post by gezzer2 on 2024-05-01
if you install synaptic from the app centre its a deb file not a snap.
kodi is available from there ..

---

### Post by MAFoElffen on 2024-05-01
@TheFu --
> **TheFu said:**
> *"Works great almost always."*
Absolutely maybe? (LOL) 

Thank you. I needed something like that this morning...

---

### Post by TheFu on 2024-05-01
> **MAFoElffen said:**
> @TheFu --

Absolutely maybe? (LOL) 

Thank you. I needed something like that this morning...

Kodi can be a complex system. It is tied to specific hardware, nearly unlimited inputs, and 500 possible addons.  If you happen to have an addon that is having issues, then that can take a week to get fixed by the addon team.  If you don't use an addon with complexities and your material is all standard, then it will always work, as far as you know.

Sometimes with a new Kodi release, the player settings might need some tweaks to get everything perfect.  For example, I've had audio-sync issues crop up that needed some playback tweaks.  And my hardware never plays VP9 well, so I have jellyfin transcode it, always.  Without jellyfin, the only answer would be to transcode from VP9 to some other well supported, video codec like h.265, h.264 or MPEG2.  In theory, VP9 and h.265 should both be supported, but that isn't the real world.  h.265 works perfectly. VP9, stutters and sometimes locks up.

So, almost always, Kodi works.

Every month, there's a new OSMC release.  I try to wait a few weeks for early issues to be resolved.  Sometimes, I'm not paying attention and get unlucky.  Usually, nothing bad happens and all is fine.  During busy times of year, I specially do not patch my OSMC systems to avoid issues and family trauma.

---

### Post by buisteric on 2024-06-19
> **irbyjm said:**
> Team Kodi has officially announced their retirement of the PPA:
[https://kodi.tv/article/ubuntu-team-kodi-ppa-officially-retired/](https://kodi.tv/article/ubuntu-team-kodi-ppa-officially-retired/)

And per the HOW-TO:
[COLOR=#202122][FONT=sans-serif]"Please note that currently the Team Kodi PPA is not maintained due to the previous sole maintainer stepping away from the responsibility.F[/FONT][/COLOR][COLOR=#202122][FONT=sans-serif]or now the only options are building from source, using Flatpak or a distro such as Debian which includes Kodi in their distribution."[/FONT][/COLOR][COLOR=#202122][FONT=sans-serif]
[/FONT][/COLOR]
[COLOR=#202122][FONT=sans-serif]I don't think the PPA has been usable since Kinetic. I see Wolfgang pushed some changes a couple of weeks ago, but they were for Jammy and Focal.
[/FONT][/COLOR]

Rebuilding from source never never works for me. Getting errors all the times, takes me days to fix the errors, and I know I'd have to redo it each time I want to upgrade Kodi. Ubuntu has Snap, not Flatpak, so using the Flatpak KODI is not a good option as well. So the only solution seems to switch distribution, which is super boring to do, requires to reconfigure too much stuff. Seems Kodi will be a dead end for me then.

---

### Post by buisteric on 2024-06-19
> **jeremielapuree said:**
> Unfortunately this bug is well documented (and for commenters saying it does not exist, please refrain to tell such things)
Here is the issue in Kodi github: [https://github.com/xbmc/xbmc/issues/24069](https://github.com/xbmc/xbmc/issues/24069)

Since Ubuntu Noble uses Python 3.12, we are facing to the problem. The solution: noble is updated to use another python version (I don't believe it will happen)
Better solution; Universe repo update to Kodi Omega (unfortunately since Noble is LTS, I don't believe it will happen too)

So, we will have to wait Ubuntu 24.10 for a working deb Kodi in Ubuntu

Otherwise, you can download flatpak Omega kodi in the kodi official site :sad::sad: .

Python versions are supposed to be backward compatible with each other. If Ubuntu comes with Python 3.12, then Python code running on older Python versions should run on 3.12. If something is broken, that is likely a native library that doesn't compile well for Python 3.12. Rebuilding from source will just exhibit that compilation error and not work. Flatpak won't work either as Ubuntu comes with Snap. So that pretty much means Kodi is now incompatible with Ubuntu and requires switching Linux distribution. Keep in mind Kodi works out of the box on Android and Windows, which one again pushes Linux back. Most people will not scratch their head with this and just switch to Windows or, even worse, buy a Mac and be stuck with even more vendor lock in.

---

### Post by TheFu on 2024-06-19
```
$ lsb_release -d
Description:    Debian GNU/Linux 11 (bullseye)

$ python --version
Python 3.9.2

$ uname -a
Linux pi4 5.15.92-1-osmc #1 SMP PREEMPT Tue Jul 25 00:03:42 UTC 2023 aarch64 GNU/Linux

```

Is what my main OSMC box has. Not that it is helpful to anyone.

My setup has Jellyfin as a media server on an Ubuntu 20.04 server where all media is stored and OSMC running on R-Pi4 and R-Pi3 hardware. The OSMC systems have a Jellyfin addon that gets everything from the Jellyfin server.  I also have jellyfin running on a few Android tablets and my phone.  These can be either controllers or players (in DLNA terms, "renderers").  When traveling, a tablet with a VPN connection back home allows access to all remote media with hidef media transcoded down to 480p resolutions to be nicer with limited bandwidth over the internet.

Why Jellyfin?
[LIST]
[*]Transcoding from video codecs that aren't supported by the player hardware.
[*]Jellyfin supports audio formats/containers that other, "popular" media servers completely ignore.  Vorbis/ogg, Opus/ogg, and FLAC.
[*]Jellyfin supports different users, so each user can separately track what they've seen or haven't seen.
[*]Jellyfin knows, regardless of client player device, what media has been seen already. It knows that I'm one Episode 21 of season 3 and regardless of the client, that will be presented as the next episode to be shown.
[*]Jellyfin can be used as the server, controller and player platform.
[*]Jellyfin supports OTA TV recording if you have one of the specific network TV tuner devices on your network.  I have an HDHR-Quad connected to an attic antenna to watch/record local channels.  There are 4 tuners and those are available to any computing device on the LAN as needed. My specific setup gets weekly TV schedule data for free and creates a grid of what is on, with automatic recording of shows that I've denoted to record by title, title+channel, or title+channel+approx time.  In my part of the world, typically gaining access to schedule data is a $35/yr subscription.  I understand that other parts of the world don't have to pay for schedule data and I'm jealous.
[/LIST]

Why OSMC?
[LIST]
[*]OSMC is a custom build of Kodi for specific hardware platforms.  
[*]It is specifically designed to work with limited CPUs and the exact GPU provided by each platform.
[*]The OSMC player experience is 10x better than the Jellyfin player interface and 1000x better than the Plex player interface. Clearly this is subjective, but when plex removed the subtitles if pause was pressed, I knew plex's client was useless.
[*]The OSMC support team is extremely helpful. The head developer is right there to answer questions.  It is like having direct access to Linus for our bonehead Linux questions. That just doesn't happen most places.  For critical issues, he can provide workarounds or a custom patch fairly quick and the fix will be in the next release.
[*]The head developer understands prioritization.  For example, Debian 12 isn't the base OS because there are other moving parts in the Kodi and OSMC ecosystems.  This generally prevents overzealous upgrades making our spouses and kids, er, .... unhappy.
[/LIST]

---

### Post by jasonxoc on 2024-06-25
I gave up trying to install it from packages / flatpak etc. I just compiled it and pointed it to python3.10 with -DPYTHON_VER=3.10 and -DPYTHON_DIR=/usr/local/lib/python3.10  

Followed: github.com/xbmc/xbmc/blob/master/docs/README.Linux.md to build

I had this other issue with the installer not liking my version of Exiv2 … Apparently the version that ubuntu24.04 has is > the version it wants… it works fine though. I just edited cmake/modules/FindExiv2 file 

Note: DONT COPY/PASTE THIS. I typed it in, it’s not copied / pasted… so make your own changes 

Around line 60ish
if((exiv2_VERSION VERSION_LESS ${${MODULE}_VER} AND ENABLE_INTERNAL_EXIV2) OR ((CORE_SYSTEM_NAME STREQUAL linux OR CORE_SYSTEM_NAME STREQUAL freebsd) AND ENABLE_INTERNAL_EXIV2)) 
  buildexiv2()
else()
  buildexiv2()
endif()

Also the build failed on xbmc/build/exiv2/src/exiv2/src/futils.cpp 

I just added: 
#include <cstdint> 
in the standard includes and it built fine… at the top of the file.. around line 15ish
It’s what the compiler suggested to do and it works fine. 

Compiled version runs perfectly… actually it runs way faster than kodi has ever run.

---

