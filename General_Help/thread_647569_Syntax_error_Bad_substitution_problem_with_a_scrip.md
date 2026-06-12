---
title: "Syntax error: Bad substitution problem with a script"
date: 2007-12-22
forum: General Help
---

### Post by Muty-bg on 2007-12-22
Hi I have a problem with the ati scriptlet for the hibernate script(for tuxonice)

I'm getting this error when I try to run it:

/usr/local/share/hibernate/scriptlets.d/ati: 62: Syntax error: Bad substitution

Here is the whole scriptlet
```
# -*- sh -*-
# vim:ft=sh:ts=8:sw=4:noet

###
## Handles fglrx specifics:
## 1. Enables all connected monitors on resume.
## 2. Sets the X resolution to the minimum specified for connected monitors.
##
## Author: Pat Double <pat@patdouble.com>
###

AddConfigHandler ATIOptions
AddConfigHelp "ATIEnableMonitors <boolean>" "Enable all connected monitors on resume. If the resolution is specified for one or more of the enabled monitors, the X session will be set to the lesser resolution of those enabled."
AddConfigHelp "ATIMonitor_LCD width height" "Set the desired width and height for LCD."
AddConfigHelp "ATIMonitor_CRT1 width height" "Set the desired width and height for CRT1."
AddConfigHelp "ATIMonitor_CRT2 width height" "Set the desired width and height for CRT2."
AddConfigHelp "ATIMonitor_TMDS1 width height" "Set the desired width and height for TMDS1 (DVI)."
AddConfigHelp "ATIMonitor_TV width height" "Set the desired width and height for TV."

# Monitor constants
ATI_MONITOR_LCD=0
ATI_MONITOR_CRT1=1
ATI_MONITOR_CRT2=2
ATI_MONITOR_TV=3
ATI_MONITOR_TMDS1=3

ATIEnableMonitors() {

	# Find the aticonfig configuration program
	ATI_CONFIG="`which aticonfig 2>/dev/null`"
	[ -z "$ATI_CONFIG" ] && ATI_CONFIG="/opt/ati/bin/aticonfig"
	if [ ! -x "$ATI_CONFIG" ]; then
		vecho 0 "Could not find 'aticonfig'"
		return 1
	fi


	local connected_monitors enabled_monitors

	# Get current and enabled monitors
	connected_monitors=`$ATI_CONFIG --query-monitor | grep -i connect | cut -d : -f 2 | tr -d [:space:]`
	enabled_monitors=`$ATI_CONFIG --query-monitor | grep -i enable | cut -d : -f 2 | tr -d [:space:]`

	# Sanity check
	[ -z "$connected_monitors" ] && vecho 0 "No connected monitors? Aborting!" && return 0

	vecho 3 "Connected monitors: $connected_monitors    Enabled monitors: $enabled_monitors"

	# Don't do anything if there isn't any change
	[ "$connected_monitors" = "$enabled_monitors" ] && return 0

	# Change the enabled monitors
	vecho 1 "Enabling monitors $connected_monitors"
	# Give some time for the driver to complete the switch back to X
	sleep 3s
	$ATI_CONFIG --enable-monitor=$connected_monitors

	# Adjust the resolution if set
	local width height monindex
	width=0
	height=0
	for monitor in ${connected_monitors//,/ }; do
		[ $monitor = 'lvds' ] && monindex=$ATI_MONITOR_LCD
		[ $monitor = 'crt1' ] && monindex=$ATI_MONITOR_CRT1
		[ $monitor = 'crt2' ] && monindex=$ATI_MONITOR_CRT2
		[ $monitor = 'tv' ] && monindex=$ATI_MONITOR_TV
		[ $monitor = 'tmds1' ] && monindex=$ATI_MONITOR_TMDS1
		if [ $width -eq 0 -o ${ATI_MONITOR_WIDTH[monindex]} -lt $width ]; then
			width=${ATI_MONITOR_WIDTH[monindex]}
			height=${ATI_MONITOR_HEIGHT[monindex]}
		fi
	done

	if [ $width -ne 0 -a $height -ne 0 ]; then
		FindXServer || return 0
		vecho 1 "Setting resolution to $width x $height"
		# Give some time for the driver to complete the monitor switch
		sleep 3s
		su $XUSER -c "xrandr --size ${width}x${height}"
	fi
	
	return 0
}

ATIOptions() {
	case $1 in
		atienablemonitors)
			BoolIsOn "$1" "$2" || return 0
			[ -z "$ATI_MONITORS_HOOKED" ] || return 0
			ATI_MONITORS_HOOKED=1
			AddResumeHook 10 ATIEnableMonitors
			;;

		atimonitor_lcd)
			ATI_MONITOR_WIDTH[$ATI_MONITOR_LCD]=$2
			ATI_MONITOR_HEIGHT[$ATI_MONITOR_LCD]=$3
			;;

		atimonitor_crt1)
			ATI_MONITOR_WIDTH[$ATI_MONITOR_CRT1]=$2
			ATI_MONITOR_HEIGHT[$ATI_MONITOR_CRT1]=$3
			;;

		atimonitor_crt2)
			ATI_MONITOR_WIDTH[$ATI_MONITOR_CRT2]=$2
			ATI_MONITOR_HEIGHT[$ATI_MONITOR_CRT2]=$3
			;;

		atimonitor_tv)
			ATI_MONITOR_WIDTH[$ATI_MONITOR_TV]=$2
			ATI_MONITOR_HEIGHT[$ATI_MONITOR_TV]=$3
			;;

		atimonitor_tmds1)
			ATI_MONITOR_WIDTH[$ATI_MONITOR_TMDS1]=$2
			ATI_MONITOR_HEIGHT[$ATI_MONITOR_TMDS1]=$3
			;;
		*)
		return 1
	esac

	return 0
}

```

Line 62 is: for monitor in ${connected_monitors//,/ }; do

I can't really spot anything unusual. Any ideas?

Thanks for the help

---

### Post by hunt.topher on 2008-04-07
Just out of curiosity, try running a really simple script including substring manipulation like so:

[INDENT][B]#!/bin/bash

stringToSplit="thisisatest"
echo ${stringToSplit:3}[/B][/INDENT]

I'm suggesting this because Ubuntu gives me the same error any time I try to retrieve part of a string using the ${string1:position} approach - but only if it's in a script I'm trying to run, instead of just straight in the terminal.

I'm new to Linux scripting so I have no idea what to think about this. Is this an old approach? Is awk the "right" way to do the above? Any idea why the old way (the first way I found online) doesn't seem to work well in Ubuntu Gutsy?

---

