---
title: "vncserver configuration problem"
date: 2007-01-07
forum: General Help
---

### Post by perlappuntu on 2007-01-07
First of all let me clarify my objective: be able to start simultaneous and independent vnc sessions for each user of the machine.  I'm having trouble configuring the vncserver with Ubuntu 7.10 (everything was fine with 7.06).  I'm successfully running the vncserver via xinetd (I followed the instructions described in forum by [Tichondrius et al.]("http://www.ubuntuforums.org/showthread.php?t=122402")) but this approach doesn't accomplish my objective because it restricts the vnc use to a single user.  if I try to start the vncserver (vncserver :66 -fp /usr/share/fonts/X11/misc) from a SSH session instead, once I connect via a vncviewer I get a pop-up window in gnome with the following message:

```
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correct
ly.

The last error message was:

Unable to determine the address of the message bus (try 'man dbus-launch' and 'm
an dbus-daemon' for help)

GNOME will still try to restart the Settings Daemon next time you log in.

```

Besides the error message the gnome doesn't look configured right, e.g. the screen resolution is not the one I set in vnc.conf.  Unfortunately I'm quite new to Linux and I need some help...


This is part of my SYSLOG (the one related to the event):

```
Jan  7 16:00:58 datacenter gconfd (dummy-5555): starting (version 2.16.0), pid 5
555 user 'dummy'
Jan  7 16:00:58 datacenter gconfd (dummy-5555): Resolved address "xml:readonly:/
etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jan  7 16:00:58 datacenter gconfd (dummy-5555): Resolved address "xml:readwrite:
/home/dummy/.gconf" to a writable configuration source at position 1
Jan  7 16:00:58 datacenter gconfd (dummy-5555): Resolved address "xml:readonly:/
etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jan  7 16:00:58 datacenter gconfd (dummy-5555): Resolved address "xml:readonly:/
var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jan  7 16:00:58 datacenter gconfd (dummy-5555): Resolved address "xml:readonly:/
var/lib/gconf/defaults" to a read-only configuration source at position 4
Jan  7 16:01:02 datacenter gconfd (dummy-5555): Resolved address "xml:readwrite:
/home/dummy/.gconf" to a writable configuration source at position 0
Jan  7 16:01:04 datacenter gnome-power-manager: (dummy) Critical error: This pro
gram cannot start until you start the dbus session service.  This is usually sta
rted automatically in X or gnome startup when you start a new session.
ran  7 16:03:33 datacenter gnome-power-manager: (dummy) Critical error: This pro
gram cannot start until you start the dbus session service.  This is usually sta
rted automatically in X or gnome startup when you start a new session.
Jan  7 16:07:22 datacenter gnome-power-manager: (dummy) Critical error: This pro
gram cannot start until you start the dbus session service.  This is usually sta
rted automatically in X or gnome startup when you start a new session.

```

This is my /etc/vnc.conf file

```
# /etc/vnc.conf written by Marcus Brinkmann. This file is in the Public Domain.
#
# This is the configuration file for the vncserver package.
# It is perl syntax, but only variable assignment is allowed.
# A semicolon will be added if missing.
# Every value has suitable defaults, so you probably don't need any file.
#
# This file will be sourced by `vncserver' and `vncpasswd'.
# After this file, $(HOME)/.vncrc will be sourced, so values can be
# overwritten on a per-user basis. If you want to reactivate the default
# value there, you have to specify an empty value. For example, $fontPath
# will set to the default value after
#
# $fontPath = "/foo";
# $fontPath = "";
#
# If you are missing something, please let me know.
# Marcus.Brinkmann@ruhr-uni-bochum.de

# System configuration
# --------------------
#
# This section contains entries that should be true for all users.

# $vncClasses should be the path to the java classes of server.
# $vncClasses = "/usr/share/vncserver";

