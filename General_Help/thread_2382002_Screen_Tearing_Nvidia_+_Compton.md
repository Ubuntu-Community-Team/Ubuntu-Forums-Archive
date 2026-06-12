---
title: "Screen Tearing Nvidia + Compton"
date: 2018-01-07
forum: General Help
---

### Post by mydroog on 2018-01-07
Hey everyone,

On my main PC, I am forced to use Nvidia's proprietary drivers, currently Version 384.90, due to having 2 graphics cards in SLI mode with 3 monitors hooked up to them.

In Firefox with smooth scrolling enabled, or during video playback, I get bad screen tearing. I've tried messing with every vsync option in compton with no success, I've tried launching compton with paramters -d :0 which should apply it across multiple monitors, I've tried running it as a background daemon and in the foreground, all with the same result.

Does anyone have advice on where to go from here?

---

### Post by yetimon_64 on 2018-01-07
I use XFCE but have never tried setting compton as the compositor as I use compiz. One thing springs to mind though on reading your post ... have you disabled the existing compositor in Xfce, ie. xfwm4 ? 

It may pay you to have a read of [[COLOR=#0000ff]--this site--[/COLOR]]("http://duncanlock.net/blog/2013/06/07/how-to-switch-to-compton-for-beautiful-tear-free-compositing-in-xfce/") as a guide that may possibly be of some help setting up and using compton. It is from 2013 so don't know if the ppa is necessary or not nowadays as compton is in the repositories here (on trusty 14.04) at least. Otherwise the guide linked seems reasonably comprehensive at a glance. Good luck, yeti.

---

### Post by mydroog on 2018-01-07
> **yetimon_64 said:**
> I use XFCE but have never tried setting compton as the compositor as I use compiz. One thing springs to mind though on reading your post ... have you disabled the existing compositor in Xfce, ie. xfwm4 ? 

It may pay you to have a read of [[COLOR=#0000ff]--this site--[/COLOR]]("http://duncanlock.net/blog/2013/06/07/how-to-switch-to-compton-for-beautiful-tear-free-compositing-in-xfce/") as a guide that may possibly be of some help setting up and using compton. It is from 2013 so don't know if the ppa is necessary or not nowadays as compton is in the repositories here (on trusty 14.04) at least. Otherwise the guide linked seems reasonably comprehensive at a glance. Good luck, yeti.

I have disabled it, and yes I started from that guide. I followed it perfectly, and I tried manipulating the config file for different vsync settings, which didn't result in anything.

Why do you use compiz? I might consider using that instead if it works better

---

### Post by mydroog on 2018-01-07
Here is my current configuration for Compton

```


#################################
#
# Backend
#
#################################

# Backend to use: "xrender" or "glx".
# GLX backend is typically much faster but depends on a sane driver.
backend = "glx";

#################################
#
# GLX backend
#
#################################

glx-no-stencil = true;

# GLX backend: Copy unmodified regions from front buffer instead of redrawing them all.
# My tests with nvidia-drivers show a 10% decrease in performance when the whole screen is modified,
# but a 20% increase when only 1/4 is.
# My tests on nouveau show terrible slowdown.
# Useful with --glx-swap-method, as well.
glx-copy-from-front = false;

# GLX backend: Use MESA_copy_sub_buffer to do partial screen update.
# My tests on nouveau shows a 200% performance boost when only 1/4 of the screen is updated.
# May break VSync and is not available on some drivers.
# Overrides --glx-copy-from-front.
# glx-use-copysubbuffermesa = true;

# GLX backend: Avoid rebinding pixmap on window damage.
# Probably could improve performance on rapid window content changes, but is known to break things on some drivers (LLVMpipe).
# Recommended if it works.
# glx-no-rebind-pixmap = true;


# GLX backend: GLX buffer swap method we assume.
# Could be undefined (0), copy (1), exchange (2), 3-6, or buffer-age (-1).
# undefined is the slowest and the safest, and the default value.
# copy is fastest, but may fail on some drivers,
# 2-6 are gradually slower but safer (6 is still faster than 0).
# Usually, double buffer means 2, triple buffer means 3.
# buffer-age means auto-detect using GLX_EXT_buffer_age, supported by some drivers.
# Useless with --glx-use-copysubbuffermesa.
# Partially breaks --resize-damage.
# Defaults to undefined.
glx-swap-method = "undefined";

#################################
#
# Shadows
#
#################################

# Enabled client-side shadows on windows.
shadow = true;
# Don't draw shadows on DND windows.
no-dnd-shadow = true;
# Avoid drawing shadows on dock/panel windows.
no-dock-shadow = true;
# Zero the part of the shadow's mask behind the window. Fix some weirdness with ARGB windows.
clear-shadow = true;
# The blur radius for shadows. (default 12)
shadow-radius = 5;
# The left offset for shadows. (default -15)
shadow-offset-x = -5;
# The top offset for shadows. (default -15)
shadow-offset-y = -5;
# The translucency for shadows. (default .75)
shadow-opacity = 0.5;

# Set if you want different colour shadows
# shadow-red = 0.0;
# shadow-green = 0.0;
# shadow-blue = 0.0;

# The shadow exclude options are helpful if you have shadows enabled. Due to the way compton draws its shadows, certain applications will have visual glitches
# (most applications are fine, only apps that do weird things with xshapes or argb are affected).
# This list includes all the affected apps I found in my testing. The "! name~=''" part excludes shadows on any "Unknown" windows, this prevents a visual glitch with the XFWM alt tab switcher.
shadow-exclude = [
    "! name~=''",
    "name = 'Notification'",
    "name = 'Plank'",
    "name = 'Docky'",
    "name = 'Kupfer'",
    "name = 'xfce4-notifyd'",
    "name *= 'VLC'",
    "name *= 'compton'",
    "name *= 'Chromium'",
    "name *= 'Chrome'",
    "name *= 'Firefox'",
    "class_g = 'Conky'",
    "class_g = 'Kupfer'",
    "class_g = 'Synapse'",
    "class_g ?= 'Notify-osd'",
    "class_g ?= 'Cairo-dock'",
    "class_g ?= 'Xfce4-notifyd'",
    "class_g ?= 'Xfce4-power-manager'"
];
# Avoid drawing shadow on all shaped windows (see also: --detect-rounded-corners)
shadow-ignore-shaped = false;

#################################
#
# Opacity
#
#################################

menu-opacity = 1;
inactive-opacity = 1;
active-opacity = 1;
frame-opacity = 1;
inactive-opacity-override = false;
alpha-step = 0.06;

# Dim inactive windows. (0.0 - 1.0)
# inactive-dim = 0.2;
# Do not let dimness adjust based on window opacity.
# inactive-dim-fixed = true;
# Blur background of transparent windows. Bad performance with X Render backend. GLX backend is preferred.
# blur-background = true;
# Blur background of opaque windows with transparent frames as well.
# blur-background-frame = true;
# Do not let blur radius adjust based on window opacity.
blur-background-fixed = false;
blur-background-exclude = [
    "window_type = 'dock'",
    "window_type = 'desktop'"
];

#################################
#
# Fading
#
#################################

# Fade windows during opacity changes.
fading = true;
# The time between steps in a fade in milliseconds. (default 10).
fade-delta = 4;
# Opacity change between steps while fading in. (default 0.028).
fade-in-step = 0.03;
# Opacity change between steps while fading out. (default 0.03).
fade-out-step = 0.03;
# Fade windows in/out when opening/closing
# no-fading-openclose = true;

# Specify a list of conditions of windows that should not be faded.
fade-exclude = [ ];

#################################
#
# Other
#
#################################

# Try to detect WM windows and mark them as active.
mark-wmwin-focused = true;
# Mark all non-WM but override-redirect windows active (e.g. menus).
mark-ovredir-focused = true;
# Use EWMH _NET_WM_ACTIVE_WINDOW to determine which window is focused instead of using FocusIn/Out events.
# Usually more reliable but depends on a EWMH-compliant WM.
use-ewmh-active-win = true;
# Detect rounded corners and treat them as rectangular when --shadow-ignore-shaped is on.
detect-rounded-corners = true;

# Detect _NET_WM_OPACITY on client windows, useful for window managers not passing _NET_WM_OPACITY of client windows to frame windows.
# This prevents opacity being ignored for some apps.
# For example without this enabled my xfce4-notifyd is 100% opacity no matter what.
detect-client-opacity = true;

# Specify refresh rate of the screen.
# If not specified or 0, compton will try detecting this with X RandR extension.
refresh-rate = 0;

# Set VSync method. VSync methods currently available:
# none: No VSync
# drm: VSync with DRM_IOCTL_WAIT_VBLANK. May only work on some drivers.
# opengl: Try to VSync with SGI_video_sync OpenGL extension. Only work on some drivers.
# opengl-oml: Try to VSync with OML_sync_control OpenGL extension. Only work on some drivers.
# opengl-swc: Try to VSync with SGI_swap_control OpenGL extension. Only work on some drivers. Works only with GLX backend. Known to be most effective on many drivers. Does not actually control paint timing, only buffer swap is affected, so it doesn’t have the effect of --sw-opti unlike other methods. Experimental.
# opengl-mswc: Try to VSync with MESA_swap_control OpenGL extension. Basically the same as opengl-swc above, except the extension we use.
# (Note some VSync methods may not be enabled at compile time.)
vsync = "opengl-swc";

# Enable DBE painting mode, intended to use with VSync to (hopefully) eliminate tearing.
# Reported to have no effect, though.
#DBE Can't Be Used With GLX Backend
#dbe = false;
# Painting on X Composite overlay window. Recommended.
paint-on-overlay = true;

# Limit compton to repaint at most once every 1 / refresh_rate second to boost performance.
# This should not be used with --vsync drm/opengl/opengl-oml as they essentially does --sw-opti's job already,
# unless you wish to specify a lower refresh rate than the actual value.
#sw-opti = false;

# Unredirect all windows if a full-screen opaque window is detected, to maximize performance for full-screen windows, like games.
# Known to cause flickering when redirecting/unredirecting windows.
# paint-on-overlay may make the flickering less obvious.
unredir-if-possible = true;

# Specify a list of conditions of windows that should always be considered focused.
focus-exclude = [ ];

# Use WM_TRANSIENT_FOR to group windows, and consider windows in the same group focused at the same time.
detect-transient = true;
# Use WM_CLIENT_LEADER to group windows, and consider windows in the same group focused at the same time.
# WM_TRANSIENT_FOR has higher priority if --detect-transient is enabled, too.
detect-client-leader = true;

#################################
#
# Window type settings
#
#################################

wintypes:
{
    tooltip =
    {
        # fade: Fade the particular type of windows.
        fade = true;
        # shadow: Give those windows shadow
        shadow = false;
        # opacity: Default opacity for the type of windows.
        opacity = 0.85;
        # focus: Whether to always consider windows of this type focused.
        focus = true;
    };
};


```

---

### Post by yetimon_64 on 2018-01-08
> **mydroog said:**
> ...
Why do you use compiz? I might consider using that instead if it works better

The cube and expo screen functionality more so than any video tearing issues basically. I got used to the "eye candy" style effects very early on in my time on ubuntu, about the time of hardy heron (8.04), and still use them to this day even with xfce.

 I have no idea if compiz will help your situation though; I am on a nvidia/intel hybrid graphics set up with the nvidia proprietary driver in use (version 340.102) and have never had any issues with tearing using compiz.

Edit: I should note that compiz nowadays is nowhere near as useful or as stable as it used to be, it may not be such a good option for you as it is pretty much outdated nowadays; I am a bit of a "die hard" for some of the older functions and do put up with a reduced usability as compared to when compiz was at its peak functionality. Cheers.

---

### Post by mydroog on 2018-01-09
Hey guys,

I feel like I've tried everything at this point, and nothing is working. Incredibly frustrating. I think it may be because I have different GPUs driving different monitors, going to try to connect them to one GPU and see if that helps shake things up.

Ultimately at this point, I'm having so many issues I switched to the default compositor in XFCE for the time being. Compton seems to slow down the system, especially visible when dragging windows quickly. I've been troubleshooting and trying to fix things for weeks and ultimately it's not better than the default compositor, so I've given up on it for the time being. 

Here is a rough log I'm keeping of things I've tried:

> 1)  Added "{ ForceCompositionPipeline = On }" to xorg.conf in /etc/X11/ --> Already Set
        --> Can also try to set FullForceCompositionPipeline, if required
        --> Still tears, tried to isntead use ForceFullCompositionPipeline
        --> Still Tears
        -->Left the option on


2) Launch compton with -d :0 arguments to enable on all screens, no change and still screen tearing. I always launch it with
"compton -b -d :0"

3)Try to set xrender as backend
    -> Worse tearing than even stock setup, somehow.

4) Tried changing the glx-swap-method of compton to 0, undefined, and -1. Don't notice any changes in any of them.

