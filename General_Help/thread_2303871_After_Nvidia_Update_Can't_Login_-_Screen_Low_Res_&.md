---
title: "After Nvidia Update Can't Login - Screen Low Res &gt; Crashes After Enterting Password"
date: 2015-11-22
forum: General Help
---

### Post by john487 on 2015-11-22
Hello, I have Ubuntu 15.10 running and I have an Nvidia GTX 970.  The other day (Saturday) I let the updater install an updated Nvidia driver. It installed fine and never asked me for a reboot. I shut down the system then today when I tried to login, my login screen is low res (640x400) vs my real resolution of 2560x1440. I enter in my password and the screen gets all glitchy/pixelated and will not login, it just kicks me back to the log on menu. It does not say my password is wrong, just nothing.

I have tried using the recovery mode to use an older graphics driver, but my mouse doesn't work on the menus and I can't figure out for the life of me what the keyboard shortcuts are, so I can't even use this option. It seems like sometimes my keyboard works on the menus and others it doesnt.

Anyone have any ideas? I'd rather not have to format and start from scratch.

---

### Post by mistcloud-misty on 2015-11-22
Try this: When you boot into recovery mode, you can hit the up and down keys on your arrow keys to scroll between options. Hit down key until you get to the "Drop to root shell prompt" option, hit enter. You man need to login using the username you choose at the login menu and the normal password. 

Once in, type "sudo apt-get remove --purge nvidia* 

Reboot. You should be able to login now, but will likely be in low graphics mode. Install the new driver through the proprietary drivers if it's there, then reboot again. 

Sometimes updates break Nvidia. Let me know if that helps.

---

### Post by john487 on 2015-11-22
First off, thank you for the help. As you can probably tell, I am a Linux novice.

So I have tried to do that, but it won't work. The recovery menu is in read only, I assume this is the default.

I enter in the command and get:

W: Not using locking (I think thats what this says) for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt
E: The package lists or status file couldnt be paused or opened

Then I tried to use the "login" command from the terminal, it asks me for my user name which is two words (is there some kind of syntax if its two words?) and then asks me for my password, it then says login incorrect and won't log me in. I KNOW my password is right, so maybe it is how I am entering the login name? For example it is, Bob Smith. 

Any thoughts? Thank you again.

*EDIT*: For what its worth I took the latest 15.10 update that same day as well. I kept my system totally up to date, so I took the Nvidia update and then the Ubuntu update that came out likely Friday or Saturday morning.

---

### Post by mistcloud-misty on 2015-11-22
I never had that issue in recovery mode so I did a little research. Try typing this while in recovery mode and see if it does anything:

```
mount -o rw,remount /
```

If there's an error you might want to wait for someone with a little more knowledge in this to check it out. If it works, you should successfully be able to enter the purge command for Nvidia.

You may also try to "Resume normal" from recovery mode which should launch your computer in low graphics mode. You may be able to login that way, or it may black screen when you hit enter and send you back to the login screen - if you can login from there, you can type that code into terminal and re-install the Nvidia driver right from low graphics mode. For me I was unable to login to recovery mode so I had to use root shell prompt, but mine was in write mode so I had no issues.

Hopefully your computer should be able to run smoothly without regressing to the older drivers.

---

### Post by john487 on 2015-11-22
I tried the mount command and I got "special device remount does not exist." So no go there. The resume normal just gives me the same issue.

What is weird, at the logon screen, I put my password in, I get a graphical glitch, then I see briefly the black screen with white text that is sometimes displayed during boot, another graphical glitch, then it boots me back to the login menu again...So maybe its not just nvidia drivers, maybe the update totally borked my install. Is there any way to remove an update?

This is so annoying, one update and my entire OS dies...UGH. Thank you again for the help.

---

### Post by mc4man on 2015-11-22
In the recovery mode 1st hit the fsck option, that will give you read/write. When that completes you can then go to the root shell prompt option, ect.
Or boot up to login screen, once there go,   ctrl+alt+F3
login in on the tty screen, then run 
```
sudo apt-get --purge nvidia*
```
Once that completes then go sudo reboot ect.

