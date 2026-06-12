---
title: "Gutsy Upgrade: Problems with Fonts, Xgl, sound, Java &amp; printing - argh!!"
date: 2007-12-04
forum: General Help
---

### Post by doundounba on 2007-12-04
So I finally decided to upgrade my main box to Gutsy - and am now entering a world of pain, apparently.  This machine has been running Kubuntu since Breezy, and in general, I've been pleased as punch, and most upgrades have been smooth or smooth-ish.

But this time, after upgrading, I have had and am having the following issues:

[LIST]
[*]Firefox fonts were waaayyy too small.  After hunting on the forums, this was fixed by uttering:
```
$ gconftool --type float --set /desktop/gnome/font_rendering/dpi 96
``` which fixed the menus, and then setting  layout.css.dpi to 96 and messing with the preferences to get acceptable fonts in page renders.  Still no quite to my liking, but I can live with it.
[*]Xgl seemed to be turned on and was slowing down the whole system very painfully. (Even though my system's not that under spec'ed with a 7600GS, an Athlon X2 4200 and 2GB of RAM.)  For this one, I followed this advice from another thread:
> Create a file at "~/.config/xserver-xgl/disable" - in my case I put a simple line like "##comment", although I suspect the only important issue is that the file exists. After restarting X, xgl is no longer running, instead I have good old Xorg again.
[*]No sound: I was using a PCI SB live and I've had to go back to onboard sound since I can't get any sounds out of the external card anymore.  I've yet to test the mic input, which was the reason I moved to the secondary card in the first place...
[*]Java in Firefox is busted.  I've yet to find a fix for this one.  Annoyed as I need it for my university work.
[*]Printing's borked too.  Things get into the queue, but then the print queue just says "error".  I've seen stuff in threads and on Launchpad about apparmor causing printing problems ([here]("http://ubuntuforums.org/showthread.php?t=600302") and [here]("https://bugs.launchpad.net/ubuntu/+bug/133982")), but so far, none of the workarounds that have worked for other people have worked for me.  I'm pringing via USB to a Samsung ML-2020.  Printing is also something I can't live without.
[/LIST]

All of this was working fine before the Gutsy upgrade.  I'm a little nonplussed.

EDIT: ARGH: This should probably go under "Installation and Upgrades"... Sorry.  I don't suppose one can move posts between forums...

---

