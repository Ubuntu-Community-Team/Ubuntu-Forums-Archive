---
title: "Starting a script before Startx or xorg.conf loads"
date: 2007-01-25
forum: General Help
---

### Post by Joseph Brown on 2007-01-25
I am trying to make changes to the xorg.conf before startx accesses it. I am running Ubuntu 6.10 and have tried many things. I do know that placing the script in /etc/init.d does not work and adding the information into /home/user/.xinitrc does not work.

---

### Post by kerry_s on 2007-01-25
What? I'm not understanding, Why do you need to modify xorg.conf at startup? Normally you would just setup xorg.conf the way you want and it's done. Is there some setting that is not staying when you set it?

---

### Post by Joseph Brown on 2007-01-25
I have a laptop and I want the system to notice whether I am booting with external dual monitors or the laptop LCD. I am using ddcprobe to detect the different configurations and I am using a script to copy over the xorg.conf file. The script works fine but startx is initialize before the xorg is copied down. I need to find a place to run the script before startx is kicked off.

---

### Post by kerry_s on 2007-01-25
That makes since, startx is a simple /bin/bash script, you might try putting your script in the startx script so it runs your script first before the rest of the startx script. Make a back up first then> sudo gedit /usr/bin/startx
Good luck.

---

### Post by lswb on 2007-01-25
Did you try to call your script from '/etc/rc.local' ? 

It sounds like using udev rules would be a reasonable approach to what you want to do also.  Check 'man udev' to get an idea of what it's about and look for a howto on using udev rules. The idea is that at startup or whenever the kernel detects a hardware change, the rules files in /etc/udev/rules.d are executed; From there you can run programs, make symbolic links, etc.

Larry

---

### Post by Joseph Brown on 2007-01-25
Copying it to startx did not work. I think if might be because the GDM uses another method to start the Xserver. I wish I knew which script pulls the data from xorg.conf. Kerry thanks for the advise.

---

### Post by Joseph Brown on 2007-01-25
Tried rc.local.. no worky

---

### Post by Praetorian65 on 2007-01-25
Place in init.d, type in console "sudo update-rc.d /etc/init.d/yourscript defaults".

Try that.

---

### Post by kerry_s on 2007-01-25
> **Joseph Brown said:**
> Copying it to startx did not work. I think if might be because the GDM uses another method to start the Xserver. I wish I knew which script pulls the data from xorg.conf. Kerry thanks for the advise.

When i press ctrl + alt + F1 i see the last thing called was gnome display manager(GDM) so i think you need to look at /etc/gdm/Xsession which looks to me like what is setting up the display.> gedit /etc/gdm/Xsession <to look at it.

---

### Post by Joseph Brown on 2007-01-26
My first attempt was to put in the /etc/init.d folder. I did run the update-rc.d. I have tried putting it in rc.local. I have tried creating .xinitrc file in my home directory and adding the script in. I have placed it in gdm.config-custom and in Xsession. I have added it into /usr/bin/startx, but I think that gdm loads the x server a differnt way than using startx. Permission appear to be fine the xorg file is being copied but it appears to be after what script reads the xorg file.

---

### Post by kerry_s on 2007-01-26
Check in /usr/bin and see if there's a startgnome, i don't have gnome, but on this Xubuntu install there's startxfce4, that also has commands to set up display in it(starts at line 37 on mine). I have a feeling gdm uses that instead of startx.

---

### Post by kerry_s on 2007-01-26
Can you post the code for your monitor script your trying to use, i'd like to try using my laptop and see if i can figure it out. Thanks

---

### Post by Joseph Brown on 2007-01-26
#!/bin/sh
#/etc/init.d/xorg.conf_switcher.sh
#Determine if the laptop LCD display is active.
#When local lcd is present "LPL0000" is in ddcprobe.
if /usr/sbin/ddcprobe | grep "LPL0000"; then
	echo "Laptop LCD is active."> /home/username/test.txt
#Copy default single screen xorg file to xorg.conf.
	cp /etc/X11/xorg_local.conf /etc/X11/xorg.conf
else
	echo "An external display is active." > /home/username/test.txt
#Copy dual screen xorg file to xorg.conf.
	cp /etc/X11/xorg_external.conf /etc/X11/xorg.conf
fi

exit 0

---

### Post by Joseph Brown on 2007-01-26
I have finally found the fix. I call my code from the /etc/init.d/gdm file. I placed it in as the first line of code and it works. Thanks for everyone help.

---

### Post by kerry_s on 2007-01-26
That's Fantastic! I knew it had to be gdm related. I just couldn't visualize what you were doing from my end, and i was starting to think it might be the script itself. Very nice script by the way, i'm guessing you have 2 xorg.conf files already set up, but what is this part for "/home/username/test.txt" is that just a log?