---

### Post by john487 on 2015-11-22
OK so what worked was fsck then purge. What was odd was that even using clt-alt-f3, it still said my login was bad. So I did the purge, rebooted, was able to login just fine, BUT the whole left side of the Unity menu is gone and the top bar that displays networking, date, reboot, etc...is gone. After doing the purge, the default driver was the X.org one, but I was able to get into the settings menu via right click on the desktop, everything was slow and sluggish so I tried installing the Nvidia drivers that were just labeled proprietary and it worked (I tried the proprietary + tested and got the same issue as before). I should also add that doing the keyboard shortcut for the terminal didn't work either.

I also got a message saying there was an internal error: 

executable path
/sbin/plymouthhd

package
plymouth 0.9.0-0Unbuntu

Problem Type
crash

So...what the heck is going on? Obviously my OS is totally borked. Is there a way I can get the left side of Unity back and the top bar? Also, does Ubuntuhave a repair feature or if I re-installed Ubuntu would it leave all my programs and settings?
'

---

### Post by mistcloud-misty on 2015-11-22
Try reinstalling the unity desktop with the following commands:

```
sudo apt-get update
sudo apt-get install --reinstall ubuntu-desktop

sudo apt-get install --reinstall unity
```

You should do so from root shell prompt as you did when purging Nvidia - let me know what happens.

---

### Post by buzzingrobot on 2015-11-22
"Plymouth" is the pretty screen displayed as Ubuntu boots.  It does not work with Nvidia's proprietary drivers.

You can try resetting Unity:

> sudo apt-get install dconf-tools
dconf reset -f /org/compiz/
setsid unity
unity -reset-icons

I've no idea why that update broke your system or even if the Nvidia was involved.  I do know that many Nvidia cards on the market bearing the same ID and number can have slight differences introduced by a vendor. Those may or may not affect the ability of a driver to work.

---

### Post by john487 on 2015-11-22
Mistcloud-misty, I tried that and it didnt work, but one thing it did do was speed up the desktop, it was laggy before then doing that made it...better.

Buzzingrobot, I installed dconf-tools, but when i enter the dconf reset -f /org/compiz/ command, I get "Cannot autolaunch D-Bus without X11 $DISPLAY"

Any ideas? I am using the Nvidia driver listed as (proprietary) not the one that says (proprietary + tested). Should I use the X.Org one, does that matter here?

I wont be responding until the morning, thank you all so much for the help.

---

### Post by john487 on 2015-11-23
Anyone have any ideas how I can get the dconf command to run?

---

### Post by buzzingrobot on 2015-11-23
> **john487 said:**
> Anyone have any ideas how I can get the dconf command to run?

Try running this :

```
[COLOR=#111111][FONT=Ubuntu] export DISPLAY=:0[/FONT][/COLOR]
```

immediately before the dconf command. Don't expect anything to happen.  It's an attempt to tell dconf how to find the display.

If you then get the other reset commands to work but problems persist after a reboot, you could consider using Additional Drivers to remove the Nvidia proprietary drivers and install the open source Nouveau driver.  That's the xorg driver you've seen listed.  The downside of Nouveau is that its 3D performance often does not compare with Nvidia's drivers and, for some newer cards, the driver may not work at all.  This is because the number of cards with Nvidia chips in them exceeds the resources of the Nouveau developer community to figure out each card and provide drivers. While commercial vendors can tweak their cards from the baseline Nvidia design *and* ensure drivers are available, only Nvidia releases closed-sourced proprietary Nvidia drivers for Linux.

I've found that it's better to wait and see if I need the performance of a proprietary Nvidia driver before I jump into installing one.  I don't use games or demanding video and find that Unity runs very nicely on Intel Haswell video here.  Intel provides and supports an excellent open source driver which is used by default of Intel video is active. The best part:  No potential upgrade breakage.

---

### Post by john487 on 2015-11-23
I tried everything, no luck. Decided just to nuke my install and re-install it. Thank you to everyone who helped.

---

