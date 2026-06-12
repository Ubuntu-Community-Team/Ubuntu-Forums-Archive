---
title: "Low Resolution (wrong aspect ratio) on Display Port"
date: 2019-02-01
forum: General Help
---

### Post by AR_Kozz on 2019-02-01
HP Compaq Pro 6305MT running an AMD a8-5500b APU with RadeonHD7560D.
Ubuntu 18.04 and Windows 10 on two separate sata HDD's selected via f9 options at boot.
display: VGA and DP. DP plugged into DVI port on a TV.

before problem: both ubuntu and windows ran in 1280x720 via the DP port

critical event?: unplugged cable from desktop to tv and plugged in hdmi-to-dvi cable from laptop for a while.

problem: 

desktop PC now blank during initial boot on DP; "no display detected" for BIOS screens and GRUB screen. Works fine via vga.
DP display detected as soon as Ubuntu starts booting. Not detected under Windows boot.
Ubuntu boots into 1024x768 mode.
Gnome Display Manager reports no higher resolution. Stuck in 4:3.

while this looks like a bios problem, which HP is useless at supporting, I doubt it's bad hardware since Ubuntu is still able to use the DP. The cable does not appear damaged, and if it were I'd expect worse than just low resolution. It's not the DVI port on the TV, as the laptop still works fine on it. So I'm looking for the nuts and bolts of whatever Ubuntu knows that the BIOS and Windows seem to have forgot. Where should I start?

add: kernel log shows "EDID is invalid" appears for DP-1 device concurrent with the problem. TV reported as "unknown device" by GDM as well. So whatever happened has effectively blocked the TV's EDID from my PC.

Until I solve that issue, how can I force the display back to 1280x720, e.g. with xorg radically different than it used to be?

add: okay, I fixed that with xrandr. Now to figure out how to splain things to idiot Windows 10 and the BIOS which don't even try. Cheers. Solved as far as ubuntu goes.

---

### Post by TheFu on 2019-02-02
Please mark the thread solved using the **thread tools button** near the top. This helps people avoid wasting time looking to help when already solved or for incomplete answers when something isn't solved.

---

