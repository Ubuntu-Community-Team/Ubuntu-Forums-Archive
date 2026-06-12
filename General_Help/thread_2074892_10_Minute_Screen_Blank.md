---
title: "10 Minute Screen Blank"
date: 2012-10-22
forum: General Help
---

### Post by jim_deadlock on 2012-10-22
Since upgrading to 12.10 my screen goes black after 10 minutes idle. Where is the setting to change this? I've tried 'brightness and lock' and 'power settings', neither of which have any effect.

---

### Post by GreatDanton on 2012-10-22
I have this option under brightness and lock.

Regards.

EDIT: It's working for me

---

### Post by mardybear on 2012-10-22
Hi jim_deadlock

Do you have your screensaver set to activate onto a black/blank screen after 10 mins?

mardybear

---

### Post by jim_deadlock on 2012-10-22
With gnome-screensaver installed I was not able to access any options, even by running gnome-screensaver via ALT-F2 which I found strange. Anyway, I've solved this by uninstalling gnome-screensaver and switching to xscreensaver, which does the job.

However, ideally I would like to power off the screen rather than blank it. Is this possible?

---

### Post by bra|10n on 2012-10-22
Does **xset q** in a terminal show anything?

---

### Post by jim_deadlock on 2012-10-22
```
$ xset q

Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000002
  XKB indicators:
    00: Caps Lock:   off    01: Num Lock:    on     02: Scroll Lock: off
    03: Compose:     off    04: Kana:        off    05: Sleep:       off
    06: Suspend:     off    07: Mute:        off    08: Misc:        off
    09: Mail:        off    10: Charging:    off    11: Shift Lock:  off
    12: Group 2:     off    13: Mouse Keys:  off
  auto repeat delay:  500    repeat rate:  33
  auto repeating keys:  00ffffffdffffbbf
                        fadfffefffedffff
                        9fffffffffffffff
                        fff7ffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  2/1    threshold:  4
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  0
Colors:
  default colormap:  0x20    BlackPixel:  0x0    WhitePixel:  0xffffff
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/Type1,built-ins
DPMS (Energy Star):
  Standby: 1200    Suspend: 1200    Off: 1200
  DPMS is Disabled

```

---

### Post by bra|10n on 2012-10-22
Ok we can now see the 1200 sec (10 min) settings across the board. 
What is it you want to do?

---

### Post by jim_deadlock on 2012-10-22
I'd like to power off the display after 30 mins.

---

### Post by bra|10n on 2012-10-23
> **jim_deadlock said:**
> I'd like to power off the display after 30 mins.

Ok then I think *off after 30mins* is best handled by you power management settings.

Now, if I'm understanding your situation correctly your screen currently dims @ 10mins and therefore well before you want your screen turned off at 30mins?

If this is the case you can try ,
```
xset dpms 3600 3600 3600
xset s noblank
xset -dpms
```which should 'disable' dpms for an hour, or if that doesn't work try,
```
xset dpms 0 0 0
xset s noblank
xset -dpms
```which effectively turns off dpms.

The last line of code turns off dpms, however xset behaviour is buggy for some and not others. Go figure!

```
man xset
```will output more information on xset and other options available.
You'll need to see what works for you.
Good luck,.

---

### Post by robtygart on 2012-10-23
I have had this problem before and now again.. 

I would like mine to stay off, but when I do 

```
 xset -dpms
```
The next time I log back in dpms is back on.. 

Is there a way to keep it off?

---

### Post by whatthefunk on 2012-10-23
You could write a short script and have it run at startup.

---

### Post by ~LoKe on 2012-10-23
Add it in /etc/rc.local

```
gksu gedit /etc/rc.local
```
Add xset -dpms before "exit 0".  Should look like this:

> #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

xset -dpms

exit 0

---

### Post by jim_deadlock on 2012-10-23
@[bra|10n]("http://ubuntuforums.org/member.php?u=1069087")  I did look at man xset but the syntax looks complicated and I wasn't sure exactly what to do, so thanks for the commands, I'll play around with them and see what works.

---

### Post by bra|10n on 2012-10-23
Glad it's working :KS
~LoKe's post above is also a good idea if this becomes troublesome down the track...
cheers

---

### Post by danielbauwens on 2012-10-23
If you go to the Power Settings, you can make it suspend after 30 minutes.

I know you said power off, but this is pretty afective too.

---

### Post by jim_deadlock on 2012-10-23
I did try the suspend option in power settings but it seems to have no effect for me whatsoever. I'm on a desktop machine if that makes any difference. I'm sure those power settings used to have more options and used to be what I needed, maybe it's my imagination.

---

### Post by ontaiwolf on 2012-10-23
That's how I managed to disable the black screen, I just added a simple script to startup applications:

```
bash -c "xset s noblank; xset s off"
```

I think "xset s off" only could also do the job but "xset s noblank" makes it more safe... :D

---

### Post by beejee on 2012-10-24
Had the same problem, thanks for the fix info.

Shouldn't this be controlled by "brightness and lock" because right now the "Turn screen off when inactive for:" option has no effect on a clean install?

---

### Post by jim_deadlock on 2012-10-24
I'm running into another problem now. When I set:

xset dpms 0 0 1800

... it reverts to 0 0 0  after 60 seconds. Anyone know why and how to fix it?

---

### Post by kherring7383 on 2012-10-24
This is a pretty common issue with all versions of Ubuntu. First by default the gnome screensaver is installed and will blank the screen in about 10 minutes. So one of the fist things that I do  after a new install is to remove it and replace it with xscreensaver which you can access and choose a screensaver or none at all. 

