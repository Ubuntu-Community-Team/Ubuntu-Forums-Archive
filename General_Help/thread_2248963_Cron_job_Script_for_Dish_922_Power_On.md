---
title: "Cron job Script for Dish 922 Power On"
date: 2014-10-18
forum: General Help
---

### Post by aircarver on 2014-10-18
I recently added a Dish 922 satbox, replacing a Dish 211k.  The hitch is that the 922 shuts down after the 'overnight' data download.  With the 211k, the workaround was to set the Dish box to 'autotune' a program, which would turn the box back on, and it would stay on.  The 922 does not come on for an  autotune, and if you make a (throwaway) recording. it turns off after it's done.

A note:  The 922 is rf controlled by the remote, but can have ir turned on in the menus, so it can be controlled by ir blaster and also the ir remote from the 211k.  (And the rf control still works)
The 922 uses the same Dish ir blaster codes as the 211k, and worked with the existing 12.04 Mythbuntu setup, except for after it turns off after the data download.

I have read that a power on before a channel change is not a good way to do it (Delay before the box can accept the channel codes)

I need to make a cron job script that sends a 'power on' once daily (about 3:30 am) on the existing serial port lirc ir blaster that was only changing channels on the 211k.  How would I do that ?

---

### Post by tgalati4 on 2014-10-18
Do you know the keycode that is transmitted when hitting the the "Power On" button on the remote?

Open a terminal:

```
xev
```

Put the mouse cursor in the *xev* box and take note of the keycodes that get transmitted when you push the remote buttons.

Does the Dish922 box have a 7-pin serial connector in the back?  If so, you could wire up a 12VDC power-on by pulling 12VDC from one of your computer harddrive power wires.  Then the Dish box will stay powered on whenever the computer has power.

Otherwise you would simply echo the keycode to the serial port using a one-line script.  Then put that script into a cronjob.

This link refers to HDMI control, but the echo commands are similar.  [http://www.mythtv.org/wiki/HDMI-CEC](http://www.mythtv.org/wiki/HDMI-CEC)

---

### Post by aircarver on 2014-10-27
What I needed was how to do this with a cron job:

> crontab -e

{Brings up choice of editors)  [Pick nano]

Enter into the editor

> 25 4 * * * /usr/bin/change_channel.sh power_on

Save the entered text & exit from nano.

check the entry.

> crontab -l

You get:

> # Edit this file to introduce tasks to be run by cron.
#
# Each task to run has to be defined through a single line
# indicating with different fields when the task will be run
# and what command to run for the task
#
# To define the time you can provide concrete values for
# minute (m), hour (h), day of month (dom), month (mon),
# and day of week (dow) or use '*' in these fields (for 'any').#
# Notice that tasks will be started based on the cron's system
# daemon's notion of time and timezones.
#
# Output of the crontab jobs (including errors) is sent through
# email to the user the crontab file belongs to (unless redirected).
#
# For example, you can run a backup of all your user accounts
# at 5 a.m every week with:
# 0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
#
# For more information see the manual pages of crontab(5) and cron(8)
#
# m h  dom mon dow   command

25 4 * * * /usr/bin/change_channel.sh power_on


25 4 * * * /usr/bin/change_channel.sh power_on
This line will run every day at 25 minutes past 4 in the morning.  Right after the Dish box ran the downloads for the box at 4 am.  (My setting ... dish defaults to doing this at 3 am.)

/usr/bin/change_channel.sh is where I have the channel change script for the ir blaster, and is kind of standard.  If yous is different use that.  It needs to be the same as the entry you put in the backend setup if the input connections for the video card (This case a HD-PVR)

Dish Network will no longer mess up your early morning recordings because the Sat Box was off and displaying the Dish logo screensaver .....:p

---

