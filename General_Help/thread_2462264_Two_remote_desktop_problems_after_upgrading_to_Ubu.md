---
title: "Two remote desktop problems after upgrading to Ubuntu 21.04"
date: 2021-05-17
forum: General Help
---

### Post by KneadToKnow on 2021-05-17
My upgrade generally went smoothly, but I've had three problems with remote desktop, one of which I resolved myself.

Problem zero, which I fixed myself, was that desktop sharing had been disabled during the upgrade process. Re-enabling it was no big deal, but it was odd that there was no notice or anything that it would be disabled.

Problem one is that when accessing my 21.04 machine remotely. If the machine is awake (that is to say, the screen has not been blanked), I get a black screen with an X mouse cursor on my remote device. If the machine has blanked its screen, I get a message that "the connection closed unexpectedly." My remote device is my phone running the RealVNC Viewer for Android, ver. 3.7.1.4443. From the looking around I've done, I'm guessing this has something to do with Wayland? I'd love to know if there's a fix.

Problem two is on the other side of the coin: when I access multiple devices on my network using Remmina on my 21.04 machine, I used to be able to drag and drop the tabs for the individual connections to their own windows so I could adjust their size to fit different original resolutions. I can no longer do that. I click and drag the tab off to an empty spot on the desktop, and it just slides right back to where it came from. Any thoughts on what might be the issue there?

Thanks for any recommendations.

---

### Post by TheFu on 2021-05-17
Don't use Wayland.
Use x2go, not VNC.
Anything complex that is not "core" can stop working after any upgrade. That should be expected. Reading the release notes for the release BEFORE do-release-upgrade is smart too.
[https://discourse.ubuntu.com/t/hirsute-hippo-release-notes/19221](https://discourse.ubuntu.com/t/hirsute-hippo-release-notes/19221) has the release notes. I skimmed them and didn't see anything, but your eyes will probably see things mine did not. There are many known issues spelled out.

---

### Post by KneadToKnow on 2021-12-21
> **KneadToKnow said:**
> Problem two is on the other side of the coin: when I access multiple devices on my network using Remmina on my 21.04 machine, I used to be able to drag and drop the tabs for the individual connections to their own windows so I could adjust their size to fit different original resolutions. I can no longer do that. I click and drag the tab off to an empty spot on the desktop, and it just slides right back to where it came from. Any thoughts on what might be the issue there?

I accidentally discovered the solution to my own problem and wanted to document it. To view connections in separate windows in Remmina 1.4.20 (git n/a), go to Preferences > Appearance > Tabs grouping and choose "None."

---

### Post by TheFu on 2021-12-21
21.04 has less than 1 month of support remaining. Time to move to 21.10 ASAP.  Waiting until after support is removed makes it much harder to upgrade in-place. 

Running non-LTS releases usually doesn't provide long enough support for typical users.  I'd go nuts being forced to use a new OS every 6 months.  Going from LTS to LTS is the best compromise for most users.  That would be 18.04 --> 20.04 --> 22.04 --> 24.04 ....   even years, April releases.  Every flavor of official Ubuntu gets 3 yrs of support. A few get 5 years and the "Server" and main Gnome desktop get 5 yrs and 5 ESM years, if you need it.

Could we have met at SELF in Charlotte?

---

### Post by KneadToKnow on 2021-12-23
Thanks for the feedback. This device is already running 21.10; the question was originally asked back in May when 21.04 was a recent upgrade. I run LTS on my backup server to keep it stable, but on this machine, I've decided to try keeping up with the current releases as long as the hardware will let me.

I've never been to SELF, sorry.

---

