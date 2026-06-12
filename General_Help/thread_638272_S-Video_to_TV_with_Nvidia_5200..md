---
title: "S-Video to TV with Nvidia 5200."
date: 2007-12-11
forum: General Help
---

### Post by Garrulousbrevity on 2007-12-11
Hey,

So I recently purchased as Nvidia 5200 with two VGA ports and an S-video port.  Unlike my old Radeon card it does most of what I want it to without hours of tweaking.  However, I am having trouble getting it to display on both my monitor and my TV at the same time.  

I have an S-Video to RCA cable attached to the computer which goes to an RCA switch which is attached to the TV, and when the switch is on the right setting, the nvidia-settings program is able to detect the television.  If I set the "configure" to "Separate X screen," the monitor works when I hit ctrl+alt+backspace, but not the TV.  If I set the configure to "Twinveiw" the TV does display everything clearly (or at least as clearly as the TV is capable of), but the monitor remains blank.  

I've been looking at how xorg.conf file is modified, but I really have no idea how to go about editing it.

I guess what I'm looking for is either having both screens display at once, or having an easy way of switching between the two.

Any suggestions?

---

### Post by technoidiot on 2007-12-11
I had the same setup in Windoze and they way I got it to work was thru the Nvidia setting to stretch your screen. I have not tied this in Kubuntu which is what I am currently using but I image there should be so extension of the equivalent or same setting dialogue. Sorry I can't be of more help but this is something you might look for.

---

### Post by fenian on 2007-12-11
First you need to enable the Nvidia driver ; go to the menu System>Administration>Restricted Drivers and choose to enable the nvidia driver.
Then open the Nvidia settings controls with the command...

> sudo nvidia-settings

Go to X Server Display Settings.If your TV display isn't detected click the detect displays button.Once your TV is detected click the configure button you will have three choices...
1-Disabled=disables display.
2-Set as seperater X screen=TV will act as seperate screen w/ seperate settings (resolution,etc..)from main display.With this setting you can perform seperate tasks on both screens,i.e. watch  a video on the TV while surfing the web on the main monitor.This is how I have mine set up.
3-Twin view=Either clones the output of the main screen on the TV or extends the desktop across both screens.

Once you choose the settings you want you have to click the save to X Configuration button or the settings won't work.After saving you need to restart the X server for the changes to take eefect,to do this press ctrl+alt+backspace.

---

### Post by Garrulousbrevity on 2007-12-11
> **fenian said:**
> First you need to enable the Nvidia driver ; go to the menu System>Administration>Restricted Drivers and choose to enable the nvidia driver.
Then open the Nvidia settings controls with the command...



Go to X Server Display Settings.If your TV display isn't detected click the detect displays button.Once your TV is detected click the configure button you will have three choices...
1-Disabled=disables display.
2-Set as seperater X screen=TV will act as seperate screen w/ seperate settings (resolution,etc..)from main display.With this setting you can perform seperate tasks on both screens,i.e. watch  a video on the TV while surfing the web on the main monitor.This is how I have mine set up.
3-Twin view=Either clones the output of the main screen on the TV or extends the desktop across both screens.

Once you choose the settings you want you have to click the save to X Configuration button or the settings won't work.After saving you need to restart the X server for the changes to take eefect,to do this press ctrl+alt+backspace.

Hey, thanks for the reply.  I already have the restricted drivers enabled, and I've been using the command sudo nvidia-settings, and doing as you've said already.  However, I don't get a display on both screens.  If I set everything up, and configure them to be separate X screens, there is no display on the TV after I restart the X server.  If I set them to Twin View, I get no display on my monitor after I restart the X server.  I suppose if I wanted to watch a movie on the TV once in a while I could replace the xorg.conf file with the one that displays on the TV and restart X server, and then switch it when the movie i over, but that's involved, and seeing as how my girlfriend's laptop, which is running vista can display on both screens without an issue it would just be easier to transfer my movie files over to her computer and download the video codecs... 

Anyway, thanks for your reply.

---

