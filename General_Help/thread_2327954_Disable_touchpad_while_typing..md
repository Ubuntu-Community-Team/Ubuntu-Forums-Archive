---
title: "Disable touchpad while typing."
date: 2016-06-16
forum: General Help
---

### Post by Roasted on 2016-06-16
Hello friends. I'm working with a Dell Inspiron 15 5000 series laptop with Ubuntu 16.04. Fresh install. I noticed that the touchpad made me want to light things on fire, as it's sensitivity to palms when typing is a bit irritating. I went into mouse and touchpad in the system settings and didn't see my old friend known as "disable touchpad when typing."

So the search began. I tried a few different things.

gsettings set org.gnome.settings-daemon.peripherals.touchpad disable-while-typing true (which says not found)

syndaemon -i 1 -K -d (which does nothing)

Using synclient, set the palm detection to 1 (which does nothing)

I also tried the below:
xinput set-prop "Touchpad Name" "Synaptics Noise Cancellation" 20 20
xinput set-prop "Touchpad Name" "Synaptics Finger" 50 90 255
which didn't help :(

Installed Touchpad-Indicator from the atareao PPA and set it to have a 7 (yes, 7) second delay to re-activate the touchpad. This also did nothing.

I'm fully updated... not really sure what else I can try. Any suggestions?

---

### Post by sudodus on 2016-06-16
In standard Ubuntu 16.04 LTS, up to date (updated and dist-upgraded), it is easy for me to turn off the touchpad completely via

*System settings (the icon with a cog wheel and a wrench) -- Mouse and touchpad*

Click on the switch at the right side of the window to toggle  it off / on (and close the window).

You can also test if you can keep the touchpad on with the other settings off (tap to click, two finger scroll ...)

-o-

In Xubuntu and Lubuntu the methods you describe with synclient and syndaemon work, but not in standard Ubuntu. I have not tried in the other flavours.

---

### Post by Roasted on 2016-06-16
Thanks for your response, but I don't want to disable the touchpad all the time. I just wanted to automatically disable it while typing. There used to be a setting for this within the system settings menu, but I can't seem to find it now. Likewise, I find it a little concerning that all the above attempts did not bring a fix either.

---

### Post by vasa1 on 2016-06-16
> **Roasted said:**
> ...
gsettings set org.gnome.settings-daemon.peripherals.touchpad disable-while-typing true (which says not found)
...
Maybe you could try this on your system:```
11:57 AM ~ $ **gsettings list-recursively | grep touch**
org.gnome.desktop.peripherals.touchpad natural-scroll false
org.gnome.desktop.peripherals.touchpad click-method 'default'
org.gnome.desktop.peripherals.touchpad scroll-method 'two-finger-scrolling'
org.gnome.desktop.peripherals.touchpad left-handed 'mouse'
org.gnome.desktop.peripherals.touchpad send-events 'enabled'
org.gnome.desktop.peripherals.touchpad tap-to-click false
org.gnome.desktop.peripherals.touchpad speed 0.0
org.gnome.desktop.peripherals.touchpad natural-scroll false
org.gnome.desktop.peripherals.touchpad click-method 'default'
org.gnome.desktop.peripherals.touchpad scroll-method 'two-finger-scrolling'
org.gnome.desktop.peripherals.touchpad left-handed 'mouse'
org.gnome.desktop.peripherals.touchpad send-events 'enabled'
org.gnome.desktop.peripherals.touchpad tap-to-click false
org.gnome.desktop.peripherals.touchpad speed 0.0
org.gnome.desktop.peripherals.touchscreen display ['', '', '']
11:57 AM ~ $ 
```
to get an idea of which gsettings are available for you.


And re. "Using synclient, set the palm detection to 1 (which does nothing)", how exactly did you do that? For example, I have "synclient VertEdgeScroll=0" in my autostart. No spaces before and after "=".

---

### Post by Bucky Ball on 2016-06-16
The confusion may be happening due to the mouse being selected in 'Mouse and touchpad' rather than the touchpad. There is a drop-down box with two entries. One should be 'synaptic touchpad' or something like that, the other entry should be for the mouse. 

Make sure you are disabling the touchpad, not the mouse. Apologies if this is completely obvious and you've already tried it ...

---

### Post by Roasted on 2016-06-16
I'm not seeing a drop down... This is what I'm seeing: [http://i.imgur.com/EeORBB5.png](http://i.imgur.com/EeORBB5.png)

Where tap to click, two finger scroll, etc. are, I recall seeing a "disable touchpad while typing" button. This setting specifically disabled the touchpad when keystrokes were recognized. I know I can turn the touchpad on and off manually, but there was a dedicated setting to keep the touchpad off for automatic + temporary intervals when typing. As it stands now, this brand new laptop's usability is considerably poor with the touchpad selecting frequently at random while typing, so locating this functionality is a must. :(

Here's the gsettings output (I grep'd touchpad instead of touch as I was getting a lot of touchscreen entries mixed in here too)
```
gsettings list-recursively | grep touchpad
org.gnome.settings-daemon.plugins.media-keys.custom-keybindings.touchpad-indicator binding ''
org.gnome.settings-daemon.plugins.media-keys.custom-keybindings.touchpad-indicator command '/usr/bin/python3 /opt/extras.ubuntu.com/touchpad-indicator/share/touchpad-indicator/change_touchpad_state.py'
org.gnome.settings-daemon.plugins.media-keys.custom-keybindings.touchpad-indicator name 'Touchpad indicator'
org.gnome.desktop.peripherals.touchpad natural-scroll false
org.gnome.desktop.peripherals.touchpad click-method 'default'
org.gnome.desktop.peripherals.touchpad scroll-method 'two-finger-scrolling'
org.gnome.desktop.peripherals.touchpad left-handed 'mouse'
org.gnome.desktop.peripherals.touchpad send-events 'enabled'
org.gnome.desktop.peripherals.touchpad tap-to-click true
org.gnome.desktop.peripherals.touchpad speed 0.0
org.gnome.desktop.peripherals.touchpad natural-scroll false
org.gnome.desktop.peripherals.touchpad click-method 'default'
org.gnome.desktop.peripherals.touchpad scroll-method 'two-finger-scrolling'
org.gnome.desktop.peripherals.touchpad left-handed 'mouse'
org.gnome.desktop.peripherals.touchpad send-events 'enabled'
org.gnome.desktop.peripherals.touchpad tap-to-click true
org.gnome.desktop.peripherals.touchpad speed 0.0

```

