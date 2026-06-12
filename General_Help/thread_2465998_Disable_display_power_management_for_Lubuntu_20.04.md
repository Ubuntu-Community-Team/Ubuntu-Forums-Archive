---
title: "Disable display power management for Lubuntu 20.04 LTS / LXQt"
date: 2021-08-17
forum: General Help
---

### Post by Regexaurus on 2021-08-17
I'm trying to use Lubuntu 20.04 LTS / LXQt for a digital signage application. It seems Lubuntu disables display output after 5-10 minutes. The physical display shows "no signal detected" when this happens, but I can still ssh to the system. When the system boots, a user is automatically signed on and the signage software client launches. For this user/account, I've tried:


[LIST]
[*]Editing ~/.xscreensaver and changing timeout from 0:10:00 to 24:00:00
[*]Creating ~/.xinitrc and adding the lines:
[LIST]
[*]xset s off
[*]xset -dpms
[/LIST]
[/LIST]

I rebooted after making these changes. These changes made no difference. I'm guessing I may need to adjust a global setting, perhaps something in /etc/sddm.conf...?

I would appreciate your hints/suggestions!

---

### Post by GhX6GZMB on 2021-08-17
Try Preferences -> LXQt Settings -> Power Management, select Idle and uncheck the Enable box.

Leave the SDDM stuff alone, that's only for the login screen.

---

### Post by Regexaurus on 2021-08-18
Yeah, that was already unchecked...

---

### Post by guiverc on 2021-08-18
I've had no issues, but I've only used GUI tools to make changes so I don't know if you've missed anything with your direct edits

