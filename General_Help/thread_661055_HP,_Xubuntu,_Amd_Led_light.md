---
title: "HP, Xubuntu, Amd: Led light"
date: 2008-01-07
forum: General Help
---

### Post by Peter Sommer-Larsen on 2008-01-07
Hi.
I have been messing a bit around with led light controlling because i would like
one of my leds to blink when i receive an email.

I have found out something about how to control the wireless network led in
/etc/acpi/start.d/60-asus-wireless-led.sh which is a script looking like this:

```
#!/bin/sh
. /usr/share/acpi-support/state-funcs
if isAnyWirelessPoweredOn ; then
    setLEDAsusWireless 1
else
    setLEDAsusWireless 0
fi
```

The state-funcs file look like this:
```

#!/bin/sh
# Paul Sladen, 2006-03-28, 2007-03-26
# Library functions to check/change status of wireless

# Return 0 if there is, allowing you to write   if isAnyWirelessPoweredOn; then ...
isAnyWirelessPoweredOn()
{
    for DEVICE in /sys/class/net/* ; do
	if [ -d $DEVICE/wireless -a -r $DEVICE/device/power/state ] ; then
	    # If any of the wireless devices are turned on then return success
	    if [ "`cat $DEVICE/device/power/state`" -eq 0 ] ; then
		# Check if 'rf_kill' disagrees
		if [ -r $DEVICE/device/rf_kill ] ; then
		    if [ "`cat $DEVICE/device/rf_kill`" -eq 0 ] ; then
			# And rf_kill has the radio on
			return 0
		    fi
		else
		    return 0
		fi
	    fi
	fi
    done
    # otherwise return failure
    return 1
}

# Takes no parameters, toggles all wireless devices.
# TODO: Should possible toggle all wireless devices to the state of the first one.
# Attempts to use 'rf_kill' first, and then tries 'power/state', though that
# will fail on >=2.6.18 kernels since upstream removed the functionality...
toggleAllWirelessStates()
{
    for DEVICE in /sys/class/net/* ; do
	if [ -d $DEVICE/wireless ] ; then
	    # $DEVICE is a wireless device. Check if it's powered on:
	    ON=0
	    OFF=1  # 1 for rf_kill, 2 for power/state
	    for CONTROL in $DEVICE/device/rf_kill $DEVICE/device/power/state ; do
		if [ -w $CONTROL ] ; then
		    # We have a way of controlling the device, lets try
		    if [ "`cat $CONTROL`" = 0 ] ; then
			# It's powered on. Switch it off.
			if echo -n $OFF > $CONTROL ; then 
			    break
			else
			    OFF=2 # for power/state, second time around
			fi
		    else
			# It's powered off. Switch it on.
			if echo -n $ON > $CONTROL ; then
			    break
			fi
		    fi
		fi
	    done
	fi
    done
}

# Pass '1' to blink suspending LED and '0' to stop LED
setLEDThinkpadSuspending()
{
    action=`test "$1" -ne 0 && echo blink || echo off`
    test -w /proc/acpi/ibm/led && echo -n 7 "$action" > /proc/acpi/ibm/led
}

# Pass '1' to light LED and '0' to dark LED
setLEDAsusWireless()
{
    action=`test "$1" -ne 0 && echo 1 || echo 0`
    test -w /proc/acpi/asus/wled && echo -n "$action" > /proc/acpi/asus/wled
}

```

As it can be seen the script tries to control a file in the dir;
/proc/acpi/ibm/led
Since I haven't got an IBM i don't have this dir.

So is it only possible to control leds with IBM computers or what?
Guess its normally a hardware specific property. 

Thx.
Sommer

---

### Post by Peter Sommer-Larsen on 2008-01-07
By the way my computer is a HP Pavilion zv6000.
And next time I will buy an IBM with a Nvidia card :guitar:

---

### Post by Peter Sommer-Larsen on 2008-01-08
...

---

