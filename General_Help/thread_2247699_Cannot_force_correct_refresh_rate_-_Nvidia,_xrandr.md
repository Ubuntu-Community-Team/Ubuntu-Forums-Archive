---
title: "Cannot force correct refresh rate - Nvidia, xrandr"
date: 2014-10-09
forum: General Help
---

### Post by sns4rnr on 2014-10-09
ok so I'm about to start pulling my hair out and throwing things.  I have swapped my old Radeon card for a new nvidia GT730.  The Radeon card was using the built-in open source driver so I did not have to purge any proprietary Radeon drivers.  I have installed and activated the nvidia proprietary recommended driver 340.46 from the xorg-edgers ppa because Ubuntu's repository options don't support this card.  After some tweaking with xorg.conf and having to force a custom edid, I finally got the driver working.
nvidia-xconfig created something called a "metamode" in the xorg.conf for my resolution choice.
nvidia-settings made some further adjustments to xorg.conf as well.

The system boots to the correct 1680x1050 resolution on the "greeter" login screen - before user login... I'm golden that far.

When the user logs in, I have issues... The resolution is technically correct, however the desktop image is shifted left 1-2 inches so the launcher is off screen.
If I launch "nvidia-settings", and go to X server configuration,  Select Advanced options, I can re-set my resolution there.  Caveat.... I am presented with 3 options for refresh rates... Auto, 60(1) and 60(2).  Choosing either Auto or 60(1) gives me the offset-image problem.  Choosing refresh rate 60(2) works and the screen is fine - until the next reboot, logout/login.... or if I use system settings display to change or simply "re-choose" my resolution, the offset image problem returns, and I have to go back to nvidia-settings to fix it.

I've been all over the web chasing many many "how to make nvidia-settings persistent" threads and have tried virtually everything I can find there, but nothing is working.
nvidia-settings ---load-config-only   literally does nothing at all.

xrandr command reveals this:
Screen 0: minimum 8 x 8, current 1680 x 1050, maximum 16384 x 16384
VGA-0 connected primary 1680x1050+0+0 (normal left inverted right x axis y axis) 473mm x 296mm
   1680x1050      60.0*+   60.0  
   1600x1200      60.0  
   1440x900       75.0     59.9  
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.0     70.1     60.0  
   800x600        75.0     72.2     60.3     56.2  
   640x480        75.0     72.8     59.9  
DVI-D-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)

Note the duplicate refresh rates for 1680x1050 and also the "473mm x 296mm".   In the above, the first 60.0 is marked with * indicating the active choice and a + indicating the default or preferred choice.  In this condition I have the offset screen image.
After going to nvidia-settings and choosing the second 60 hz refresh rate, the second 60.0 option is active, and the "473mm x 296mm" changes to "470mm x 300mm" and the screen is fine.

SO - nvidia-settings has the option to save to "xorg.conf" which I've done and that did fix the same image offset problem with the greeter/login page, but does nothing with regard to the post login running of X.  I need a way to copy "root's" profile to my standard users' maybe.

I've tried to address this with xrandr commands which some threads suggest to use in some "xinit" location or in startup programs, but until I can get such a command to work directly, there's no point in figuring out where to put such a command permanently.  Trying to set the refresh rate with xrandr results in no change from either condition I find myself in.  I guess there's no way for xrandr to distinguish between the two options on it's own and I can't find syntax with xrandr to choose between them.   Similarly I'm not finding any command line nvidia-settings syntax yet either.

If I could find a way to remove the "first" refresh rate option from wherever that's hiding, maybe the system will automatically fall to the one I want.   Xrandr commands to try to either delmode or rmmode are failing with errors citing "bad match" issues.

Any ideas?    Something's hiding from me in here.  Gotta be a fix somewhere.

Ubuntu 14.04
AMD 8320
nvidia GT730   340.46 proprietary driver
Acer X223w monitor

EDIT:  Collected output from command  nvidia-settings --query all  while problem was present and when not for comparison....

When screen image is shifted: (BAD)
  Attribute 'CurrentMetaMode' (snstest-build:0.0): id=72, switchable=no,
  source=RandR :: DPY-0: nvidia-auto-select @1680x1050 +0+0
  {ViewPortIn=1680x1050, ViewPortOut=1680x1050+0+0} 

  Attribute 'GPUUtilization' (snstest-build:0[gpu:0]): graphics=1, memory=2,
  video=0, PCIe=0 

When screen image is fine: (GOOD)
  Attribute 'CurrentMetaMode' (snstest-build:0.0): id=72, switchable=no,
  source=nv-control :: DPY-0: 1680x1050_60_0 @1680x1050 +0+0
  {ViewPortIn=1680x1050, ViewPortOut=1680x1050+0+0} 

  Attribute 'GPUUtilization' (snstest-build:0[gpu:0]): graphics=1, memory=2,
  video=0, PCIe=1 

EDIT:   RESOLVED  ...  Sort of....
I could never figure out how to disable nvidia-auto-select mode.  It seems nvidia has designed this to be a generic forced "safe" mode, but not guaranteed to give the "best" or even preferred mode for a given user.  I found some info on how the pool of modes available is constructed/managed by the driver and there are aspects to it beyond control of the user.  In my case, Nvidia is a little "over-confident" in their auto-select procedures as it really limits the abilities of users to deal with cases where it proves insufficient.

Anyway - on a whim, I decided to connect this same monitor via DVI cable instead of VGA cable...  and voila.... its ok...   With no other changes...
nvidia-auto-select is still choosing the same "mode" as before (the first 1680x1050 60hz option) but over the DVI cable, it's working ok... I manually changed to the second 60hz option expecting that one to have issues now, but no... that's ok too.  Go figure.  Maybe the DVI mode supported by the monitor is where the details of the first mode came from and were just not very applicable over VGA.

Another item that was fixed... though the screen resolution on VGA with the second 60Hz option was ok, I got strange occasional flickering in some windows particularly when focus was drawn to the top or bottom edges of the window.    Some of the affected Apps are ok now... others (firefox) still flicker on odd occasions.  

Well there's 20 hours I'll never get back.   Still no real official explanation of the original problem.   But it's working so time to go do it all again on my live install.

---

