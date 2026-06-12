---
title: "Lots of suddenly appearing problems (Help!)"
date: 2008-01-16
forum: General Help
---

### Post by bakaeigo on 2008-01-16
I logged into my computer today and found tons of problems that hadn't existed yesterday. 
Here's a list:

1) Sound is no longer working except for the startup and logoff sounds. When I click on the volume control icon, it says "The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured"

2) "sudo" no longer works for anything. Instead, I must use "su" to become root in the terminal before using any administrative commands

3) Many of the options in the System>>Administration menu are now gone. It now only includes Firestarter, Keyring Manager, Network Tools, Partition Editor, Printing, Startup Manager, System Log, System Moniter, and Update Manager.

4) Even the programs that are listed in the Administration menu don't run. After entering my root password, this error message comes up: "The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator"

5) Whenever launching a directory with Gnome-Do, it opens in Konqueror (I also have KDE installed, though I use GNOME primarily). This is not the case when clicking anything in the "Places" menu.

These are just the things I have noticed so far. Is there a way to fix all of this, and if so, how? I really don't want to reinstall ubuntu.

---

### Post by freddyp on 2008-01-16
Can you su into the system and create a new user?  If so, how does the system respond to the new account?

---

### Post by bakaeigo on 2008-01-16
> **freddyp said:**
> Can you su into the system and create a new user?  If so, how does the system respond to the new account?

What would I type into the terminal to get the "Users & Groups" Dialogue?

---

### Post by freddyp on 2008-01-16
Check this link and see if it helps  --

[http://ubuntuforums.org/showthread.php?t=353276](http://ubuntuforums.org/showthread.php?t=353276)

---

### Post by freddyp on 2008-01-16
Ops forgot.  Here's one from Ubuntu documentation for Gutsy.  Of course if you're already root won't don't need sudo --

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_Add_standard_Users](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_Add_standard_Users)

---

### Post by bakaeigo on 2008-01-16
I created a new user, and the problems seem to be the same on the test account.

---

### Post by bakaeigo on 2008-01-17
Bump :(

---

### Post by bakaeigo on 2008-01-17
Bump again.

---

### Post by bakaeigo on 2008-01-17
Okay, I managed to get everything up and running, except for the sound. How do I fix the sound problem?

---

