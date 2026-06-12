---
title: "Can't get Powertop Optimizations to stick"
date: 2014-10-31
forum: General Help
---

### Post by chazzyfresh33 on 2014-10-31
I've been attempting to optimize my laptop's battery life lately. Obviously I already have TLP installed, but lately I've been working with Powertop and Laptop-Mode to try to improve even more. My Powertop HTML Continually shows 3 things that I should improve upon but it seems no matter what I do I can't make them stick. I've tried putting them in RC Local and the .conf files in Laptop Mode, but nothing seems to work. These are the 3.


Wireless Power Saving for interface wlan0 	iw dev wlan0 set power_save on


VM writeback timeout 	echo '1500' > '/proc/sys/vm/dirty_writeback_centisecs';


Enable Audio codec power management 	echo '1' > '/sys/module/snd_hda_intel/parameters/power_save';


Any ideas as to how to make this work? This is what my RC Local looks like right now


    #!/bin/sh -e
    #
    # rc.local
    #
    # This script is executed at the end of each multiuser runlevel.
    # Make sure that the script will "exit 0" on success or any other
    # value on error.
    #
    # In order to enable or disable this script just change the execution
    # bits.
    #
    # By default this script does nothing.
    fstrim -v /
    #
    # Modification for SSD
    for dir in apparmor apt cups dist-upgrade fsck gdm installer samba unattended-upgrades ;
    do
               if [ ! -e /var/log/$dir ] ; then
                       mkdir /var/log/$dir
               fi
    done
    
    iwconfig wlan0 txpower 5
    
    iw dev wlan0 set power_save on
    
    #echo '1500' > '/proc/sys/vm/dirty_writeback_centisecs';
    
    echo '1' > '/sys/module/snd_hda_intel/parameters/power_save';
    
    rfkill block bluetooth
    
    exit 0

---

### Post by tgalati4 on 2014-10-31
It's possible that your hardware does not recognize those switches.  It's also possible that the BIOS is controlling those settings based on Power Management settings.  Try turning off Power Management in BIOS to see if the software switches stick.

How much power do you expect to save with these settings?  In my experience it is very, very low.  On the order of a few %.  Your CPU, GPU, display are the big power users and short of undervolting, declocking, and screen dimming (so that it is unreadable) there is little you can do to improve power usage.

---

### Post by chazzyfresh33 on 2014-10-31
I'm just all about optimization. If I can make something better I will

---