# $XFConfigPath   can be set to the global XF86Config file. This will be
#                 parsed to gain default values for $fontPath and $colorPath.
#                 If you want to disable this feature, point it to an
#                 invalid file, "/foo" for example.
# $XFConfigPath = "/etc/X11/XF86Config";

# $fontPath should be a comma seperated list of fonts to be added to the font
#           path. If not specified, and $XFConfigPath is valid, vncserver
#           will read the $fontPath from there. If both are not set, the
#           default will apply.
# Example: $fontPath = "tcp/localhost:7100";     # would make vnc to use xfs.
# Example: $fontPath = "";
#	$fontPath .= "/usr/X11R6/lib/X11/fonts/misc/,";
# 	$fontPath .= "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled,";
# 	$fontPath .= "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled,";
# 	$fontPath .= "/usr/X11R6/lib/X11/fonts/Type1/,";
# 	$fontPath .= "/usr/X11R6/lib/X11/fonts/Speedo/,";
# 	$fontPath .= "/usr/X11R6/lib/X11/fonts/75dpi/,";
# 	$fontPath .= "/usr/X11R6/lib/X11/fonts/100dpi/,";
#	$fontPath .= "/usr/X11R6/lib/X11/fonts/freefont/,";
#	$fontPath .= "/usr/X11R6/lib/X11/fonts/sharefont/";
# I don't know what the default is, though.
$fontPath = "/usr/lib/X11/fonts/misc/"

# $colorPath should be the RGB file to be used by X. This can also be taken from
#            XF86Config file if specified by $XFConfigPath
# $colorPath = "/usr/X11R6/lib/X11/rgb";

# User configuration
# ------------------
#
# This section contains entries that may change from user to user.

# $vncUserDir contains the filename for the log files directory of Xvnc
#             (the server) and the viewers that are connected to it.
# $vncUserDir = "$ENV{HOME}/.vnc";
$vncUserDir = "$ENV{HOME}/.vnc";

# $vncPasswdFile contains the filename of the password file for Xvnc.
$vncPasswdFile = $vncUserDir . "/passwd";

# $vncStartup points to a script that will be started at the very beginning.
# $vncStartup = "/etc/X11/Xsession";
$vncStartup = $vncUserDir . "/xstartup";

# $xauthorityFile should be the path to the authority file that should be used
#                 by your vnc X server.
# $xauthorityFile = "$ENV{HOME}/.Xauthority";
$xauthorityFile = "$ENV{HOME}/.Xauthority";

# $defaultDesktopName should be set to the default name of the desktop.
#                     This can be changed at the command line with -name.
$defaultDesktopName = "Ubuntu";

# $geometry sets framebuffer width & height. Default will be calculated if
#           server is started from within a running X servers. Can be changed at
#           the commandline (-geometry). A fixed default will be used if
#           vncserver is not invoked in a running X session.
# Example:  $geometry ="640x480";
$geometry ="1360x768";

# $depth       sets the framebuffer color depth. Must be between 8 and 32.
# $pixelformat sets the default pixelformat.
#              The default will be calculated if none of both is specified
#              and when vncserver is called from within a running X servers.
#              Can be changed at the command line with option -depth.
#              A fixed default value will be used if vncserver is not
#              invoked in a running X session.
# Example:  $depth = "16";
#           $pixelformat = "rgb565";
$depth = "16";
$pixelformat = "rgb565";

# $getDefaultFrom sets the display from which you can query the default of
#                 the above three options, if you don't want to start vncserver
#                 from within a running X server. It will be added to the call
#                 of xdpyinfo.
#                 It is useful to get the default from the X server you will
#                 run xvncviewer in.
# Example:  $getDefaultFrom = "-display localhost:0"

# $rfbwait sets the maximum time in msec to wait for vnc client viewer.
# $rfbwait = "120000";

```

and this my ~/.vnc/xstartup file:

```
#!/bin/sh

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic -nowin &
exec gnome-session

```

---

### Post by Asos_Illusionist on 2007-01-16
can anybody give me one xstartup that boots up the kde not the gnome..?

---

