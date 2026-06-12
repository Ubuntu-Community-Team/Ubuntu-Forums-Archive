---
title: "Can not get correct resolution for monitor"
date: 2017-01-04
forum: General Help
---

### Post by lsutiger on 2017-01-04
I have a new install of 16.04.1. DE is gnome flashback The monitor is an Acer AL2216W. The video card is a [AMD/ATI] RS880 [Radeon HD 4200] (from lspci). I attempted to install the driver from AMD but that had some pretty bad results(looping at the login screen). Uninstalled and able to log back in.
I did some research and started issuing commands with xrandr. I was able to get the desired resolution(1680X1050). That was good until reboot. Now it is stuck on 1280X800 - this is from Settings-->Display.
When I recall xrandr I receive the following:
```
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 8192 x 8192
VGA-0 connected primary 1280x800+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00  
   800x600       60.32    56.25  
   848x480       60.00  
   640x480       59.94  
   1680x1050_60.00  59.81* 
```
The asterisk means that is the current mode being used, but it is not.
I followed the instructions [here]("http://askubuntu.com/questions/760707/bad-resolution-in-ubuntu-16-04") to get the resolution correct the first time. I then followed the instructions [here]("http://askubuntu.com/questions/754231/how-do-i-save-my-new-resolution-setting-with-xrandr") in order to save the settings, which did not take.
I am lost on how to get this corrected.

EDIT: I was able to remove the 1680x1050 mode, re-add and apply.
How do I save this for reboot?

---

### Post by DuckHook on 2017-01-05
First and foremost, don't use any of the old AMD/ATI drivers for Xenial and newer. They no longer work with the newer versions of Xorg. Because your card is the HD 4200, you have only one choice and it is the community supported *radeon* driver.

[LIST=1]
[*]How did you remove the fglrx drivers? You may have left some config files behind that are messing up radeon. Did you create a Xorg.conf file as part of your experimenting? If so, please post its contents.
[*]You link to instructions using the .xprofile technique. Please post contents of ~/.xprofile and also confirmation that it is in the right directory and has the right permissions:```
ls -laF ~ | grep .xprofile
``````
cat ~/.xprofile
```
[*]Do you use a KVM switch? Such switches often interfere with your video card properly reading the monitor's EDID. If so, connect the monitor directly to the computer.
[*]What video port and cable type are you using?
[*]Please post output of:```
cvt 1680 1050 60
```
[*]Also with cable connected directly (no KVM switch), post results of:```
sudo apt install read-edid && sudo get-edid | parse-edid
```
[/LIST]

---

### Post by lsutiger on 2017-01-05
1) I was following the [instructions ]("https://help.ubuntu.com/community/RadeonDriver"), though I never got to the step of removing and driver other than what was installed due to the logon screen looping issue. No Xorg.conf file created.
2) Permissions:
```
ls -laF ~ | grep .xprofile
-rwxrwxr-x  1 dvdsrv dvdsrv  179 Dec 30 15:10 .xprofile*

```
Contents:
```

xrandr --newmode "1680x1050_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
xrandr --addmode VGA-0 1680x1050_60.00
xrandr --output VGA-0 --mode 1680x1050_60.00
```
3) I DO use a KVM switch, but I am currently bypassing it and have since starting. I am still receiving this in the log:
```
[drm:radeon_vga_detect [radeon]] *ERROR* VGA-1: probed a monitor but no|invalid EDID
```
After much research on this it seems a lot of people are experiencing this but it does not harm the system other than spamming your log. A lot of the fixes proposed to eliminate this in the log seems to break other things. I currently have a smooth running system. The only issue is with the resolution not saving.
4) The VGA port on the MB and a regular VGA cable. This same cable and motherboard has been in place for a number of years along with the KVM switch. This system was running 10.04 and we decided to upgrade to 16.04 since we had some time to do so.
5) ```
# 1680x1050 59.95 Hz (CVT 1.76MA) hsync: 65.29 kHz; pclk: 146.25 MHz
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync

```
6) ```
This is read-edid version 3.0.2. Prepare for some fun.
Attempting to use i2c interface
No EDID on bus 1
No EDID on bus 2
No EDID on bus 3
No EDID on bus 4
1 potential busses found: 0
256-byte EDID successfully retrieved from i2c bus 0
Looks like i2c was successful. Have a good day.
WARNING: Checksum failed
Trying to continue...
Section "Monitor"
	Identifier "Acer AL2216W"
	ModelName "Acer AL2216W"
	VendorName "ACR"
	# Monitor Manufactured week 22 of 2007
	# EDID version 1.3
	# Analog Display
	DisplaySize 470 300
	Gamma 2.20
	Option "DPMS" "true"
	Horizsync 30-82
	VertRefresh 56-76
	# Maximum pixel clock is 210MHz
	#Not giving standard mode: 1280x1024, 60Hz
	#Not giving standard mode: 1280x960, 60Hz
	#Not giving standard mode: 1152x864, 75Hz
	#Not giving standard mode: 1440x900, 60Hz
	#Not giving standard mode: 1440x900, 75Hz
	#Not giving standard mode: 1680x1050, 60Hz
	#Not giving standard mode: 1280x720, 60Hz
	#Not giving standard mode: 1360x765, 60Hz
	Modeline 	"Mode 0" 146.25 1680 1784 1960 2240 1050 1053 1059 1089 -hsync +vsync 
EndSection

```

