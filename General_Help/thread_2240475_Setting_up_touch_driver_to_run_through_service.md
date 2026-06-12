---
title: "Setting up touch driver to run through service"
date: 2014-08-20
forum: General Help
---

### Post by venkat-330 on 2014-08-20
We are trying to integrate a touch panel to our Linux system.

  [Touch driver (General touch)]("http://www.generaltouch.com/upload/file/linuxgtusbdriver_i386.rar")
  I am trying to run this application in Linux service.Below are the steps which i followed
  **Driver installtion**

  cp -rf Gentouch_S/ /usr/local/Gentouch_S/
cp -f 10-evdev.conf /usr/share/X11/xorg.conf.d/10-evdev.conf
cp -f 69-gentouch.rules /etc/udev/rules.d/69-gentouch.rules
  **Setting touch in service**
   cp genTouchService /etc/init.d/genTouchSevice
 chmod 755 /etc/init.d/genTouchSevice
 update-rc.d genTouchSevice defaults
  **Script details for :/etc/init.d/genTouchSevice**
  #! /bin/sh
# /etc/init.d/genTouchSevice
#
# Carry out specific functions when asked to by the system
case "$1" in
  start)
    logger "Gentouch module started by service"
    /usr/local/Gentouch_S/GT_service start
    ;;
  stop)
    logger "Gentouch module stopped by service"
    /usr/local/Gentouch_S/GT_service stop
    ;;
  restart)
    logger "Gentouch module restarted by service"
    /usr/local/Gentouch_S/GT_service restart
    ;;

  *)
    echo "Usage: /etc/init.d/genTouchSevice {start|stop|restart}"
    exit 1
    ;;
esac

exit 0
  On doing this, I was pretty sure that the application started via service during boot up. verified by log(2014 Aug 20 00:58:24::logger:: Gentouch module started by service)
  Even though the service started, When i touch my screen i dont see any touch events (No movement in pointer position too)
  So, Just tried restarting touch driver in below scenarios:
  **1 . service genTouchSevice restart**
  No effeci, Still there was no touch event detection
  **2./usr/local/Gentouch_S/ST_service restart**
  My application was able to sense the touch events.
  What is the error.Unable to find it

---

