---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2007-09-24
forum: General Help
---

### Post by mpgarate on 2007-09-24
any ideas?

> mike@mike-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up hotkey-setup (0.1-17ubuntu19) ...
KDSETKEYCODE: Invalid argument
failed to set scancode 8a to keycode 205
KDSETKEYCODE: Invalid argument
failed to set scancode 87 to keycode 236
KDSETKEYCODE: Invalid argument
failed to set scancode 8b to keycode 227
KDSETKEYCODE: Invalid argument
failed to set scancode 89 to keycode 161
KDSETKEYCODE: Invalid argument
failed to set scancode 85 to keycode 224
KDSETKEYCODE: Invalid argument
failed to set scancode 86 to keycode 225
KDSETKEYCODE: Invalid argument
failed to set scancode 92 to keycode 226
KDSETKEYCODE: Invalid argument
failed to set scancode 81 to keycode 164
KDSETKEYCODE: Invalid argument
failed to set scancode 82 to keycode 128
KDSETKEYCODE: Invalid argument
failed to set scancode 83 to keycode 165
KDSETKEYCODE: Invalid argument
failed to set scancode 84 to keycode 163
KDSETKEYCODE: Invalid argument
failed to set scancode a2 to keycode 164
KDSETKEYCODE: Invalid argument
failed to set scancode 90 to keycode 165
KDSETKEYCODE: Invalid argument
failed to set scancode 99 to keycode 163
KDSETKEYCODE: Invalid argument
failed to set scancode a4 to keycode 166
KDSETKEYCODE: Invalid argument
failed to set scancode ed to keycode 226
invoke-rc.d: initscript hotkey-setup, action "start" failed.
dpkg: error processing hotkey-setup (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on hotkey-setup; however:
  Package hotkey-setup is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 hotkey-setup
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by JMillard81 on 2007-09-25
Press ALT+F2


gksudo gedit /etc/init.d/hotkey-setup [ENTER]


Edit (Substitute it for your manufacturers name):

Dell*)
. /usr/share/hotkey-setup/dell.hk
;;

to:

Dell*)
;;

then do:

sudo apt-get -f install

---

### Post by mpgarate on 2007-09-25
okay... i ended up just re-installing... only to run into a [sound problem]("http://ubuntuforums.org/showthread.php?t=559922")... but thanks for the tip, I'll reference this thread if it happens again!

---

### Post by mpgarate on 2007-09-25
actually... im having that problem again.. must be something with gutsy and / or my computer... okay heres my file.. im not sure what i'm supposed to change

> #!/bin/sh

manufacturer=`dmidecode --string system-manufacturer`
name=`dmidecode --string system-product-name`
version=`dmidecode --string system-version`

SAVED_STATE=/var/run/hotkey-setup
THINKPAD_LOCKFILE=$SAVED_STATE.thinkpad-keys
THINKPAD_PROC_HOTKEY=/proc/acpi/ibm/hotkey
THINKPAD_KEYS=/usr/sbin/thinkpad-keys

# This is here because it needs to be executed both if we have a
# Lenovo that also IDs as a ThinkPad, or if we have a real IBM one.
do_thinkpad () {
    . /usr/share/hotkey-setup/ibm.hk
    modprobe thinkpad-acpi
    # Try to enable the top 8-bits of the mask
    sed -e '/mask:/s/.*\(....\)$/0xff\1/p;d' $THINKPAD_PROC_HOTKEY > $THINKPAD_PROC_HOTKEY
    # If the top bit (ThinkPad key) sticks, skip the polling-daemon
    if ! grep -q '0x[8-9a-f].....$' $THINKPAD_PROC_HOTKEY && test -x $THINKPAD_KEYS; then
        if [ ! -c /dev/input/uinput ]; then
            modprobe uinput
        fi
        if [ ! -c /dev/nvram ]; then
            modprobe nvram
        fi
        $THINKPAD_KEYS $1 && touch $THINKPAD_LOCKFILE
    fi
}

