---
title: "How to install dual monitor command file permanently"
date: 2013-10-27
forum: General Help
---

### Post by jgrauca on 2013-10-27
Hello,
I run xubuntu 13.10 on my desktop with two monitors. 
In Settings Manager I created a .sh file with ArandR to get a extended Desktop.
Each time I restart, I have to execute the .sh file again. 
The script looks like this:
> [I]#!/bin/sh
xrandr --output VGA-0 --mode 1920x1080 --pos 0x0 --rotate normal --output DVI-0 --mode 1920x1080 --pos 1920x0 --rotate normal[/I]

What do I have to do .....to get this command executed at boot? 
In other words: .....to have it installed permanently?

---

### Post by TheFu on 2013-10-27
There are different ways depending on your GPU.  In the end, modifying the /etc/X11/xorg.conf file is what happens.
For nvidia, this: [http://blog.jdpfu.com/2010/05/12/ubuntu-10-04-dual-monitor-with-nvidia-driver](http://blog.jdpfu.com/2010/05/12/ubuntu-10-04-dual-monitor-with-nvidia-driver) explains.

---

### Post by Toz on 2013-10-27
In addition to @TheFu's suggestion, you could also try to use lightdm's "display-setup-script" parameter. To do this, save the script to /usr/local/bin/ (for example as /usr/local/bin/displaysetup.sh) and make the file executable. Then edit **/etc/lightdm/lightdm.conf** and add the line:
```
display-setup-script=/usr/local/bin/displaysetup.sh
```
...to the end of the file and reboot to test.

---

### Post by jgrauca on 2013-10-27
Thank you both, TheFu and Toz, for the prompt response...
My hardware is:
Processor             >>> AMD Athlon II X2 240 on MSI 785GM-E51 Mainboard 
integrated Graphic >>>ATI Radeon HD4200GPU
I put this information here before I try your suggestions in case it needs a different approach!

---

### Post by SantaFe on 2013-10-27
Despite my board name, I'm NOT trying to derail this topic, but was wondering if this would work in KDM as well?  Or how to do it, as I'm having the same trouble as the OP.  Thanks! ;)

---

### Post by Toz on 2013-10-27
> **SantaFe said:**
> Despite my board name, I'm NOT trying to derail this topic, but was wondering if this would work in KDM as well?  Or how to do it, as I'm having the same trouble as the OP.  Thanks! ;)

Either solution _should_ work, yes. If you've got time, maybe you can try both and report back the results?

---

### Post by TheFu on 2013-10-27
My solution does NOT care which DE or login manager you use.  It is related ONLY to the GPU and xorg.conf ... which any LinuxOS running a GUI will use ... er ... until Canonical stops using X/Windows.  But all the other distros will and Ubuntu will have the X/Windows as an option forever, I bet.

---

### Post by jgrauca on 2013-10-27
> **Toz said:**
> In addition to @TheFu's suggestion, you could also try to use lightdm's "display-setup-script" parameter. To do this, save the script to /usr/local/bin/ (for example as /usr/local/bin/displaysetup.sh) and make the file executable. Then edit **/etc/lightdm/lightdm.conf** and add the line:
```
display-setup-script=/usr/local/bin/displaysetup.sh
```
...to the end of the file and reboot to test.



After restart, boot stops in a dead lock ---> see attachment!
I could only get out of it by "hardware reset" and new xubuntu installation.
What could have gone wrong?
I'm not sure if I made the file executable...Here are the screenshots 02,03 to show what I did. 
I wonder if this is correct?

---

### Post by Toz on 2013-10-28
Yipes! I've used this method successfully on a number of occassions. Sorry you had to resort to a full re-install. For future reference, instead of re-installing, you could try to go to a text console (Ctrl+Alt+F1) and undo the change or, if the text console is unavailable, boot into [recovery mode]("https://wiki.ubuntu.com/RecoveryMode") and undo the change.

