---
title: "I switched from Nouveau driver to the NVidia driver and now the colors are off"
date: 2023-06-15
forum: General Help
---

### Post by SpaceManJack on 2023-06-15
So to see how I got here please go here first and read up on my situation [https://ubuntuforums.org/showthread.php?t=2487684](https://ubuntuforums.org/showthread.php?t=2487684)

So I'm on 22.04LTS and I was using the Nouveau driver and everything was fine but just a few days ago I decided to go from my 24inch monitor to my 55 inch 4k TV and instantly the mouse movement felt slow and inaccurate so I came here to Ubuntu forums for help and someone said "Are you using the NVidia driver?"

No i was not using the NVidia driver so today I switched over to the NVidia driver and now my colors are off, white now looks like a grey, so when I go to youtube and put on a white screen the white looks kinda greyish.

 The source of the problem is X11 because when I switch back to the Nouveau driver the colors are ok again (Nouveau will automatically put on Wayland), or now listen, when I install the NVidia drivers and when I'm at the login screen there's a cog and that cog allows me to manually switch over to Wayland so I can use Wayland with NVidia drivers, so NVidia drivers with Wayland the colors are totally fine, so it's X11, X11 is the problem here (and just so you are aware, in 22.04LTS when you are using the NVidia driver it will automatically switch it to X11 because NVidia GPUs don't play nice with Wayland). So yeah I'm kinda stumped here. 

So the colors are fine if I use NVidia drivers with Wayland (I have to manually switch it to Wayland at the login screen), and the colors are fine if I switch back to Nouveau drivers (Nouveau drivers automatically turn on Wayland). So it seems X11 is the problem here.

Is there a way to fix the color issue here?

---

### Post by TheFu on 2023-06-16
I vaguely remember that the nvidia software package comes with a customization tool to handle color settings. Did you use that?  The program is something like **nvidia-settings**. From the manpage:
```
NAME
       nvidia-settings - configure the NVIDIA graphics driver

SYNOPSIS
       nvidia-settings [options]
       nvidia-settings [options] --no-config
       nvidia-settings [options] --load-config-only
       nvidia-settings [options] {--query=attr | --assign=attr=value} ...
       nvidia-settings [options] --glxinfo

       Options: [-vh] [--config=configfile] [-c ctrl-display]
                [--verbose={none | errors | deprecations | warnings | all}]
                [--describe={all | list | attribute_name}]

       attr has the form:
            DISPLAY/attribute_name[display_devices]

DESCRIPTION
       The nvidia-settings utility is a tool for configuring the NVIDIA graph&#8208;
       ics driver.  It operates by communicating with  the  NVIDIA  X  driver,
       querying and updating state as appropriate.  This communication is done
       via the NV-CONTROL, GLX, XVideo, and RandR X extensions.
...

```
It goes on with about 10 pgs of information.  These programs only work with the nvidia driver active.

There are a few other programs that start with nvidia* too.

---