### Post by fenian on 2007-12-11
Can you post your xorg.conf file?I've attached my xorg.conf which you can use as a rough guide,I'm running  seperate X screens wih no issues.I have an Nvidia 6200 and desktop effects are disabled og Ubuntu Gutsy.

---

### Post by Garrulousbrevity on 2007-12-11
I didn't see any glaringly obvious differences between our files, though I have to say I don't know what to look for in this regard.  Anyway, here's mine.

---

### Post by Garrulousbrevity on 2007-12-11
I do seem to be short one "screen" section and one "monitor" section from you.

---

### Post by fenian on 2007-12-11
O,.K. first backup your xorg.conf with the command...
> 
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

now to edit the file...

> sudo gedit /etc/X11/xorg.conf

Change this...
> 
Section "ServerFlags"
	Option		"Xinerama"	"true"
EndSection

to this...

> Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

---

### Post by Garrulousbrevity on 2007-12-12
No change...

---

### Post by Garrulousbrevity on 2007-12-12
Update: 

Noticing that your xorg.conf file was much more sparse than mine, I hacked out a lot of the resolution information that had been added for my monitors.  There was no change.

Also, I tried to recreate the situation in which I had the TV only working, and I don't seem to be able to do it again.  

I did try it with my girlfriend's laptop again, and that worked fine.  So, I'm assured that the hardware is working.

---

### Post by fenian on 2007-12-12
I would try reinstalling the Nvidia driver and reconfiguring the xorg file.Start by removing the nvidia driver from the System>Admin. menu then restart the computer.When you get to the login window click options in the left corner and choose failsafe terminal this will  log you into a terminal enviroment login and the enter...

> sudo dpkg-reconfigure -phigh xserver-xorg

then reboot with> 

sudo reboot

Log in normally and reinstall the restricted driver restart and try to run nvidia-settings again.

---

### Post by Garrulousbrevity on 2007-12-12
No change.  my xorg looks a lot cleaner now, and I find that futsing with nvidia-settings doesn't send me to low graphics mode... but still nothing on the TV.  I've tried playing with different resolutions for the TV, but none of the choices has produced anything.  And as my girlfriend has pointed out several times over the last few hours, it works fine in Vista...

Anyway, new xorg looks like this:

---

### Post by fenian on 2007-12-12
I modified your xorg.conf with some settings that are similiar to those I have on another computer which has a 5200 but an older nvidia driver from before the nvidia-settings controls.I don't know if these settings will work with the newer driver,be sure to copy your 'working' xorg.conf.

Possible changes you could make to this file is where it says "UseDisplayDevice"
change those (there are two instances)to read "ConnectedMonitor"

---

### Post by Garrulousbrevity on 2007-12-12
> **fenian said:**
> I modified your xorg.conf with some settings that are similiar to those I have on another computer which has a 5200 but an older nvidia driver from before the nvidia-settings controls.I don't know if these settings will work with the newer driver,be sure to copy your 'working' xorg.conf.

Possible changes you could make to this file is where it says "UseDisplayDevice"
change those (there are two instances)to read "ConnectedMonitor"
No change with the xorg file you posted... changeing "UseDisplayDevice" to "ConnectedMonitor" displays on neither screen.

---

### Post by walmartshopper67 on 2007-12-16
I don't have a ton of time with school right now, but I have an Nvidia GEForce FX 5200 - and i'm running one monitor and a television - i have NEVER gotten beryl or compiz or compiz fusion to work correctly on this card, it always ends up with some blacked out screens - this may be because i'm running twinview. But here is my current WORKING xorg. I have a bunch of other xorgs (i save a copy every time i make a change, if you want one lemme know, or IM me on AIM - walmartshopper 67 and i can send you them. 

here it is: [http://ghettonet.no-ip.org/~gdev/xorg.conf](http://ghettonet.no-ip.org/~gdev/xorg.conf)

Good luck:)

---

### Post by Garrulousbrevity on 2007-12-29
Well, finals are over and I'm back home for a few weeks... so... my computer and the TV are about 300 miles apart, and my S-Video cable just doesn't quite reach.  This problem is on temporary hiatus.  Though the one thing I will check out, is to see if the missing pin from my first cable is still in my video card's S-Video port.

---

