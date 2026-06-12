---
title: "System Crashes after the latest update"
date: 2013-09-26
forum: General Help
---

### Post by Lee_Nowell on 2013-09-26
Hi All,

I am running 12.04 and haven't installed any updates for a couple of months.  Weekend before last, I installed all updates shown in the update manager and all seemed ok until I rebooted... When it restarted, it had forgotten all the resolution settings, detected the correct card but not the monitor resolution.  Also, I believe I was seeing "No irq handler for vector" messages on the screen during restart (I can't remember whether it was on start up or shutdown).  Cutting a long story short after a lot of messing around and searching here, I uninstalled all NVidia drivers (except nvidia-common as directed in the post) and magically the display problem was resolved.

Now, it starts fine, graphics problem solved but after a period of time, the system hangs with a black screen with several "No irq handler for vector" errors on it. It does not respond to keyboard nor mouse and needs to be switched off using to restart.  I suspect it is when it is trying to sleep/ go into suspend mode but I am not sure.

Here is a sample of messages from syslog

Sep 25 13:02:06 MediaPC kernel: [ 2011.768857] do_IRQ: 0.107 No irq handler for vector (irq -1)
Sep 25 13:02:06 MediaPC kernel: [ 2012.031886] do_IRQ: 0.107 No irq handler for vector (irq -1)
Sep 25 13:02:08 MediaPC kernel: [ 2013.241551] do_IRQ: 0.107 No irq handler for vector (irq -1)
Sep 25 13:02:08 MediaPC kernel: [ 2013.241558] do_IRQ: 0.107 No irq handler for vector (irq -1)
Sep 25 13:02:08 MediaPC kernel: [ 2013.247439] do_IRQ: 0.107 No irq handler for vector (irq -1)
Sep 25 13:02:08 MediaPC kernel: [ 2013.447151] do_IRQ: 0.107 No irq handler for vector (irq -1)
Sep 25 13:02:08 MediaPC kernel: [ 2013.457231] do_IRQ: 0.107 No irq handler for vector (irq -1)
Sep 25 13:02:08 MediaPC kernel: [ 2013.465002] do_IRQ: 0.107 No irq handler for vector (irq -1)
Sep 25 13:02:08 MediaPC kernel: [ 2013.465009] do_IRQ: 0.107 No irq handler for vector (irq -1)
Sep 25 13:02:08 MediaPC kernel: [ 2013.761089] do_IRQ: 0.107 No irq handler for vector (irq -1)


pm-powersave and pm-suspend logs do seem to have anything that jumps out as an error.

The bottom section of the "Kernal Ring" shows....

[  301.016707] DVB: registering new adapter (saa7133[0])
[  301.016707] DVB: registering adapter 0 frontend 0 (Philips TDA10046H DVB-T)...
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] tda1004x: setting up plls for 48MHz sampling clock
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] tda1004x: found firmware revision 23 -- ok
[  301.016707] dvb_init() allocating 1 frontend
[  301.016707] DVB: registering new adapter (saa7133[1])
[  301.016707] DVB: registering adapter 1 frontend 0 (Philips TDA10046H DVB-T)...
[  301.016707] tda1004x: setting up plls for 48MHz sampling clock
[  301.016707] tda1004x: found firmware revision 23 -- ok
[  301.016707] eth0: no IPv6 routers present
[  301.016707] tda1004x: setting up plls for 48MHz sampling clock
[  301.016707] tda1004x: found firmware revision 23 -- ok
[  301.016707] tda1004x: setting up plls for 48MHz sampling clock
[  301.016707] tda1004x: found firmware revision 23 -- ok
[  301.016707] init: plymouth-stop pre-start process (2810) terminated with status 1
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 18 callbacks suppressed
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 77 callbacks suppressed
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 7 callbacks suppressed
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 1 callbacks suppressed
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 11 callbacks suppressed
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] do_IRQ: 0.107 No irq handler for vector (irq -1)
[  301.016707] [Hardware Error]: Machine check events logged

Does anyone have any idea what this is or what I could try to get to the bottom of this?

thanks in advance for your help

Lee.

---