Looking at your screenshots, the issue may have been the ownership and permissions of the file. You have:
> -rxw------ 1 jg jg 136 ...etc
...I would have left it at the default:
```
-rwxr-xr-x 1 1 root root 136 ...etc
```
...as I believe the script is run by the lightdm user, who would not have had access to that file with the permissions you set. It might have hung the process.

---

### Post by TheFu on 2013-10-28
Looks like someone is ready for a tutorial on Linux/UNIX file permissions. 30 minutes now will pay off for the next 40+ yrs. Trust me.
To find a tutorial - google "tutorial Linux UNIX file permissions"
The first page of results seemed reasonable to me.

---

### Post by Cariboo1938 on 2013-10-29
> **Toz said:**
> Yipes! I've used this method successfully on a number of occassions. Sorry you had to resort to a full re-install. For future reference, instead of re-installing, you could try to go to a text console (Ctrl+Alt+F1) and undo the change or, if the text console is unavailable, boot into [recovery mode]("https://wiki.ubuntu.com/RecoveryMode") and undo the change.
Looking at your screenshots, the issue may have been the ownership and permissions of the file. You have:
...I would have left it at the default:
```
-rwxr-xr-x 1 1 root root 136 ...etc
```
...as I believe the script is run by the lightdm user, who would not have had access to that file with the permissions you set. It might have hung the process.

I got a little further....No dead lock after 'Restart':D ...but still not permanent. I had to run Arandr again to get the Dual Monitor setting. 

It seems there is still something missing, but I can't figure it out. 
I attached the screenshots of Ownership/Permission and lightdm.conf and the screenlayout.sh file. I'm just wondering if it is necessary to make *lightdm.conf* executable too?

---

### Post by Toz on 2013-10-29
Lightdm.conf does not need to be made executable.

Instead of running arandr to fix the issue, can you instead run:
```
/usr/local/bin/screenlayout.sh
```
...and see if it sets up the monitor configuration correctly?

There are also lightdm log files in /var/log/lightdm. Of interest would be lightdm.log. You'll need root privledges to view the file. Try:
```
sudo -i mousepad /var/log/lightdm/lightdm.log
```
...to view the file. Copy the contents and paste back in between **[noparse]```
 
```[/noparse]** tags.

---

### Post by Cariboo1938 on 2013-10-29
> **Toz said:**
> Lightdm.conf does not need to be made executable.
Instead of running arandr to fix the issue, can you instead run:
```
/usr/local/bin/screenlayout.sh
```
...and see if it sets up the monitor configuration correctly?

[COLOR="#0000FF"]I put the screenlayout.sh on the Desktop and after boot, when I get the mirrored monitors only, 
I execute the .sh file dirctly from there. 
It does the same as running */usr/local/bin/screenlayout.sh* from the terminal.[/COLOR]

> **Toz said:**
> 
There are also lightdm log files in /var/log/lightdm. Of interest would be lightdm.log. You'll need root privledges to view the file. Try:
```
sudo -i mousepad /var/log/lightdm/lightdm.log
```
...to view the file. Copy the contents and paste back in between **[noparse]```
 
```[/noparse]** tags.