Thanks for the help, everyone!

---

### Post by vanadium on 2016-06-16
Take a look here: [http://ubuntuforums.org/showthread.php?t=2316240](http://ubuntuforums.org/showthread.php?t=2316240). This is what saved me on a Dell XPS 13 9350. As in the linked thread, two touchpad drivers appeared to be active. syndaemon was loaded, but probably talking to the wrong driver. I disabled the SynPS/2 Synaptics TouchPad as outlined in that post. After rebooting, syndaemon (which apparently runs in a default install as "syndaemon -i 1.0 -t -K -R") would do its work in disabling the touchpad while typing.

List your drivers with "xinput list". If you see two drivers, you know where to look to solve your issue.

---

### Post by Roasted on 2016-06-16
> **vanadium said:**
> Take a look here: [http://ubuntuforums.org/showthread.php?t=2316240](http://ubuntuforums.org/showthread.php?t=2316240). This is what saved me on a Dell XPS 13 9350. As in the linked thread, two touchpad drivers appeared to be active. syndaemon was loaded, but probably talking to the wrong driver. I disabled the SynPS/2 Synaptics TouchPad as outlined in that post. After rebooting, syndaemon (which apparently runs in a default install as "syndaemon -i 1.0 -t -K -R") would do its work in disabling the touchpad while typing.

List your drivers with "xinput list". If you see two drivers, you know where to look to solve your issue.

Hey there, vanadium. I did just that. At first I didn't think it was working, as I expected "disable touchpad while typing" to actually *disable* the touchpad while typing. What I'm seeing though is if I put gedit 50% left side, put cursor on right side hovering over desktop, and just begin to spam type while simultaneously doing a "tap to click" motion on the touchpad, it does not register my taps as clicks. If I give it 1, maybe 1.5 seconds after typing, tap to click works again. So it seems to me this may actually be working. It just threw me off with the touchpad still being moveable while typing. Was this your experience with your XPS?

Thanks for your assistance. I think this might be the ticket.

EDIT - For kicks (and I'm a wildly curious person), I commented out the input section that I added to the synaptics xorg file. After a restart, yup, touchpad was terrible all over again. While tapping and typing it would reroute the focus all over the place. Uncommented, saved, restarted lightdm, boom. That was the answer. :D

---

### Post by vanadium on 2016-06-17
Indeed, it is only tapping and scrolling that is being disabled (the -t option of syndaemon). In Ubuntu 16, syndaemon runs by default as "syndaemon -i 1.0 -t -K -R". If we could find where to change these options, we could indeed remove the -t option to have the touchpad fully disabled while typing (and tweak the other options). As a less elegant method, adding a different syndaemon command to /etc/rc.local might also work.

---

### Post by Roasted on 2016-06-17
> **vanadium said:**
> Indeed, it is only tapping and scrolling that is being disabled (the -t option of syndaemon). In Ubuntu 16, syndaemon runs by default as "syndaemon -i 1.0 -t -K -R". If we could find where to change these options, we could indeed remove the -t option to have the touchpad fully disabled while typing (and tweak the other options). As a less elegant method, adding a different syndaemon command to /etc/rc.local might also work.

Just building on this/babbling a bit in case it provides others with ideas, my first instinct would be to add it to startup applications, either by putting the command right in the command field or throwing that syndaemon 1 liner in a bash script and call the bash script from startup applications.

Thanks for your info! :D

---

### Post by vanadium on 2016-06-17
I researched it somewhat and apparently that command is loaded "by default" by gnome system tools. Apparently, the command is hard coded. In Gnome 3, the UI setting to disable it is gone. The way, therefore, would indeed be to issue the command again - I am not sure whether the running instance must previously be killed.

Since it is launched by gnome, you probably should add the command to startup applications, or to a script that runs when you log in (which one could that be?). A command for the startup applications could be
```

sleep 1 && killall syndaemon && sleep 0.5 && syndaemon <preferred options>

```
The sleep commands, providing some delay, may not be needed at all.

---

### Post by ozsliver on 2016-08-08
> **vanadium said:**
> Take a look here: [http://ubuntuforums.org/showthread.php?t=2316240](http://ubuntuforums.org/showthread.php?t=2316240). This is what saved me on a Dell XPS 13 9350. As in the linked thread, two touchpad drivers appeared to be active. syndaemon was loaded, but probably talking to the wrong driver. I disabled the SynPS/2 Synaptics TouchPad as outlined in that post. After rebooting, syndaemon (which apparently runs in a default install as "syndaemon -i 1.0 -t -K -R") would do its work in disabling the touchpad while typing.

List your drivers with "xinput list". If you see two drivers, you know where to look to solve your issue.

Dear Vanadium,

Thank you so much! I spent days trying to fix this issue on my Dell 5000 with Lubuntu. It turns out I had the two touchpads too. I even noticed it before but did not make the connection. Thanks heaps again!

---

