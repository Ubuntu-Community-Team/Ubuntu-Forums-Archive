---
title: "USB Mass storage device plugin for rhythmbox?"
date: 2006-12-26
forum: General Help
---

### Post by remusus on 2006-12-26
Does a plugin for rhythmbox exist to manage usb mass storage devices?  I can't find one out there.

---

### Post by remusus on 2006-12-26
bump... why do my questions always get very few views, and no responses?  I'd be happy with a "no plugins exist at this time" response :rolleyes:

---

### Post by theaverageidiot on 2006-12-26
Actually, I was looking for something like this too. Help? :) Even a different program besides Rythmbox. I tried a few others like Banshee that seemed it had features that would meet my needs but they never worked or were all bugridden. Maybe it's just me :/.

---

### Post by remusus on 2006-12-27
@theaverageidiot: I know amarok can handle mass-storage mp3 players, but that isn't an option on the setups that I am dealing with.

---

### Post by doclivingston on 2006-12-28
Rhythmbox 0.9.6 and later have "generic" audio player support, which will let you play tracks from devices that HAL reports as being audio players. If your player doesn't show up, adding an empty file named ".is_audio_player" into the top level of the device will act as a work-around.

Current versions don't have the ability to transfer tracks to, or sync automatically with, generic players - but it being actively worked on, at [http://bugzilla.gnome.org/show_bug.cgi?id=76528](http://bugzilla.gnome.org/show_bug.cgi?id=76528).

---

### Post by theaverageidiot on 2007-01-05
> **doclivingston said:**
> Rhythmbox 0.9.6 and later have "generic" audio player support, which will let you play tracks from devices that HAL reports as being audio players. If your player doesn't show up, adding an empty file named ".is_audio_player" into the top level of the device will act as a work-around.

Current versions don't have the ability to transfer tracks to, or sync automatically with, generic players - but it being actively worked on, at [http://bugzilla.gnome.org/show_bug.cgi?id=76528](http://bugzilla.gnome.org/show_bug.cgi?id=76528).
I've done the whole .is_audio_player thing before and it showed up but it would fail to transfer songs 90% of the time or just hang forever :/.

---

