---
title: "Looking for some general info on how Launchpad/Gnome Bug Tracker works (Gimp crash)"
date: 2016-05-08
forum: General Help
---

### Post by rrrrube on 2016-05-08
I did a fresh install of Xubuntu 16.04 when it came out, then installed Gimp. I started having problems with Gimp crashing and eventually worked out the steps to the point I could crash Gimp every time. I've little experience with bug reporting, but I submitted a bug as best as I could on Launchpad. You can see the bug report here:

[https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/1576424](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/1576424)

Currently, it shows 'Fix Released' under The Gimp package and is assigned to Gnome Bugs. It also shows as New and Undecided under gimp (ubuntu). When I check the linked gnome bug, it goes back to 2011 but shows a status of 'RESOLVED FIXED'.

I'm a little confused as to who is responsible for what here. Can someone offer some insights on what (if anything) might be happening with this bug? Is there a fix available, that presumably I'll get at some point soon via the normal updates? Or is the 'gimp (ubuntu)' package the one I need to keep an eye on? I think the status there implies that no-one's looking at it (yet). I'm not sure of the procedure or protocols between the different packages and bug trackers.

I'd appreciate any info anyone has on what may be happening. And if you've got any suggestions on how to avoid this problem, that would be even better! The crashes aren't solely limited to the steps outlined in the bug report. It'll crash at other times too when using the text tool, but these were a bit more random and I couldn't always work out a pattern. It's very frustrating and I'm a little nervous to use Gimp now in case I lose work. I actually nuked Xubuntu and installed vanilla Ubuntu 16.04, in case it was a Xubuntu problem, but it happens under Ubuntu with Unity too.

---

### Post by buzzingrobot on 2016-05-08
This at git.gnome.org "might" be the fix, dated 27 March: [https://git.gnome.org/browse/gtk+/commit/?h=gtk-2-24&id=2811221d7039bd82265ce36a1b0dd9a0eeb431ad](https://git.gnome.org/browse/gtk+/commit/?h=gtk-2-24&id=2811221d7039bd82265ce36a1b0dd9a0eeb431ad)

It's a patch to gtk+ 2.24. The last note in the changelog for the version in Xenial is date 7 March.  That's  a key library, so I'd hope a patched update comes along very soon.

---

### Post by rrrrube on 2016-05-08
Thanks for the reply. I'll hope there's a fix soon. :)

---

