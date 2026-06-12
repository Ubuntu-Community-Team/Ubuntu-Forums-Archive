---
title: "How to detect if chrome is playing a video in fullscreen"
date: 2015-11-24
forum: General Help
---

### Post by fkervin on 2015-11-24
Hi all,

I've a problem with compton (the compositor I use in xubuntu)  and I need to disable it when Google Chrome is playing a video in fullscreen. I've write my problem in the [Compton thread]("http://ubuntuforums.org/showthread.php?t=2144468&page=2&p=13396111#post13396111").

I need an sh function that runs "killall compton" when google chrome start playing a video in fullscreen and also run "compton -b" when this video is closed or back from fullscreen to windowed mode?

Can this be done or I'm asking for something impossible?

Many thanks to all

Regards

---

### Post by ajgreeny on 2015-11-24
You can make application exceptions for some of the graphics properties that compton manages in the configuration file ~/.config/compton.conf which is worth making if you do not already have one for compton.  What problem do you see when using compton with chrome; that may help figure out what you could do.

Have a look at [https://github.com/chjj/compton/wiki/perf-guide](https://github.com/chjj/compton/wiki/perf-guide) which offers the following info:-
> If it&#8217;s only full-screen applications that have performance issues with compton running, --unredir-if-possible causes compton to unredirect the screen (thus with almost zero performance penalty) when there&#8217;s a full-screen window.

Here is a copy of my compton.conf file which has shadow exceptions for applications other than chrome (I use chromium, not chrome), but without knowing what problem you see it's difficult to know what might help.
```
backend = "glx";
paint-on-overlay = true;
glx-no-stencil = true;
glx-no-rebind-pixmap = true;
vsync = "opengl-swc"; 

# These are important. The first one enables the opengl backend. The last one is the vsync method. Depending on the driver you might need to use a different method.
# The other options are smaller performance tweaks that work well in most cases. 
# You can find the rest of the options here: https://github.com/chjj/compton/wiki/perf-guide, and here: https://github.com/chjj/compton/wiki/vsync-guide


# Shadow
shadow = true;			# Enabled client-side shadows on windows.
no-dock-shadow = true;		# Avoid drawing shadows on dock/panel windows.
no-dnd-shadow = true;		# Don't draw shadows on DND windows.
clear-shadow = true;		# Zero the part of the shadow's mask behind the window (experimental).
shadow-radius = 7;		# The blur radius for shadows. (default 12)
shadow-offset-x = -7;		# The left offset for shadows. (default -15)
shadow-offset-y = -7;		# The top offset for shadows. (default -15)
shadow-exclude = [
 "! name~=''",
 "n:e:Notification",
 "n:e:Plank",
 "n:e:Docky",
 "g:e:Synapse",
 "g:e:Kupfer",
 "g:e:Conky",
 "n:w:*Firefox*",
 "n:w:*Chrome*",
 "n:w:*Chromium*",
 "n:w:*VirtualBox*",
 "class_g ?= 'Notify-osd'",
 "class_g ?= 'Cairo-dock'",
 "class_g ?= 'Xfce4-notifyd'",
 "class_g ?= 'Xfce4-power-manager'"
];

# The shadow exclude options are helpful if you have shadows enabled. Due to the way compton draws its shadows, certain applications will have visual glitches 
# (most applications are fine, only apps that do weird things with xshapes or argb are affected). 
# This list includes all the affected apps I found in my testing. The "! name~=''" part excludes shadows on any "Unknown" windows, this prevents a visual glitch with the XFWM alt tab switcher.

# Fading
fading = true; # Fade windows during opacity changes.
fade-delta = 4; # The time between steps in a fade in milliseconds. (default 10).
fade-in-step = 0.03; # Opacity change between steps while fading in. (default 0.028).
fade-out-step = 0.03; # Opacity change between steps while fading out. (default 0.03).
#no-fading-openclose = true; # Fade windows in/out when opening/closing

detect-client-opacity = true; # This prevents opacity being ignored for some apps. For example without this enabled my xfce4-notifyd is 100% opacity no matter what.

# Window type settings
wintypes:
{
  tooltip = { fade = true; shadow = false; };
};
```

---

### Post by fkervin on 2015-11-25
Many thanks for your answer, ajgreeny,

The problem is quite simple, when I go fullscreen with compton enabled the video plays during 1-2 seconds and then image gets frozen while audio continues playback.

I've try lo launch conmpon using:

compton --config ~/.compton.conf --unredir-if-possible --shadow-exclude 'n:a:Conky' -b &
It seems that playback lasts a bit more than 1-2 seconds, but in the same way it gets hanged :(

How can I make compton ignore fullscreen videos on chrome?

Regards

---

### Post by fkervin on 2015-12-02
I still have this problem, I suppose anyone can help, can someone?

Regards and thanks

---