[COLOR="#0000FF"]Here is the lightdm log-file[/COLOR]
```
[B][+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.8.2, UID=0 PID=979
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: Registered seat module xlocal
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Registered seat module unity
[+0.00s] DEBUG: Registered seat module surfaceflinger
[+0.00s] DEBUG: Adding default seat
[+0.00s] DEBUG: Seat: Starting
[+0.00s] DEBUG: Seat: Creating greeter session
[+0.00s] DEBUG: Seat: Setting XDG_SEAT=seat0
[+0.00s] DEBUG: Seat: Creating display server of type x
[+0.00s] DEBUG: Seat: Starting local X display
[+0.02s] DEBUG: Deactivating Plymouth
[+0.04s] DEBUG: Using VT 7
[+0.04s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+0.04s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+0.04s] DEBUG: DisplayServer x-0: Launching X Server
[+0.04s] DEBUG: Launching process 993: /usr/bin/X -core :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.06s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+0.06s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.06s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.71s] DEBUG: Got signal 10 from process 993
[+0.71s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+0.71s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+0.71s] DEBUG: Quitting Plymouth; retaining splash
[+0.73s] DEBUG: Launching process 1017: /usr/local/bin/screenlayout.sh
[+0.86s] DEBUG: Process 1017 exited with return value 0
[+0.86s] DEBUG: Seat: Exit status of /usr/local/bin/screenlayout.sh: 0
[+0.86s] DEBUG: Seat: Display server ready, starting session authentication
[+0.86s] DEBUG: Session: Setting XDG_VTNR=7
[+0.86s] DEBUG: Session pid=1024: Started with service 'lightdm-greeter', username 'lightdm'
[+1.03s] DEBUG: Session pid=1024: Authentication complete with return value 0: Success
[+1.03s] DEBUG: Seat: Session authenticated, running command
[+1.03s] DEBUG: Session pid=1024: Setting XDG_VTNR=7
[+1.03s] DEBUG: Session pid=1024: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/lightdm-gtk-greeter
[+1.05s] DEBUG: Session pid=1024: Logging to /var/log/lightdm/x-0-greeter.log
[+1.06s] DEBUG: Activating VT 7
[+1.49s] DEBUG: Session pid=1024: Greeter connected version=1.8.2
[+2.34s] DEBUG: Session pid=1024: Greeter start authentication for jg
[+2.34s] DEBUG: Seat: Setting XDG_SEAT=seat0
[+2.34s] DEBUG: Session: Setting XDG_VTNR=7
[+2.34s] DEBUG: Session pid=1099: Started with service 'lightdm', username 'jg'
[+2.35s] DEBUG: Session pid=1099: Got 1 message(s) from PAM
[+2.35s] DEBUG: Session pid=1024: Prompt greeter with 1 message(s)
[+13.63s] DEBUG: Session pid=1024: Continue authentication
[+13.65s] DEBUG: Session pid=1099: Authentication complete with return value 0: Success
[+13.65s] DEBUG: Session pid=1024: Authenticate result for user jg: Success
[+13.67s] DEBUG: Session pid=1024: User jg authorized
[+13.67s] DEBUG: Session pid=1024: Greeter sets language en_CA
[+13.71s] DEBUG: Writing /home/jg/.dmrc
[+13.80s] DEBUG: Session pid=1024: Greeter requests session xubuntu
[+13.84s] DEBUG: Writing /home/jg/.dmrc
[+13.92s] DEBUG: Seat: Stopping greeter; display server will be re-used for user session
[+13.92s] DEBUG: Session pid=1024: Sending SIGTERM
[+13.92s] DEBUG: Session pid=1024: Exited with return value 0
[+13.92s] DEBUG: Seat: Session stopped
[+13.92s] DEBUG: Seat: Greeter stopped, running session
[+13.92s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+13.92s] DEBUG: Session pid=1099: Setting XDG_VTNR=7
[+13.92s] DEBUG: Session pid=1099: Running command /usr/sbin/lightdm-session startxfce4
[+13.92s] DEBUG: Session pid=1099: Logging to .xsession-errors
[+13.94s] DEBUG: Activating VT 7
[/B]
```

---

### Post by Toz on 2013-10-29
Can you also try adding:
```
session-setup-script=/usr/local/bin/screenlayout.sh
```
...to the end of /etc/lightdm/lightdm.conf?

---

### Post by Cariboo1938 on 2013-10-29
> **Toz said:**
> Can you also try adding:
```
session-setup-script=/usr/local/bin/screenlayout.sh
```
...to the end of /etc/lightdm/lightdm.conf?

Nope, didn't do the trick...

As you can see, the file *screenlayout* is located in [I]/usr/local/bin
[/I] and the end line of line *ightdm.conf* is now ```
session-setup-script=/usr/local/bin/screenlayout.sh 
```

but I still have the same display on both monitors.

---

### Post by Toz on 2013-10-30
Hmm.

