---
title: "TVTime and xawtv problems..."
date: 2005-05-17
forum: General Help
---

### Post by cwestpha on 2005-05-17
Ok I have an AverMedia AverTV Stereo PCI card. Also for a video card I have the Radeon x800 256MB card.

When I try to use xawtv I get the following problems:

```
This is xawtv-3.94, running on Linux/i686 (2.6.10-5-386)
WARNING: v4l-conf is compiled without DGA support.
WARNING: couldn't find framebuffer base address, try manual
         configuration ("v4l-conf -a <addr>")
ioctl: VIDIOC_OVERLAY(int=1): Invalid argument
game over
```

Also when I try to use something like TVTime I get the folowing back:

```
Running tvtime 0.9.15.
rtctimer: Cannot set periodic interval: Permission denied

    Failed to get 1024 Hz resolution from your RTC device.  High
    resolution access is necessary for video to be smooth.  Please
    run tvtime as root, set tvtime as SUID root, or change the
    maximum RTC resolution allowed for user processes by running this
    command as root:
        sysctl -w dev.rtc.max-user-freq=1024
    See our support page at http://tvtime.net/ for more information.

Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/athirne/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: http://gatos.souceforge.net/
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.
```

Anyone know what I need to do to fix this and can give me a walk through of how to do it?

---

### Post by FreeEagle on 2005-05-21
okay i will tell you what you have to do it is simple, Just follow what i will tell you ...

First you have to set a Root Password ( Super User Password ) this can be done so:

open a shell and write this : 

sudo passwd root    then click on Enter and put your Password ( User Password )
then he will prompt you to a new Password ( this is the Root Password )
try to choose a Root Password for you, and enter it twice to Confurm.

do this in the same Shell ( log as a Root ) :

su -
then enter your Root Password

then change to the Root Directory by doing this ;  cd ..
 then 

start TVtime as a root by writing this: 

tvtime              then Click Enter and follow the instruction that he will ask you about.

Failed to get 1024 Hz resolution from your RTC device.  High
    resolution access is necessary for video to be smooth.  Please
    run tvtime as root, set tvtime as SUID root, or change the
    maximum RTC resolution allowed for user processes by running this
    command as root:
        sysctl -w dev.rtc.max-user-freq=1024
    See our support page at [http://tvtime.net/](http://tvtime.net/) for more information.

Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/athirne/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: [http://gatos.souceforge.net/](http://gatos.souceforge.net/)
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

follow these and hope this will work with you... 


Best Regards,
 FreeEagle

---

