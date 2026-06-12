---
title: "Can't log in after resuming from Gnome screensaver"
date: 2022-06-28
forum: General Help
---

### Post by mickee384 on 2022-06-28
When I start typing the password, generally the lock screen shows up showing I am typing the password. Sometimes after a few days the lock screen shows up, but it says "Swipe to Unlock" This is a desktop all in one computer. When this happens though the lock screen is actually frozen requiring a hard boot. Any help is appreciated. Please let me know if you require more info.. I am running 22.04 and have been since it came out. This issue started about 2 weeks ago.  Could it be an issue with the last kernel update? It started shortly after that.

---

### Post by mickee384 on 2022-06-28
I have temporarily deactivated the screen lock, but I prefer to have it lock.

---

### Post by #&amp;thj^% on 2022-06-28
This seems to be a problem mostly on wayland: [https://askubuntu.com/questions/1407564/ubuntu-22-04-wont-wake-after-screen-lock-screen-dim](https://askubuntu.com/questions/1407564/ubuntu-22-04-wont-wake-after-screen-lock-screen-dim)
You never say which session your on X or wayland

[https://askubuntu.com/questions/1414619/ubuntu-22-04-xscreensaver-not-working](https://askubuntu.com/questions/1414619/ubuntu-22-04-xscreensaver-not-working)
We need to start reporting bugs or nothing happens, and the problems remain.

---

### Post by mickee384 on 2022-06-30
I am running X. Also even though I disabled the lock screen the system still froze after about 3 days requiring a hard reset. I have since disabled the gnome screensaver (Blanking of the screen) but I don't want to get issues with having the screen on all the time. So it doesn't matter about the lock - the issue is with the Gnome Screensaver. Maybe I need to reinstall that. Anyone know how that can be accomplished? Other than this issue my Ubuntu 22.04 is running perfectly. I disabled a Gnome shell extension as I figured the issues started when I installed it, but that maybe a coincidence. The extension is the one where it tracks how long an application takes to open.

---

### Post by #&amp;thj^% on 2022-06-30
> **mickee384 said:**
>   Maybe I need to reinstall that. Anyone know how that can be accomplished? Other than this issue my Ubuntu 22.04 is running perfectly. I disabled a Gnome shell extension as I figured the issues started when I installed it, but that maybe a coincidence. The extension is the one where it tracks how long an application takes to open.
They are both in the same package.
> GNOME screen saver and locker
gnome-screensaver is a screen saver and locker that aims to have simple, sane and secure defaults, and be well integrated with the GNOME desktop. GNOME screen saver and locker
 
To reinstall use:
```
sudo apt install --reinstall gnome-screensaver
```
Good Luck, I don't think this is your problem though.

---

### Post by mickee384 on 2022-07-01
I have reinstalled Gnome screensaver. Will post the results in a few days

---

### Post by mickee384 on 2022-07-03
working perfectly so far after reinstalling Gnome-screensaver. However I also uninstalled the [Applications start up time measure]("https://extensions.gnome.org/extension/5087/startup-measure/"), so that may have been the issue. I will report back in a few days or if the issue resurfaces.

---

### Post by mickee384 on 2022-07-03
working perfectly so far after reinstalling Gnome-screensaver. However I also uninstalled the Gnome Shell extension [Applications start up time measure]("https://extensions.gnome.org/extension/5087/startup-measure/"), so that may have been the issue. It was the only thing I had installed when the symptoms of the freeze after unlocking my session. I will report back in a few days or if the issue resurfaces.

---

### Post by mickee384 on 2022-07-03
ok, something I forgot to mention just before this happens the lock screen message changes to "Swipe up to unlock". Then I can click and flick the window and enter my password. I will post again if I can't login again

---

### Post by mickee384 on 2022-07-04
so today I entered my password on the lock screen it launched the desktop then froze and logged me out. I logged back in ok. But the screen blanked and locked after just a few seconds of inactivity, had to do an actual logout to fix that. Any new ideas as to what is transpiring? I have disabled the lock but have kept the blank screen to see if its the lock or the screensaver mucking me up. If that doesn't display the issue, I will try using lock without the blank screen, if that's even an option.

---

### Post by mickee384 on 2022-07-04
ok so after the last issue, now the screen locks and blanks after like 10 seconds of inactivity. Should be after 15 minutes.

---

### Post by mickee384 on 2022-07-04
Disabled the lock, screensaver activates and same issue exiting the screensaver, after 3 days so... it appears to be the screensaver after all. If it makes any difference, I have a HP Envy 23 Touchsmart AIO computer. Any more thoughts? And otherwise the PC and Ubuntu are working great!

---

### Post by mickee384 on 2022-07-06
lately now the lock screen shows "swipe up to unlock" Its not a laptop or tablet its an HP all in one desktop PC

---

### Post by mickee384 on 2022-07-07
perhaps its actually a problem with gdm3? The weird part of all of this is I don't believe this is being caused by something I've done. It just started on its own a few weeks ago. Could it be kernel related?

---

### Post by #&amp;thj^% on 2022-07-07
Nope none of those, maybe you'll want to add yourself to the many bugs here: [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bugs?search=Search&field.status=New](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bugs?search=Search&field.status=New)

---

### Post by mickee384 on 2022-07-08
ok, so last night the system didn't even blank out. The computer was active and mouse moved but desktop frozen. I am beginning to think I need to reinstall from scratch. But I will try logging in as Waykand first as I have been logging in as X

---

### Post by mickee384 on 2022-07-09
logging in as wayland may work, but I depend on using X. The dock doesn't work in wayland -- and when I installed latte.. well it installed a whole bunch of KDE apps and files. That may come back to haunt me. Is there a way to fix the Xorg by reinstalling? What about reinstalling gdm3? Is it possible the errors are in the /home folder? Creating a new user doesn't have the same issues.

---

### Post by mickee384 on 2022-07-10
ok, so I created a new user and restored my data files. I did not copy /home to new user home as I think there are corrupted files and permissions in it due to restoring the home directory by using grsync and then using grsync to the old profile. So testing the new profile now. Just with whatever files were created by adding a new user plus restoring my documents and specific settings (.icons/.themes/.thunderbird. We shall see how this goes. Side fix, I was able to restore the use of the Dash to Dock as that wasn't working for the old user, working fine in new user. What do you think about these steps I've taken?

---

### Post by mickee384 on 2022-07-17
worked or so it seems almost for a week. However after installing the Glasa Gnome Shell extension (This extension puts an icon in the panel consisting of two comic-like eyes following the cursor.) the problem has reappeared. I have remove it and will report back. If it causes the issue to not return I will post a comment on the Gnome Shell website

---

### Post by mickee384 on 2022-07-23
Glasa not the issue. Only way to fix after trying to log back in is to CTRL+Alt+F3, log in and do a reboot. I decided this time to do a complete shutdown / restart. I will post results. I also eliminated and Gnome Shell extensions as being at fault.

---

### Post by mickee384 on 2022-07-26
It seems the complete shutdown, rather than a reboot is what fixed the issue.

---

### Post by mickee384 on 2022-07-28
I spoke too soon. Happened again after 3 days... I guess i should just reinstall a fresh Ubuntu, ya?

---

### Post by mickee384 on 2022-08-01
so I reinstalled Ubuntu with Option 1 - reinstall without losing personal files etc. I then setup all my options and reinstalled all my apps. It was again fine for 2 days. When I typed my password to unlock the computer, Just the backlight was lit - no desktop. Num lock still worked. Tried CTRL ALT F1 and I got the gdm3 login page, logged in and the desktop still would not show up. Ended up rebooting after that as nothing else has worked. Even log out wouldn't work, just restart (from the system menu on the login screen) Any ideas on what the issue could be? I am on holidays in a few weeks, at which time I will do a complete fresh install. I am very frustrated that this issue persists. Has no one ever had this issue? Is it possible my hardware is at fault? Are there any logs or file outputs required for anyone to help me with this problem? Also what if I switched to lightdm over gdm3? Or is the problem not with the greeter, but with Ubuntu? If I switch to lightdm, would that cause any issues with Gnome?

---

### Post by deadflowr on 2022-08-01
> Has no one ever had this issue?

I have not has this issue.
> If I switch to lightdm, would that cause any issues with Gnome?
Personally, I have not seen any issues running gnome with lightdm as the display manager.
But it might depend on GPU.
Do you know what GPU you have?
Edit: Maybe you mentioned the GPU, but it's buried somewhere.

---

### Post by mickee384 on 2022-08-01
GPU Intel HD Graphics 
 on CPU: Intel i5-3330S (4) @ 3.200GHz

---