Can you try putting the command in **.xprofile** in your home directory?
```
mousepad ~/.xprofile
```
...and copy/paste:
```
#!/bin/sh
xrandr --output VGA-0 --mode 1920x1080 --pos 0x0 --rotate normal --output DVI-0 --mode 1920x1080 --pos 1920x0 --rotate normal
```
...save the file and make it executable:
```
chmod +x ~/.xprofile
```
...and try it again?

---

### Post by Cariboo1938 on 2013-10-30
nope...I again have to execute screenlayout.sh (in my case,from /home/jg/Dektop) after a reboot. 
Do I have to bring *lightdm.conf* first back to the originale state?

---

### Post by Toz on 2013-10-30
The .xprofile file is owned by root in your home directory - this one should be owned by you. Try:
```
sudo chown jg:jg ~/.xprofile
```
...and try again.

I've used the lightdm procedure successfully in the past. If I have time today, I'm going to hook up my external monitor to my 13.10 install and have a closer look. Maybe there has been some sort of regression in lightdm.

---

### Post by Cariboo1938 on 2013-10-30
Still not working...
BTW:
 I thank you so much for your patience and support...I am really interested how to solve the issue;)

---

### Post by Toz on 2013-10-30
Was able to do some testing this morning. 

xrandr in the lightdm configuration files no longer works for me either - must be a regression (or change) in lightdm. 

.xprofile worked for me. My .xprofile file:
```
#!/bin/bash
xrandr --output DP2 --auto --right-of LVDS1
```
..and:
```
$ ls -al  |grep xprofile
-rwxr-xr-x  1 toz  toz    132 Oct 30 10:36 .xprofile
```

Can you try with a small delay in the file and using the bash shell:
```
#!/bin/bash
sleep 3
xrandr --output VGA-0 --mode 1920x1080 --pos 0x0 --rotate normal --output DVI-0 --mode 1920x1080 --pos 1920x0 --rotate normal
```

Also check your ~/.xsession-errors file for any xrandr errors:
```
cat ~/.xsession-errors
```

---

### Post by Cariboo1938 on 2013-10-30
No change... 
the screenlayout.sh and the .xprofile contain the same code, both can be executed with a mouse click and work just great.
But, for some reason ](*,), they do not work at start after a shutdown or restart....

---

### Post by Toz on 2013-10-30
*scratches zombie head

Can you try this in .xprofile:
```

#!/bin/bash
xrandr --output VGA-0 --mode 1920x1080 --pos 0x0 --rotate normal --output DVI-0 --mode 1920x1080 --pos 1920x0 --rotate normal | tee /home/jg/.xsession-errors

```
...and afterwards, post back again the contents of .xsession-errors? (I added a tee command to the end of the xrandr command so it outputs its results to .xsession-errors)

---

### Post by TheFu on 2013-10-30
> **Cariboo1938 said:**
> No change... 
the screenlayout.sh and the .xprofile contain the same code, both can be executed with a mouse click and work just great.
But, for some reason ](*,), they do not work at start after a shutdown or restart....

For all the stuff you've tried, I'm confused as to why editing the /etc/X11/xorg.conf file hasn't been used.  This is THE STANDARD way to solve this.  15 minutes of learning and you'd be done.

Also, if you use ATI or nvidia GPUs, then those both have tools to make this easier ... -ish.  The link I provided very early explains.

I must have missed something in the last 3 pgs of msgs.

---

### Post by Cariboo1938 on 2013-10-30
> **TheFu said:**
> For all the stuff you've tried, I'm confused as to why editing the /etc/X11/xorg.conf file hasn't been used.  This is THE STANDARD way to solve this.  15 minutes of learning and you'd be done.

Also, if you use ATI or nvidia GPUs, then those both have tools to make this easier ... -ish.  The link I provided very early explains.

I must have missed something in the last 3 pgs of msgs.

I use ATI and I did not (do not want to)  install Catalyst...therefor I try to get it work the "Toz's way"!

---

