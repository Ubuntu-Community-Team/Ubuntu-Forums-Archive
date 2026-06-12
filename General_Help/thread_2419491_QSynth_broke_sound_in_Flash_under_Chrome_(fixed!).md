---
title: "QSynth broke sound in Flash under Chrome (fixed!)"
date: 2019-05-22
forum: General Help
---

### Post by gleedadswell on 2019-05-22
Maybe this should go under the Multimedia forum?

I just had this problem, and after some sleuthing managed to fix it.  But I thought I'd post it in case anyone else has this problem.

I was simultaneously running Chrome, viewing videos on YouTube while also playing around with writing some music in Rosegarden, which pipes its sound through QSynth.  Someone who actually knows what they are talking about will probably point out that there is something technically wrong with my description of the relationship between Rosegarden and QSynth.  At some point I lost sound on YouTube (one minute it was working and the next minute it wasn't).  Sound was still working in Rosegarden.  In the Sound Settings, Chrome still showed up under the Applications tab and it wasn't muted.  It also showed up in pavucontrol.  Sound still worked in Chrome for non-Flash objects (I went and listened to Owl sounds on the Audubon Society website and they worked just fine).  Sound also worked in YouTube on Firefox and in all other applications that I tried such as Rhythmbox.  So it seemed to be very specific to Flash videos playing under Chrome.

None of the following fixed it:
Rebooting
Switching to another audio output device (headphones via usb)
Killing pulseaudio and removing all files in ~/.config/pulse (then rebooting)
Installing flashplugin-nonfree-extrasound (then rebooting)
Removing and reinstalling Chrome (then rebooting).

I logged in as a different user and found that YouTube videos worked just fine under the other user account.  So the problem was clearly something in the account .config files for Chrome.  So I logged back into my usual account and did

```
rm -r ~/.config/google-chrome
```

Restarting Chrome (and grumbling about having to tell it who I was and restart syncing...) now sound in YouTube worked.

So, someone who knows more about the files in ~/.config/google-chrome could have probably come up with a solution that wouldn't have clobbered my Chrome configuration.  Presumably there is a single file somewhere in that directory that has Flash sound configuration, probably under the PepperFlash directory.  But this worked.

But my overall advice is that if you have QSynth running you probably shouldn't simultaneously run anything that uses sound without going through QSynth.  I've found in the past that QSynth doesn't seem to play nice with other programs.

---

