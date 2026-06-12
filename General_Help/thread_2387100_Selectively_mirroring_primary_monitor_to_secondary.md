---
title: "Selectively mirroring primary monitor to secondary?"
date: 2018-03-14
forum: General Help
---

### Post by wrybread on 2018-03-14
I have Lubuntu (but can switch to Ubuntu) running on a converted arcade cabinet, playing video games part time using the MAME emulator, and playing movies part time.

There's two monitors attached, each with different resolutions.

When a movie plays, I run two instances of mplayer, the second slaved to the first. It plays the movies fullscreen on both monitors and works great.

When I play games in the MAME emulator though, they show only on monitor 1. I'm wondering if there's some clever way to mirror the content of monitor 1 to monitor 2 temporarily in this case? A little lag would be fine since it's just for spectators. In Mac there's a utility called Siphon that can (I think) take the output from one monitor and pipe it to monitor 2. Or maybe there's a way to pipe the output of a monitor to mplayer and play that full screen? Or some other clever idea?

Thanks for any help.

---

### Post by dragonfly41 on 2018-03-14
I admit that this idea might not work since I don't have two monitors to play with to test it.
But I use a small tool .. X Tile .. to position multiple app windows on desktop.
I see that there is an option for monitor 1 and monitor 2 so this might work for you.

[https://www.giuspen.com/x-tile/](https://www.giuspen.com/x-tile/)

It is worth trying.

---

### Post by TheFu on 2018-03-14
If you are using 1 video card, **lxrandr**, xrandr, arandr are options.  I think there is a mirror or placement option. Not on my multi-monitor system now, so I can't check it now. Sorry.

BTW, this should work for movies too. No need to run multiple mpv instances (fork of mplayer).  However, the different resolutions might be an issue.  You can trivially make the resolutions match with the screen that is lower.

---

### Post by wrybread on 2018-03-14
>  You can trivially make the resolutions match with the screen that is lower.

But then it won't be fullscreen on both monitors.

One issue I avoided mentioning since it's already complicated: the second monitor is actually a projector. And this projector (maybe all projectors?) has a quirk: when the resolution changes, it reinitializes, causing flicker. So if possible I'd rather simply capture the activity on monitor 1 and pipe it to monitor 2, when needed.

---

### Post by wrybread on 2018-03-14
Aha, this is working! 

ffmpeg -loglevel panic -video_size 1680x1050 -framerate 25 -f x11grab -i :0.0+0,0 -f mpeg - | mplayer -quiet -cache 100 -screen 1 -fs -fixed-vo -

With that command everything on my primary monitor (with the 1680x1050 resolution) is displayed resized on my secondary monitor ("screen 1", which at the moment is 1024x768). Mplayer handles resizing it, so it's the max size possible.

There's a little bit of lag, which for my purposes is ok. Adjusting the -cache changes the lag, but I haven't been able to get rid of it entirely,. As of yet I'm not sure if the -framerate option in ffmpeg is optimal, or if the -fixed-vo option is necessary in mplayer. .

If anyone has any suggestions to refine that command, or an alternative method, very invited!

---

### Post by TheFu on 2018-03-14
**mpv** will use HW accel that mplayer doesn't out of the box.  Most people who check out mpv seem to switch.  Some good folks here turned me onto mpv about 18 months ago.  I've never looked back.  Had been using mplayer for about 10 yrs.

I have a projector, but it is driven by a r-pi, so only a single display.

I'm fairly certain that using lxrandr to set both systems to the same resolution and mirroring the display will work.  Can't see why it wouldn't - zero lag. Just make the primary 1024x768. 10 seconds to test. Zero risk.  Much lower GPU/CPU requirements.

---

### Post by wrybread on 2018-03-14
> I'm fairly certain that using lxrandr to set both systems to the same resolution and mirroring the display will work.

My two screens have different aspect ratios. And on one of my systems the primary screen is vertically oriented (1050x1680), since it's used to play classic video games like Ms. Pacman, making the difference even worse. 

MPV looks interesting, but another quirk in my system is that everything is controlled by joystick controllers. Mplayer has fantastic joystick support, I can assign different buttons to different actions, even on the fly (a different configuration for one of two instances of mplayer for example). According to this MPV doesn't support joystick input:

[https://github.com/mpv-player/mpv/issues/3320](https://github.com/mpv-player/mpv/issues/3320)

[https://github.com/mpv-player/mpv/issues/2678](https://github.com/mpv-player/mpv/issues/2678)

Not sure if that's changed though. 

And again, I know my use case if very obscure. MPV is a fantastic suggestion and I'll definitely be trying it out.

---

### Post by TheFu on 2018-03-14
Agreed.  Having a 9x16 vs a 16x10 is hard.  You definitely have some specific requirements.

I have used a 16x10 (1920x1200) and a 16x9 (1920x1080) dual monitor setup, mirrored, both at 720p resolutions. Not an issue. It works. I chose 720p to be compatible with other video equipment used here.  But your setup is vastly different.

---

