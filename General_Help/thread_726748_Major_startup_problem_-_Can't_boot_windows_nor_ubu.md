---
title: "Major startup problem - Can't boot windows nor ubuntu! Help!"
date: 2008-03-17
forum: General Help
---

### Post by freakout on 2008-03-17
I installed wubi/ubuntu (7.04) tonight on my laptop (*Toshiba L25-S119*) and everything went through fine. Ubuntu loaded up after installing/restart as normal. The first thing I did was set up my wifi connection, was easy and went through fine as well. However, after the the connection was made, a popup window asked me to create a default keyring. And that's where it all started.

Everything was pretty much frozen, no button or keys would work. The mouse would move fine, but I couldn't click, type, or move anything. I noticed it was accessing my hard drive, so I let it load for a while thinking it was just a temporary stall or something. A few minutes have passed and it's still stuck, same spot, with no progress. Still frozen.

Like I said, I couldn't click or type anything, so I had literally nothing else I could do. I tried popping the power button (which would usually do a normal shut-down) but nothing happened. Waited a bit, still nothing. The only thing I could do was a force shut-down of my laptop. So I did, and I rebooted the system. And here is where I'm stuck.

After the normal Toshiba boot screen passes, text flashes for maybe a half a second on the top of the screen, I've tried to read it a few times and it seems to read 'Invalid BOOT.INI, Booting from C:/windows' (or something like that) and it proceeds instantly to window's improper shut-down screen telling me something screwed up in the shut down and asks if I want to boot regularly or in safe mode, etc.

No choice to boot into ubuntu or windows, it just pops right into that improper shut down screen. I've chosen every option on that screen, and the result is always the same: it brings up the window's loading screen for about 2 seconds, then instantly restarts on it's own barely flashing a blue screen with some text (so fast that it's not readable at all) but it doesn't resemble the text layout of the BSOD, from what I can tell.

I can't do anything, I can't log into windows because it will just restart immediately on loading, and I can't even get to the dual boot option screen to even choose ubuntu because the window's improper shut down screen bumps in first. I can still get into the BIOS and such but no changes I've made seem to do anything, it always has the same outcome.

I'd really appreciate any kind of help, I'm stuck here with a useless laptop now. :(

Thank you.

---

### Post by ago on 2008-03-17
Boot with a windows CD or a rescue CD and in the recovery console run chkdsk /r

---

### Post by freakout on 2008-03-17
> **ago said:**
> Boot with a windows CD or a rescue CD and in the recovery console run chkdsk /r

The laptop came with restore disks (I remember using them once before) but I've moved 2 times to different houses and I've been hunting around the whole house for them and can't find anything. Is there any other possible solution? I'll continue the hunt but I've looked just about everywhere with no luck...

---

### Post by ago on 2008-03-17
There are rescue CD ISO available on the net, look for for "rescue cd iso" or "rc.iso" or "recovery console iso". You will have to burn said ISO onto CD. Or ask a friend to lend you a windows CD.

---

