---
title: "Stacer Not Working?"
date: 2021-08-24
forum: General Help
---

### Post by wyattwhiteeagle on 2021-08-24
In Stacer under Services, I chose to not allow Bluetooth to start at start up. When I check it after restarting, it is switched back to the "enabled" position.

Why is Stacer not saving my changes?

---

### Post by dragonfly41 on 2021-08-25
In the comments at the bottom of this page
[https://www.tecmint.com/stacer-linux-system-monitoring-tool/](https://www.tecmint.com/stacer-linux-system-monitoring-tool/)
a similar question is asked ... July 21st.

I suspect that you are trying out Stacer is a LiveUSB and so settings do not persist after a reboot.

Actually, this theory is [confirmed in this thread]("https://ubuntuforums.org/showthread.php?t=2466222").

Stacer is intended to work in an installed, persistent OS, not a LiveUSB.

You could create a *persistent* LiveUSB if that is all you have.

As a side issue would this site help you as a temporary measure?[  ]("http://www.rollapp.com")[Rollapp.com]("https://rolapp.com")

---

### Post by wyattwhiteeagle on 2021-08-25
> **dragonfly41 said:**
> In the comments at the bottom of this page
[https://www.tecmint.com/stacer-linux-system-monitoring-tool/](https://www.tecmint.com/stacer-linux-system-monitoring-tool/)
a similar question is asked ... July 21st.

I suspect that you are trying out Stacer is a LiveUSB and so settings do not persist after a reboot.

Actually, this theory is [confirmed in this thread]("https://ubuntuforums.org/showthread.php?t=2466222").

Stacer is intended to work in an installed, persistent OS, not a LiveUSB.

You could create a *persistent* LiveUSB if that is all you have.

As a side issue would this site help you as a temporary measure?[Rollapp.com]("https://rolapp.com")

The thread that "confirms" this...I started that thread while I was unknowing that it is possible to install to a flashdrive.

No, I'm not on the LiveUSB. I actually used an 8gb LiveUSB to install to a 128GB usb drive. 6.1gb of that is a swap area.
I didn't even use MKUSB, only 8gb live and the 128gb and the "Something Else" option in the installation process.

It isn't like being installed to an internal, but like an external. 
I'm having to use it as my main drive because my internal is dead.
it's working fine so far.

RollApp.com While most everybody swears up, down and all around that "the cloud"is awesome, I would never intentionally store my information in "the cloud", not even through an installed encrypting application.

Thank you.

---

### Post by dragonfly41 on 2021-08-25
I can't read your mind so please be specific in your next post. Saves time.

Again I can't guess what are your apps but cloud can be useful to test non sensitive apps.

My Stacer installations run fine.  Some more detective work needed.

---

### Post by wyattwhiteeagle on 2021-08-25
> **wyattwhiteeagle said:**
> The thread that "confirms" this...I started that thread while I was unknowing that it is possible to install to a flashdrive.

No, I'm not on the LiveUSB. I actually used an 8gb LiveUSB to install to a 128GB usb drive. 6.1gb of that is a swap area.
I didn't even use MKUSB, only 8gb live and the 128gb and the "Something Else" option in the installation process.

It isn't like being installed to an internal, but like an external.
I'm having to use it as my main drive because my internal is dead.
it's working fine so far.

> **wyattwhiteeagle said:**
> In Stacer under Services, I chose to not allow Bluetooth to start at start up. When I check it after restarting, it is switched back to the "enabled" position.

Why is Stacer not saving my changes?

> **dragonfly41 said:**
> I can't read your mind so please be specific in your next post. Saves time.

Again I can't guess what are your apps but cloud can be useful to test non sensitive apps.

My Stacer installations run fine. Some more detective work needed.

Please explain what you mean by non sensitive apps being different from my apps.

Besides Stacer, I use...

Synaptic to see broken packages...I dont use it for anything else.
Wine-staging. Within Wine I use IMVU, IMVU Cache Cleaner, and Lightshot. Nothing else is installed in Wine.
Google Chrome Web Browser (Linux) as my Default

I uninstalled Thunderbird.

In Settings before installing Stacer...

Screen Dimming is swtched to off.
Blank Screen...Never
Auto-Suspend...Off
Power Button...Nothing

In Privacy
...File History & Trash
......File History...Off
......Trash & Temp Files...1 Day

Everything else is how it was other than through Terminal "sudo apt update" and "sudo apt full-upgrade" and autoclean and autoremove.

The only more specific I can get is hardware lists, and an installed packages list.

---

### Post by wyattwhiteeagle on 2021-08-25
> **dragonfly41 said:**
> Please be specific in your next post. Saves time. Some more detective work needed.

I tried post all installed packages but I got this message...


> [COLOR=#000000][FONT=Ubuntubeta]Your submission could not be processed because a security token was missing.

If this occurred unexpectedly, please [inform the administrator]("https://ubuntuforums.org/sendmessage.php") and describe the action you performed before you received this error. If possible, please include the error page URL plus the date and time the error occured.

Tip : Please shorten long posts by using [https://paste.ubuntu.com/](https://paste.ubuntu.com/) for terminal and log output and link to it in your posts.
[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta]Ubuntu Forums[/FONT][/COLOR]


---

### Post by dragonfly41 on 2021-08-25
Stacer troubleshooting. You will get more accurate replies by contacting the developer.

Post an issue here:

[https://github.com/oguzhaninan/Stacer/issues](https://github.com/oguzhaninan/Stacer/issues)

However, these are the initial steps (detective work) I would follow to gather information about Stacer, rather than just reporting "it doesn't save settings".

Q. Does Stacer retain changes to other startup settings (other than Bluetooth)?
If Yes then there is some issue with Bluetooth.
If No then there is some issue with Stacer.

And regarding this

> Please explain what you mean by non sensitive apps being different from my apps.

I simply refer to apps such as games which I would regard as "non sensitive".

Certainly no personal information is safe in the cloud.

====================================

[P.S.] It might be easier to just follow the advice here.

[https://askubuntu.com/questions/67758/how-can-i-deactivate-bluetooth-on-system-startup](https://askubuntu.com/questions/67758/how-can-i-deactivate-bluetooth-on-system-startup)

Change setting manually in [COLOR=#242729][FONT=ui-monospace]/etc/bluetooth/main.conf

[/FONT][/COLOR]

---