case "$1" in
    start)

    /usr/sbin/dumpkeycodes >$SAVED_STATE
    
    if [ $? -gt 0 ]; then
	rm -f $SAVED_STATE
    fi

    . /usr/share/hotkey-setup/key-constants

    case "$manufacturer" in
	Acer*)
	. /usr/share/hotkey-setup/acer.hk
	case "$name" in
	    Aspire\ 16*)
	    . /usr/share/hotkey-setup/acer-aspire-1600.hk
	    ;;
	esac
	;;

	ASUS*)
	. /usr/share/hotkey-setup/asus.hk
	;;

	Compaq*)
	case "$name" in
	    Armada*E500*|Evo*N620*)
	    . /usr/share/hotkey-setup/compaq.hk
	    ;;
	esac
	;;

	Dell*)
	. /usr/share/hotkey-setup/dell.hk
	;;

	Hewlett-Packard*)
	# Load this _first_, so that it can be overridden
	. /usr/share/hotkey-setup/hp.hk
	case "$name" in
	    # Please open a bug if uncommenting these "Presario" entries works for you...
	    #*Presario\ V2000*)
	    #. /usr/share/hotkey-setup/hp-v2000.hk
	    #;;
	    *Tablet*)
	    . /usr/share/hotkey-setup/hp-tablet.hk
	    ;;
	esac
	;;

	IBM*)
	do_thinkpad IBM
	;;

	LENOVO*)
	case "$version" in
	    *ThinkPad*)
	    do_thinkpad --no-brightness
	    ;;
	    *)
	    . /usr/share/hotkey-setup/lenovo.hk
	    ;;
	esac
	;;
	
	MEDION*)
	case "$name" in
	    *FID2060*)
	    . /usr/share/hotkey-setup/medion-md6200.hk
	    ;;
	esac
	;;

	MICRO-STAR*)
	case "$name" in
	    *INFINITY*)
	    . /usr/share/hotkey-setup/micro-star-infinity.hk
	    ;;
	esac
	;;

	Samsung*|SAMSUNG*)
	. /usr/share/hotkey-setup/samsung.hk
	;;

	Sony*)
	modprobe sonypi; # Needed to get hotkey events
	modprobe sony-laptop
	;;

	*)
	. /usr/share/hotkey-setup/default.hk	
    esac
    . /usr/share/hotkey-setup/generic.hk
    ;;
    stop)
	if [ -f $THINKPAD_LOCKFILE ]; then
	    kill `pidof thinkpad-keys` || true ; rm -f $THINKPAD_LOCKFILE
	fi
	if [ -f $SAVED_STATE ]; then
		setkeycodes $(cat $SAVED_STATE) || true
	fi
    ;;
    restart|force-reload)
    $0 stop || true
    $0 start
    ;;
esac


edit: nevermind, i got it :) thanks!

---

### Post by raif on 2007-10-28
This still doesn't work for me.  I have a Dell multi-media keyboard and am running gutsy / kubuntu so I have removed the line beneath Dell in the hotkey-setup file.  If I do sudo apt-get -f install nothing happens, so I tried the following:

> 
root@kubuntu-desktop:/# apt-get -f install hotkey-setup
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  hotkey-setup
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/20.7kB of archives.
After unpacking 12.3kB of additional disk space will be used.
Selecting previously deselected package hotkey-setup.
(Reading database ... 160863 files and directories currently installed.)
Preparing to replace hotkey-setup 0.1-17ubuntu3 (using .../hotkey-setup_0.1-17ubuntu20_i386.deb) ...
KDSETKEYCODE: Invalid argument
failed to set scancode 80 to keycode 256
invoke-rc.d: initscript hotkey-setup, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
KDSETKEYCODE: Invalid argument
failed to set scancode 80 to keycode 256
invoke-rc.d: initscript hotkey-setup, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/hotkey-setup_0.1-17ubuntu20_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
root@kubuntu-desktop:/# /etc/init.d/hotkey-setup restart
KDSETKEYCODE: Invalid argument
failed to set scancode 80 to keycode 256


---