### Post by Cariboo1938 on 2013-10-30
> **Toz said:**
> *scratches zombie head
...and afterwards, post back again the contents of .xsession-errors? (I added a tee command to the end of the xrandr command so it outputs its results to .xsession-errors)

Here old and new xsession errors....

---

### Post by Toz on 2013-10-30
There's nothing in your .xsession-errors file? Can you confirm that its empty?

---

### Post by Cariboo1938 on 2013-10-30
> **Toz said:**
> There's nothing in your .xsession-errors file? Can you confirm that its empty?

I hope this is a valid way to confirm that .xsession-error file is empty. If I open it with mousepad I get a blank sheet.

---

### Post by TheFu on 2013-10-31
> **Cariboo1938 said:**
> I use ATI and I did not (do not want to)  install Catalyst...therefor I try to get it work the "Toz's way"!


Agreed, but catalyst is NOT needed to type in 15 lines into the xorg.conf file.  I've got to be missing something. This is not GPU specific.  Something like:
```

    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT-0: 1920x1200 +0+0, CRT-1: 1920x1080 +1920+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
```

---

### Post by dozynsleepy on 2013-10-31
I'm running Xubuntu 13.10 on a Dell Vostro laptop with a Samsung external monitor on hdmi.

These are the steps I use to retain the dual monitor configuration between reboots.

sudo apt-get install arandr
or Search for ARandR in the Ubuntu Software Centre and install it from there

Start -> Settings Manager
 
Under hardware select "Display"
Select the first display and ensure that the "Use this output" checkbox is checked.
Set the Resolution to the correct resolution for the display
Repeat for the second display, making sure that the "Use this output" is checked.

Press "All Settings" to return to the Settings dialog

Under hardware select the ARandR button (or run arandr from a terminal)
This displays the Screen Layout Editor.
Select "Outputs" and for each display ensure that 
"Active" is checked.
Resolution matches the monitor resolution.
Drag the displays to the position you want them.
Select "Layout" "Apply"
Select "Layout" "Save As"
It will store the file in your home directory under ~/.screenlayout
Name it something like "dualmonitor.sh"
Select "Layout" "Quit"
You now have a file  ~/.screenlayout/dualmonitor.sh

Which for me looks like this
#!/bin/sh
xrandr --output HDMI1 --mode 1920x1080 --pos 0x0 --rotate normal --output LVDS1 --mode 1366x768 --pos 1920x0 --rotate normal --output DP1 --off --output VGA1 --off


In the Settings dialog select "Session and Startup" in  "Sytem"
This will display the "Session and Startup" dialog box.
Select the "Application Autostart" tab
Press "Add"
Name: arandr_dualscreen
Description: Setup dual display
Command: browse to your home directory and select .screenlayout/dualmonitor.sh
or type it in /home/USERNAME/.screenlayout/dualmonitor.sh
Press OK

This will execute ~/.screenlayout/dualmonitor.sh when you login to your desktop.

---

### Post by Cariboo1938 on 2013-10-31
> **TheFu said:**
> ........ to type in 15 lines into the xorg.conf file.......... Something like:

Thank you TheFu...here is my problem. I'm not a software developer and I depend on completed codes.
Your suggested code seems not to be complete (10 lines instead of 15) and it is far over my head to figure out what the 
missing lines would have to be.
I'm certain that there is a solution to this issue - to get a manual executable file automatic executable - but I do not know how to do it.

---

### Post by Cariboo1938 on 2013-10-31
> **dozynsleepy said:**
> 
This will execute ~/.screenlayout/dualmonitor.sh when you login to your desktop.

That's It! :KS

Thank you dozynsleepy ... I knew it...It had to be a straight forward solution...Issue [SOLVED]

Thank you, TheFu and Toz,  as well for your inputs...

---

### Post by Brian_Haberman on 2014-09-18
A user named stealz found a pretty elegant way to do this which worked for me.  Look under **Weird and limited Dual Monitor behaviour at **[http://ubuntuforums.org/showthread.php?t=2227913](http://ubuntuforums.org/showthread.php?t=2227913).

---