4) Tried every single compton setting for vsync. opengl-swc seems to work the best, works better than opengl. Other options don't work with my driver

5) Tried setting and removing "Sync to VBlank" and "Allow Flipping" in Nvidia settings on and off. Didn't notice any change. 
Ultimately, I left both of them off.

--> Noticed compton issue

19.22 ] error 9 (BadDrawable) request 14 minor 0 serial 81950 ("BadDrawable (invalid Pixmap or Window parameter)")
glx_bind_pixmap(0x0440298d): Failed to query Pixmap info.
win_paint_win(0x03c02d62): Failed to bind texture. Expect troubles.
win_paint_win(0x03c02d62): Missing painting data. This is a bad sign.
[    19.22 ] error 9 (BadDrawable) request 14 minor 0 serial 81964 ("BadDrawable (invalid Pixmap or Window parameter)")
[    19.22 ] error 4 (BadPixmap) request 54 minor 0 serial 81965 ("BadPixmap (invalid Pixmap parameter)")


When pressing the file/edit/search/etc button in mousepad. It either comes up as a large black square with the menu opened inside, or a weird transparent overlay over the menu.
Excluding mousepad from compton shading doesn't seem to help. Tried to recreate the issue after a restart but couldn't, however I frequently see the win_paint_win error in terminal

---

