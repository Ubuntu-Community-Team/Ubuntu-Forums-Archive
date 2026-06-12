---
title: "Firefox webcam problem"
date: 2024-05-16
forum: General Help
---

### Post by msknight on 2024-05-16
Lunar Lobster Cinnamon 5.6.7 Kernel 6.2.0-39-generic

Issue - Firefox and Chromium, when starting a Facebook video call via the browser messenger, it can't see the web cam. It can, however, see the video input from my AverMedia.

Troubleshooting started with Cheese, which can use the camera with no problem. I concluded that the webcam itself is working and is functioning fine.

I noticed an error...
2024-05-16T19:21:13.134957+01:00 mich-desktop kernel: [183096.081516] audit: type=1400 audit(1715883673.130:706): apparmor="DENIED" operation="unlink" class="file" profile="snap.firefox.firefox" name="/dev/char/195:254" pid=5096 comm="Renderer" requested_mask="d" denied_mask="d" fsuid=1101 ouid=0

I concluded Apparmor getting in the way of Firefox using the webcam, so attempted to put firefox into complain mode to see if that would solve the issue and prove whether the issue was with apparmor or not...
sudo aa-complain snap.firefox.firefox -d /var/lib/snapd/apparmor/profiles

...however, that failed with...
ERROR: Syntax Error: Unknown line found in file /var/lib/snapd/apparmor/profiles/snap.chromium.chromium line 2836:
    userns,

So after a bit of digging and not much luck, I removed chromium and attempted again, but got the same error for snap.skype.skype this time.

I checked my versions and snapd is on 2.62, so updated to the latest/candidate 2.63 but that didn't solve it either. Also, snap refresh said that everything is up to date.

A look on this forum for "userns," didn't turn up much of use, so I'm asking here for help please.

My aim is still to put firefox into complain mode to see if that sorts the webcam issue... because there seems to be something else wrong with snap profiles that also need sorting out anyway.

---

### Post by &amp;KyT$0P# on 2024-05-16
Lunar Lobster has been EOL [since 25 January]("https://wiki.ubuntu.com/Releases#End_of_Life") and has not received any security updates since then.  Can you use a supported Ubuntu release?

Can you try a [non-snap Firefox]("https://support.mozilla.org/en-US/kb/install-firefox-linux#w_install-firefox-deb-package-for-debian-based-distributions") to see if your webcam works there?

---

### Post by msknight on 2024-05-16
Oh. I tend to use apt dist-upgrade. I'd better drag myself into the modern world! Thanks for the heads up. I'll get that upgraded.

---

### Post by msknight on 2024-05-16
OS upgraded and I can put firefox into complain mode, so I can move on with the webcam issue. I'm going to mark this as solved for that reason. Thanks for the heads up.

---