From Terminal, run the following:

sudo apt-get purge gnome-screensaver
sudo apt-get install -y xscreensaver xscreensaver-gl-extra xscreensaver-data-extra

Once installed, restart and then look for xscreensaver in the Dash, run it and then configure what you want.

Something else you might try to disble screen from going blank after 10 minutes is install dconf-editor and then from Terminal run this command:

gsettings set org.gnome.desktop.screensaver idle-activation-enabled false

Hope this helps.

---

### Post by jim_deadlock on 2012-10-24
I have used xscreensaver but my aim is to power off the screen, not blank it. At the moment I have neither gnome-screensaver nor xscreensaver installed.

---

### Post by robtygart on 2012-10-24
> **~LoKe said:**
> Add it in /etc/rc.local

```
gksu gedit /etc/rc.local
```
Add xset -dpms before "exit 0".  Should look like this:

gksu is not working for me. It had me download gksu, when I use your command it asks me to log-in, but then it says incorrect password..

EDIT:

I omited "gksu" and downloaded gedit and I can now see the edit screen...
I will try that out 

Thank you 

Rob

---

### Post by bra|10n on 2012-10-24
> **jim_deadlock said:**
> I'm running into another problem now. When I set:

xset dpms 0 0 1800

... it reverts to 0 0 0  after 60 seconds. Anyone know why and how to fix it?

This is not something you want to keep fooling about with. 
If and when you find a setting that consistently works for you, you should just donate to your local charity. It can be frustrating...

Post exactly what you did to get this to the point that you marked this thread solved, *including* your power management settings.

---

### Post by bra|10n on 2012-10-24
> **robtygart said:**
> gksu is not working for me. It had me download gksu, when I use your command it asks me to log-in, but then it says incorrect password..

EDIT:

I omited "gksu" and downloaded gedit and I can now see the edit screen...
I will try that out 

Thank you 

Rob

LoKe's command was for Ubuntu.

FYI the correct way to start graphical app's with privileges in Kubuntu is kdesu, not gtksu which is for Ubuntu.
Then you need to substitute kate for gedit, as kate is the native text editor.
So,
```
kdesu kate /etc/rc.local
```There was no need to install gedit.

---

### Post by jim_deadlock on 2012-10-24
It's true, I did jump the gun :oops:

I did:

xset dpms 0 0 30

... in order to test it. It powered off my screen after 30 sec and I was happy at that point, so then I set it to the desired 30 mins:

xset dpms 0 0 1800

... but now, as I said, it reverts to 0 0 0 after 60 seconds and the screen never powers off.

I've also done:

xset s off

... which does seem to persist without any problem.

In my power settings I have "Suspend when inactive for [never suspend]" - I've also tried 5 mins, but it has no effect, screen stays on.

---

### Post by bra|10n on 2012-10-24
I'm not on Unity, but what if any power management settings do you have set?

---

### Post by jim_deadlock on 2012-10-24
In my power settings I have "Suspend when inactive for [never suspend]" - I've also tried 5 mins, but it has no effect, screen stays on.

I'm on Gnome Shell.

---

### Post by bra|10n on 2012-10-24
Enable all power/display related settings from the GUI and ensure all timeouts are set in excess of 30mins. 60mins should do. Then disable each of these options.

Run,
```
xset s noblank
```then,

```
xset dpms 0 0 1800
```Run xset -q and check the above is set...

Do not change any settings for 30 mins and wait to see the result. If your monitor switches off as desired then reboot. 

Run xset -q again before doing anything else. If the output matches the earlier run, test again for another 30 mins. It should switch the monitor off again. If this is the case then problem solved. Do not touch power/screen related settings again :KS

If the output has reverted to default settings I think you will have to run the codes again and use LoKe's script idea to load these settings on each reboot.

As I said, this can be finicky... even if you find success you can still run **xset -q** in a terminal while using different app's etc to check these app's haven't interfered with these settings. 
Video players have been known to do this...

---

### Post by jim_deadlock on 2012-10-24
This is more or less what I already tried, I did:

```
xset s off
xset dpms 0 0 1800
```

... then checked it with:

```
xset q
```

At this point it's correctly set. If I wait 65 seconds and do xset q again, it shows that it's reverted to 0 0 0 and I have no idea why. My power settings are set to never suspend (although whatever I set there makes no difference). From what you're saying something may be interfering with it but I don't know what.

Oh, and yes I have tried waiting the full 30 mins just to make sure, but the screen stays on.

---

### Post by wojox on 2012-10-24
What graphics card do you have jim_deadlock? I had similar issues in the past with nvidia cards/chips. I installed [caffine]("https://launchpad.net/caffeine") from the ppa.

---

### Post by jim_deadlock on 2012-10-24
NVIDIA GeForce GTX 550 Ti

---

### Post by wojox on 2012-10-24
You can control it better with Caffeine. If you want it on all the time add this to xorg.conf:
```
Section "ServerFlags"
    Option         "BlankTime" "0"
    Option         "NoPM" "1"
    Option         "StandbyTime" "0"
    Option         "SuspendTime" "0"
    Option         "OffTime" "0"
EndSection
```

---

### Post by Rotarychainsaw on 2012-11-21
I am having this same problem with an ATI card and the open source driver. Did you all ever come to an agreement on the proper steps to take to fix this?

---

### Post by jim_deadlock on 2012-11-21
I'll be honest, I gave up. In the end I uninstalled all power management and screensaver packages and I physically switch off my monitor when I go away. Sad but true.

---

