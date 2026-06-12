---
title: "Laptop Doesn't Sleep/Suspend"
date: 2017-03-27
forum: General Help
---

### Post by webmanoffesto on 2017-03-27
I have a new HP ProBook 450 G3 15.6&#8243; Laptop. 

I installed Ubuntu 16.10 Gnome on it. I'm using a SSD (no spinning disk). The laptop doesn't Suspend (i.e. Suspend-to-RAM) when I shut the lid and carry it elsewhere. When I get to my destination either the laptop is hot or the battery is dead.

I know that shutting the lid can cause a number of different states (sleep, suspend, hibernate). I believe that what I want is correctly called Suspend-to-RAM (monitor off, and details saved to RAM for a speedy return to work). This laptop, on lid-close, shuts off the monitor but all else continues working.

When I call up "gnome-tweak-tool" the setttings appear to be correct (i.e. they tell the laptop to suspend-to-RAM when I close the lid) 
"When laptop lid is closed
- On Battery Power - Suspend
- When Plugged In - Suspend
Don't Suspend on Lid Cose - Off"
When I changed "Suspend" to "Hibernate" the laptop continued to do nothing except shut off the monitor when I close the lid.

How can I do that? I found some out of date posts on this but no solution yet. 
In Settings / Power I see "Power" and "Suspend and Power Button" but no place to specify action to occur on lid-close. I tried Gconf-Editor but I wasn't able to find the correct settings. 

Based on www DOT linux DOT com/news/how-suspe...op-under-linux
I think this is relevant
```
$ cat /sys/power/state
freeze mem disk
```

Seems relevant too: 
wwwDOTkernelDOTorg/doc/Documenta.../interfaceDOTtxt I read that
/sys/power/state is the system sleep state control file. it returns a list of supported sleep states, encoded as:
'freeze' (Suspend-to-Idle)
'standby' (Power-On Suspend)
'mem' (Suspend-to-RAM)
'disk' (Suspend-to-Disk)
====

$ dmesg
Shows me a long list of info, but I don't know what to look for. Could the "Unknown key pressed" be the sleep/hibernate button which the lid-close presses?
```
[158462.129003] atkbd serio0: Unknown key pressed (translated set 2, code 0x85 on isa0060/serio0).
[158462.129006] atkbd serio0: Use 'setkeycodes e005 <keycode>' to make it known.
[158514.654565] atkbd serio0: Unknown key pressed (translated set 2, code 0x85 on isa0060/serio0).
```
This looks helpful, "UnderstandingSuspend - Ubuntu Wiki"
wikiDOTubuntuDOTcom/UnderstandingSuspend

Contents of my "sleep_suspend.sh" file:
```
#!/bin/sh
# This script HANDLES the sleep or suspend button (does not TRANSLATE it). It
# is part of the *suspend* side of acpi-support, not the special keys
# translation side. If this script is called, it is assumed to be the result of
# a suspend key press that can also be heard by other parts of the system. The
# only time that it actually does something is when it is determined that no
# other parts of the system are listening (this is what the CheckPolicy call
# does).

test -f /usr/share/acpi-support/key-constants || exit 0

. /etc/default/acpi-support
. /usr/share/acpi-support/policy-funcs

CheckPolicy && exit 0

[ x$1 != xsleep ] || [ x$ACPI_SLEEP = xtrue ] || exit 0

[ x$1 != xsuspend ] || [ x$ACPI_HIBERNATE = xtrue ] || exit 0

if [ x$LOCK_SCREEN = xtrue ]; then
. /usr/share/acpi-support/screenblank
fi

if [ x$1 = xsleep ]; then
pm-suspend
elif [ x$1 = xsuspend ]; then
pm-hibernate
fi
Contents of my "sleep_suspendbtn.sh" file:
Code:
#!/bin/sh

command=$1
if [ $command = "sleep" ]; then
key=$KEY_SLEEP
elif [ $command = "suspend" ]; then
key=$KEY_SUSPEND
else
logger -t${0##*/} -perr -- "Error: Cannot recognize command $1"
fi

test -f /usr/share/acpi-support/key-constants || exit 0

. /usr/share/acpi-support/policy-funcs

if CheckPolicy; then
# If gnome-power-manager or klaptopdaemon are running, generate the X
# "sleep/suspend" key. The daemons will handle that keypress according to
# their settings.

# (With this script being called only when a key is pressed that is *not*
# seen as a suspend key by the rest of the system, we still need to do this
# translation here.)

. /usr/share/acpi-support/key-constants
acpi_fakekey $key 
else
# No power management daemons are running. Divert to our own implementation.

# Note that sleep.sh assumes that the pressed key is also seen by the rest
# of the system. However, it will choose the right path (our own
# implementation) if CheckPolicy says so. And this way we have a single
# user-configurable point for how we do suspend. (Not that that's nice, 
# but until we have pluggable suspend methods this is the way to go.)

/etc/acpi/sleep_suspend.sh $
```
=====

I found this: "Best practice to debug Linux* suspend/hibernate issues" https :// 01.org/blogs/rzhang/2015/best-practice-debug-linux-suspend/hibernate-issues
STR (suspend-to-RAM) offers significant power savings as everything in the system except memory is put into a low-power state. Memory should be placed into the self-refresh mode to retain its contents. ACPI platforms are in S3 after suspending to RAM. To enter this state, run the shell command: echo mem> /sys/power/state

I read "Power Management Interface for System Sleep" wwwDOTkernelDOTorg/doc/Documentation/power/interface.txt
and I found that:
* The file "/sys/power/state" contains this
Code:
freeze mem disk
and
* The file "/sys/power/disk" contains this
[/\code][platform] shutdown reboot suspend test_resume[/code]
I followed this "DebuggingKernelSuspend - Ubuntu Wiki" wikiDOTubuntuDOTcom/DebuggingKernelSuspend
```
sudo sh -c "sync && echo 1 > /sys/power/pm_trace && pm-suspend"
```
That DID put my laptop into Suspend-to-RAM state. A brief press on the power button woke it up, but then I got a frozen screen, it would not respond to keyboard or mouse. Frozen as things were when it SuspendedToRAM.

---