For screensaver look at [https://manual.lubuntu.me/lts/3/3.2/3.2.20/screensaver.html](https://manual.lubuntu.me/lts/3/3.2/3.2.20/screensaver.html)

For power settings look at [https://manual.lubuntu.me/lts/3/3.2/3.2.12/power_management.html](https://manual.lubuntu.me/lts/3/3.2/3.2.12/power_management.html)

I don't have experience (recent anyway) with your changes so cannot comment on what you're missing; but not having a screen blank is quick & easy to achieve via settings in the manual (it's QA-tested semi-regularly each cycle)

---

### Post by GhX6GZMB on 2021-08-18
> **Regexaurus said:**
> Yeah, that was already unchecked...

Good.
Next try is: Preferences -> LXQt Settings -> Session Settings; "Autostart", untick XScreensaver.

Cheers.

---

### Post by Regexaurus on 2021-09-07
> **guiverc said:**
> 
For screensaver look at [https://manual.lubuntu.me/lts/3/3.2/3.2.20/screensaver.html](https://manual.lubuntu.me/lts/3/3.2/3.2.20/screensaver.html)

For power settings look at [https://manual.lubuntu.me/lts/3/3.2/3.2.12/power_management.html](https://manual.lubuntu.me/lts/3/3.2/3.2.12/power_management.html)


Screensaver (xscreensaver) and power management are already disabled--I confirmed in gui.

> **ml9104 said:**
> Good.
Next try is: Preferences -> LXQt Settings -> Session Settings; "Autostart", untick XScreensaver.

Cheers.

Yes, this was already unchecked. See screenshots below of various settings. As shown, I've alternately tried disabling and enabling idleness watcher with the settings shown.

[IMG]https://i.imgur.com/kjJq3YO.jpg[/IMG] [IMG]https://i.imgur.com/pDqGXZb.jpg[/IMG] [IMG]https://i.imgur.com/fteZbnL.jpg[/IMG]
[IMG]https://i.imgur.com/lOnUt8Z.jpg[/IMG] [IMG]https://i.imgur.com/2CzKFsk.jpg[/IMG]

I also masked sleep, suspend, and hibernate systemd targets, and rebooted, as suggested various places:

$ sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target

And confirmed the change:

$ systemctl status sleep.target suspend.target hibernate.target hybrid-sleep.target

&#9679; sleep.target
     Loaded: masked (Reason: Unit sleep.target is masked.)
     Active: inactive (dead)


&#9679; suspend.target
     Loaded: masked (Reason: Unit suspend.target is masked.)
     Active: inactive (dead)


&#9679; hibernate.target
     Loaded: masked (Reason: Unit hibernate.target is masked.)
     Active: inactive (dead)


&#9679; hybrid-sleep.target
     Loaded: masked (Reason: Unit hybrid-sleep.target is masked.)
     Active: inactive (dead)


None of this has helped. The system still times out and sleeps after 5 minutes or so.

---

### Post by guiverc on 2021-09-07
I'm still not sure the use of your [customXsessio]("https://wiki.ubuntu.com/CustomXSession")n script will help in anyway way, as you're not using a default/custom X session, but one created by Lubuntu I believe (ie. I suspect the creation of the ~/.xinitrc will do nothing); you also didn't mention specifying the shell to be used as per instructions, but I'm not sure that makes a difference as *dash* will be default.

I wonder if you've installed various packages that may have pulled in other systems that have maybe taken over and replaced the LXQt ones (*I left Power Management enabled so the settings I'd created that disabled it were read; the flipping of idleness watcher should do nothing if it's disabled as you've indicated*)

I've tried a number of boxes (*focal or 20.04 & impish** 21.10)* using only the GUI tools to disable power/screensaver & each time the effect is I don't see a blank screen or screensaver kick in (*in 12 mins it was watched for anyway*).

Given you appear to have made manual edits to config files, I'd check each of those files for errors (*some programs/utilities can treat an error as the end-of-file-marker & not read further, eg. sudoers file, meaning later valid lines are ignored & defaults are used*)

---

### Post by Regexaurus on 2021-09-08
> **guiverc said:**
> I'm still not sure the use of your [customXsessio]("https://wiki.ubuntu.com/CustomXSession")n script will help in anyway way, as you're not using a default/custom X session, but one created by Lubuntu I believe (ie. I suspect the creation of the ~/.xinitrc will do nothing); you also didn't mention specifying the shell to be used as per instructions, but I'm not sure that makes a difference as *dash* will be default.

Well, it was something of a stab in the dark, which isn't great. The .xinitrc I created literally contained only the two lines I previously indicated. It contained no shebang line. So it was probably syntactically incorrect in addition to not being used by Lubuntu/LXQt. I've moved .xinitrc aside (renamed) to ensure it is inactive/unused, and rebooted for good measure. Not that it makes a difference, but bash is the default shell. It's possible I changed this, but I don't recall doing so, and I don't remember being prompted to select a default shell during install.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289147&stc=1[/IMG]

> **guiverc said:**
> 
I wonder if you've installed various packages that may have pulled in other systems that have maybe taken over and replaced the LXQt ones (*I left Power Management enabled so the settings I'd created that disabled it were read; the flipping of idleness watcher should do nothing if it's disabled as you've indicated*)

I've installed very little beyond default packages. The Rise Vision media player is installed since that is the purpose of the system.

> **guiverc said:**
> 
Given you appear to have made manual edits to config files, I'd check each of those files for errors (*some programs/utilities can treat an error as the end-of-file-marker & not read further, eg. sudoers file, meaning later valid lines are ignored & defaults are used*)

I doubt this is the problem. I moved .xinitrc aside as stated above. I did the same for .xscreensaver, then used a gui utility to configure (disable) the screensaver/xscreensaver. This automatically created another .xscreensaver.

I also enabled power management and rebooted. Again, none of this made a difference. The system still times out / sleeps after about 5 minutes.

---

### Post by Regexaurus on 2021-09-08
[COLOR=#222222][FONT=Verdana]For kicks, I tried a one-time boot with [/FONT][/COLOR]*acpi=off*[COLOR=#222222][FONT=Verdana]. That didn't work so well.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289149&stc=1[/IMG]

I also tried a one-time boot with *apm=off*. As expected, this made no difference. The system still times out and sleeps/suspends the display. As stated in the original post, I can still ssh to the system when this happens, but doing so doesn't wake the screen. Normally, there are no input devices connected to the system. If I connect a physical USB keyboard and tap a key, it wakes the display.
[/FONT][/COLOR]

---

### Post by GhX6GZMB on 2021-09-08
Looking at your screenshots in post #6 triggered my memory. I had this problem myself at one point (unwanted screen blanking, although the xscreensaver was turned off)
Try unticking the "Lock screen before suspending/hibernating".
It's totally unintuitive, but IIRC it works.

---

### Post by Regexaurus on 2021-09-08
> **ml9104 said:**
> 
Try unticking the "Lock screen before suspending/hibernating".
It's totally unintuitive, but IIRC it works.

Done. Unticked that and rebooted (a message said some changes wouldn't take effect until after next login). I was hoping that would do it, but it didn't work for me. Thanks for the suggestion!

---

### Post by guiverc on 2021-09-08
> **Regexaurus said:**
> Not that it makes a difference, but bash is the default shell. 

Dash was made the default shell for Ubuntu back in 6.10 (see [https://wiki.ubuntu.com/DashAsBinSh](https://wiki.ubuntu.com/DashAsBinSh)) 

Bash is the default for interactive sessions yes, so if you open a terminal as a user expecting to see `bash` is correct, but the file you mentioned was not interactive but run by the system itself; thus default is `dash`; as Ubuntu is a Debian based system, follows Debian generally; and `dash` is far faster than `bash.


I know nothing about the "Rise Vision media player", so don't know what toolkits, libraries it uses, thus how it will interact with the system and how that could influence things (*if it was me, I'd look at how it was installed, and what dependencies were pulled into the system during it's install**; even though that was some time ago you'll find the details in apt logs*).  I find the `sudo apt install package` & resulting messages of what *dependency* rules packages are required very informative (ie. I scan them & can consider the effects before I hit "Y" or "N" to begin install)

---

### Post by Regexaurus on 2021-09-10
This worked for me. Create/edit/save (use sudo vim/nano, etc.) /etc/X11/xorg.conf.d/50-screensaver.conf (you can use a different filename) with the contents:

```
Section "ServerFlags"
        Option "BlankTime" "0"
EndSection
```

For testing, at a terminal, I first ran/executed:

xset s off

This sets the screensaver timeout to 0 (disabled) and worked for me, but the change didn't survive reboot. You can use *xset q* to view/compare settings before/after such changes. Creating a file as explained above, is global (independent of logged-in user) and persistent (survives reboot). See the xorg.conf man page for more info. I'm not sure, but I think you might do something similar per-user (not global), with a ~/.xsession file.

Thanks all for your suggestions!

---

### Post by aug7744 on 2021-09-11
That issue happen here also.
I use Lubuntu hirsute 21.04 configurated screensaver 5 min and display 10 min.
Using normally for more than 10 minutes with an program not disable display and with another program the display is powered off.
Strange detail ... I use a program that loading several files not disable display, but has one file that if is opened will disable the display.
The xscreensaver software used to screensaver and display not work correctly thus because Lubuntu not change to another software ? waiting wayland support to be added in Lubuntu ?

---

