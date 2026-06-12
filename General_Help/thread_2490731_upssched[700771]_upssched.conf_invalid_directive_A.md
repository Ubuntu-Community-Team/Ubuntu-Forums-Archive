---
title: "upssched[700771]: upssched.conf: invalid directive AT ONLINE CyberPower-CP1500AVR"
date: 2023-09-13
forum: General Help
---

### Post by pinaart on 2023-09-13
I'm a retired EE experienced in software development, but I may just be too old to understand how to setup my NUT system and correctly configure the upssched.conf file because I get the error on the subject line plus a few more like it!

I googled for examples, but came up empty.
This is the full content of my file, upssched.conf:
> CMDSCRIPT /bin/upssched-cmd

# Custom commands
AT ONLINE * CANCEL-TIMER onbattwarn
AT ONLINE * EXECUTE ups-back-on-power
AT ONBATT * START-TIMER onbattwarn 30
AT LOWBATT CyberPower-CP1500AVR CyberPower-CP1500AVR@localhost EXECUTE lowbatt

# Debian-friendly location to upssched.conf:
PIPEFN /var/run/nut/upssched.pipe
LOCKFN /var/run/nut/upssched.lock

I even looked at the source code and I still have no insights. I have the /bin/upssched-cmd referenced by the configuration file and it's content is,
> #! /bin/sh#
case $1 in
        online) MSG="$UPS, $CHMSG - power supply has been restored." ;;
        onbatt) MSG="$UPS, $CHMSG - power failure - save your work!" ;;
        lowbatt) MSG="$UPS, $CHMSG - shutdown now!" ;;
        upsgone) MSG="The UPS $UPS has been gone for awhile" ;;
        onbattwarn) # Send a notification mail
          MSG="The UPS has been on battery for awhile"
          echo $MSG | mail -s"UPS monitor" [email]pinaar14@gmail.com[/email]
          # Create a flag-file on the filesystem, for your own processing
          /usr/bin/touch /var/run/nut/ups-on-battery ;;
        ups-back-on-power) # Delete the flag-file on the filesystem
          /bin/rm -f /var/run/nut/ups-on-battery ;;
        *) MSG="$UPS, $CHMSG - Unrecognized command: $1" ;;
esac
logger -i -t upssched-cmd $MSG

Please have mercy on my soul. My ego can't handle excessive brow-beatings any more. [IMG]https://ubuntuforums.org/images/icons/icon7.png[/IMG]
However, I would appreciate any and all pointers, suggestions, and encouragement. (I will never give up, but I just hope it doesn't take me months to iron out my issues with my NUT server system.)
In case it matters, I am using three controllers to manage one UPS each and monitoring from a separate server on my desktop. The UPSes are CyberPower CP1500AVR CP625HGa, LX1500GU and, APC Back-UPS NS 900M.

Thank you!

---