---

### Post by kerry_s on 2007-01-26
One more thing can you post the /etc/init.d/gdm file, just in case others want to do the same thing, it would be better if they can see what/how you actually put it. Thanks.

---

### Post by Joseph Brown on 2007-01-26
The >/home/username/text.txt (username = user logging in) outputs the echo statements to a txt file. This was to help me troubleshoot if the script was detecting the correct monitor settings.

---

### Post by kerry_s on 2007-01-26
Okay, so it's a log(lol). "LPL0000" that's the id(using ddcprobe) of your monitor, meaning it's specific to your setup. I would want to change this, to something that would just detect any monitor. 

Have you tried going down that road yet?

The reason this interests me is because i do alot of setups for friends and family and it would be nice to just throw that script in there just in case they go external, but there would be no way of knowing what they hook up to before hand, so it would be nice if it were more automatic instead of specific.

What'cha think?

---

### Post by Joseph Brown on 2007-01-26
Follow-up How To: Laptop Profiling for a local LCD and external Dual Monitors on Ubuntu 6.10

I. Backup current xorg.conf file. Create an xorg.conf file for the laptop LCD and one for the dual monitors connected to a docking station. ie. xorg_local.conf/xorg_external.conf
II. Make sure that Ubuntu has xresprobe. This is needed because you will need to use the ddcprobe command to get the monitor settings from the system. The xresprobe package can be loaded from synaptic or from terminal with the following command:
```
sudo apt-get xresprobe
```
III. Write a script that will use ddcprobe to determine what devices are connected and based on the results copy the correct xorg.conf file to /etc/X11.
```
#!/bin/sh
#/usr/local/bin/xorg.conf_switcher.sh
#Determine if the laptop LCD display is active.
#When local lcd is present "LPL0000" is in ddcprobe.
if /usr/sbin/ddcprobe | grep "LPL0000"; then
echo "Laptop LCD is active."
#Copy default single screen xorg file to xorg.conf.
cp /etc/X11/xorg_local.conf /etc/X11/xorg.conf
else
echo "An external display is active."
#Copy dual screen xorg file to xorg.conf.
cp /etc/X11/xorg_external.conf /etc/X11/xorg.conf
fi
exit 0
```
IV. Next you will need to save this script to a location. i.e. /usr/local/bin/xorg.conf_switcher.sh
V. Make sure the script is executable and that the permissions are set correctly.
```
sudo chmod +x xorg.conf_switcher.sh
sudo chmod 755 xorg.conf_switcher.sh
```
VI. Then add the following line into the /etc/init.d/gdm file. Make sure it is in the first line of code ran. i.e.
```
#! /bin/sh
#
# Originally based on:
# Version:      @(#)skeleton  1.8  03-Mar-1998  miquels@cistron.nl
#
# Modified for gdm, Steve Haslam <steve@arise.dmeon.co.uk> 14mar99
# modified to remove --exec, as it does not work on upgrades. 18jan2000
# modified to use --name, to detect stale PID files 18mar2000
# sleep until gdm dies, then restart it 16jul2000
# get along with other display managers (Branden Robinson, Ryan Murray) 05sep2001
[COLOR="Red"]# Call the xorg.conf_switcher.sh command to copy the correct xorg.conf file to /etc/X11
 /usr/local/bin/xorg.conf_switcher.sh[/COLOR]

set -e

# To start gdm even if it is not the default display manager, change
# HEED_DEFAULT_DISPLAY_MANAGER to "false."
HEED_DEFAULT_DISPLAY_MANAGER=true
DEFAULT_DISPLAY_MANAGER_FILE=/etc/X11/default-display-manager
PATH=/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/sbin/gdm
PIDFILE=/var/run/gdm.pid
UPGRADEFILE=/var/run/gdm.upgrade

```
VII. This should complete the customization.

---

### Post by Joseph Brown on 2007-01-26
Correct, LPL0000 is specific to my Dell D620 local LCD. You could grep anything out of the ddcprobe that would be different between the setups. I did it this way because I have a Belkin KVM and while connected to it ddcprobe will not detect the monitor type or monitor serial number. They just show up blank. Without the KVM and connected directly to the monitors you could use Dell 1907FP or the serial of the external monitor.

---

### Post by kerry_s on 2007-01-26
Yeah, i'm sure it can be simplified a little. I'll have to look into it a bit more, i'm a little busy right now though, i got to clean the house and the kids are coming this weekened, so i'm going to have to put this off for now till i get more time. I'll let you now if i come up with a easier way. Thank you  for the quick tutorial. Catch you later.

---