After fiddling I decided to write a bash script containing the xrandr commands and put that as a startup application. I have not restarted yet due to some file operations I am doing. 
\Thanks for your help!

---

### Post by DuckHook on 2017-01-05
Your *.xprofile* modeline values are incorrect. That is likely the reason you are getting wonky results. Note the following in your modeline (I've highlighted the incorrect resolution values):```
xrandr --newmode "1680x1050_60.00"   83.50  [COLOR="#FF0000"]1280[/COLOR] 1352 1480 1680  [COLOR="#FF0000"]800[/COLOR] 803 809 831 -hsync +vsync
```Now note the output of cvt:```
Modeline "1680x1050_60.00"  146.25  [COLOR="#FF0000"]1680[/COLOR] 1784 1960 2240  [COLOR="#FF0000"]1050[/COLOR] 1053 1059 1089 -hsync +vsync
```Your *.xprofiles* was probably working all along. It just had the wrong modeline. Try changing the modeline to the proper one, then logout&#8594;login or, if that doesn't work, reboot. You likely don't need fancy scripting. Just the right *.xprofile*.

---

### Post by lsutiger on 2017-01-12
> **DuckHook said:**
> Your *.xprofile* modeline values are incorrect. That is likely the reason you are getting wonky results. Note the following in your modeline (I've highlighted the incorrect resolution values):```
xrandr --newmode "1680x1050_60.00"   83.50  [COLOR="#FF0000"]1280[/COLOR] 1352 1480 1680  [COLOR="#FF0000"]800[/COLOR] 803 809 831 -hsync +vsync
```Now note the output of cvt:```
Modeline "1680x1050_60.00"  146.25  [COLOR="#FF0000"]1680[/COLOR] 1784 1960 2240  [COLOR="#FF0000"]1050[/COLOR] 1053 1059 1089 -hsync +vsync
```Your *.xprofiles* was probably working all along. It just had the wrong modeline. Try changing the modeline to the proper one, then logout&#8594;login or, if that doesn't work, reboot. You likely don't need fancy scripting. Just the right *.xprofile*.
Thanks. Just getting back to this after a busy week.
I was doing copy pasta and missed that.
I now log into the wrong resolution with the message below. After I click on close, the correct resolution is applied:
```
Could not apply the stored configuration for monitors
none of the selected modes were compatible with the possible modes:
Trying modes for CRTC 79
CRTC 79: trying mode 1024x768@60Hz with output at 1280x800@60Hz (pass 0)
CRTC 79: trying mode 800x600@60Hz with output at 1280x800@60Hz (pass 0)
CRTC 79: trying mode 800x600@56Hz with output at 1280x800@60Hz (pass 0)
CRTC 79: trying mode 848x480@60Hz with output at 1280x800@60Hz (pass 0)
CRTC 79: trying mode 640x480@60Hz with output at 1280x800@60Hz (pass 0)
CRTC 79: trying mode 1680x1050@60Hz with output at 1280x800@60Hz (pass 0)
CRTC 79: trying mode 1024x768@60Hz with output at 1280x800@60Hz (pass 1)
CRTC 79: trying mode 800x600@60Hz with output at 1280x800@60Hz (pass 1)
CRTC 79: trying mode 800x600@56Hz with output at 1280x800@60Hz (pass 1)
CRTC 79: trying mode 848x480@60Hz with output at 1280x800@60Hz (pass 1)
CRTC 79: trying mode 640x480@60Hz with output at 1280x800@60Hz (pass 1)
CRTC 79: trying mode 1680x1050@60Hz with output at 1280x800@60Hz (pass 1)
Trying modes for CRTC 80
CRTC 80: trying mode 1024x768@60Hz with output at 1280x800@60Hz (pass 0)
CRTC 80: trying mode 800x600@60Hz with output at 1280x800@60Hz (pass 0)
CRTC 80: trying mode 800x600@56Hz with output at 1280x800@60Hz (pass 0)
CRTC 80: trying mode 848x480@60Hz with output at 1280x800@60Hz (pass 0)
CRTC 80: trying mode 640x480@60Hz with output at 1280x800@60Hz (pass 0)
CRTC 80: trying mode 1680x1050@60Hz with output at 1280x800@60Hz (pass 0)
CRTC 80: trying mode 1024x768@60Hz with output at 1280x800@60Hz (pass 1)
CRTC 80: trying mode 800x600@60Hz with output at 1280x800@60Hz (pass 1)
CRTC 80: trying mode 800x600@56Hz with output at 1280x800@60Hz (pass 1)
```

---

### Post by DuckHook on 2017-02-01
Greetings lsutiger

I revisited this thread purely by accident. I usually unsubscribe from threads after 4 days with no response. Have now resubscribed.

If you are still following this, I don't understand your statement:
> **lsutiger said:**
> I now log into the wrong resolution with the message below. After I click on close, the correct resolution is applied:
A setting in .xprofile usually does not invoke a dialogue box or a terminal session. So how is this message being delivered? What is there to "close"?

---

