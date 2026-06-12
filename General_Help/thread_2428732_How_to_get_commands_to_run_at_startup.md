---
title: "How to get commands to run at startup"
date: 2019-10-08
forum: General Help
---

### Post by goemonburo on 2019-10-08
I have needed to disable 2 finger scrolling and tap-to-click and managed to do this with some "xinput set-prop" commands.  This works, but currently I have to use the up arrow in a terminal each time I boot and go back through .bash_history until I get those commands and redo them.  Each time.  Is there a good way to make this happen automatically when I boot?

Also, can I turn off Bluetooth at boot?  I almost never use it and am sure that it being on drains some battery on my laptop.  I tried looking for a Bluetooth manager in Preferences or System, but didn't find anything that seemed to fit the bill.

I am using Lubuntu 18.04LTS on a Dell Inspiron 3184.  Any help would be welcome.

---

### Post by Dennis N on 2019-10-08
Commands to run at login can be in a bash script. I put such a script into ~/bin. To get a script to run at login:

Go to: **Preferences > Default Applications for LXSession > Autostart Tab** 
Put the full path to script filename in the box next to 'Add', then click 'Add'.
And be sure script is executable or it won't launch.

---

### Post by TheFu on 2019-10-08
> **goemonburo said:**
> I have needed to disable 2 finger scrolling and tap-to-click and managed to do this with some "xinput set-prop" commands.  This works, but currently I have to use the up arrow in a terminal each time I boot and go back through .bash_history until I get those commands and redo them.  Each time.  Is there a good way to make this happen automatically when I boot?

There is a ~/.config/openbox/autostart file that will be run immediately after login if openbox is running as the Window Manager.  That is the default for LXDE.  That is where you should place any commands you want run at login.  If the file doesn't exist, create it and make it have executable permissions for your userid.

Linux is multi-user.  GUI related commands cannot be run "at boot", they can only be run at login.  I have mouse settings in that autostart file. Works well and only for GUI logins.  Most of the time, I don't login with a GUI, choosing to remote into systems using ssh, so having GUI programs run at inappropriate times is a bad thing.

> **goemonburo said:**
> Also, can I turn off Bluetooth at boot?  I almost never use it and am sure that it being on drains some battery on my laptop.  I tried looking for a Bluetooth manager in Preferences or System, but didn't find anything that seemed to fit the bill.

You can disable bluetooth a few different ways.
* in the BIOS (must be re-enabled in the BIOS)
* with "systemctl mask" - must be reenabled using "*unmask*", then *enable* and *start*
* rfkill - Hard or Soft Block the specific device. The name/number to block is dependent on rfkill list   On my laptop, the bluetooth is "3", but sometimes it is 2.  I softblock mine after being hacked through bluetooth on a fresh Ubuntu install with all patches applied the day before the hack. I haven't noticed any power impact, but generally only use my laptop about 5 hrs at a time on battery and I think it would easily get to 8 hrs for my typical uses. It is an 8th generation Core i5.

---

### Post by goemonburo on 2019-11-21
Alas, for the touchpad script, I did not have an "autostart" dir in my ~/.config/openbox folder and creating one and adding the script didn't work.  However, storing it in /bin and adding it to the "Default Applications" did.  So I'm very grateful for that suggestion.  Thank you!  

(Still haven't messed with the Bluetooth thing.  Seems so silly to have it automatically on all the time though, wasting battery and sending signals needlessly...)

---

### Post by TheFu on 2019-11-21
The ~/.config/openbox/autostart file must have eXecute permissions.
```
chmod +x ~/.config/openbox/autostart
```

My contents:
```
$ more  ~/.config/openbox/autostart
/usr/bin/setxkbmap -option caps:super &

/usr/bin/synclient  TapButton1=1 &
/usr/bin/synclient  TapButton2=3 &
/usr/bin/synclient  TapButton3=2 &
/usr/bin/synclient  AreaRightEdge=850 &
/usr/bin/synclient  AreaLeftEdge=50 &
 
# No bluetooth kernel modules!
sudo /sbin/rmmod btusb  btrtl btintel btbcm  bluetooth

# want a screen saver that locks the screen?
/usr/bin/xscreensaver -no-splash  &

```
Notice that I don't trust the PATH.

---

### Post by Dennis N on 2019-11-21
Lubuntu 18.04 --I have applications to autostart on login in the text file: **~/.config/lxsession/Lubuntu/autostart**
Note: the directions given in post #2 append items to that file.

---

### Post by TheFu on 2019-11-21
My last lubuntu install was on 16.04, so 18.04 may have (probably?) changed the config from where it has been since 2010.  Progress ... or just trying to avoid confusion as LXDE and LXQt work was concurrent.

---

