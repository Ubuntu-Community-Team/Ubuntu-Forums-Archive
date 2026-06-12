---
title: "Chrome profile crashed...how to reset?"
date: 2015-01-03
forum: General Help
---

### Post by Mike_Walsh on 2015-01-03
Morning, everybody.

I did a USB flashdrive install of Lubuntu 14.04 about a month ago. I installed Google Chrome, alongside Firefox, as I tend to use it more. Up until last night, everything's been working fine.

Not TOO sure what happened! It may have been a particular site I visited, or it could be my Google Drive account; it's never been that smooth to operate from the day I set it up.

All of a sudden, the CPU went into 100% overdrive; flat-out. I shut the browser down. This didn't cure it. So; I went to shutdown, and do a re-boot. No response; nada. The only way to shutdown was by doing a 'hard' power-off.

I re-booted, and went back into Chrome. Fine for a few minutes; then.....same thing. CPU flat-out (I use the CPU monitor applet in the task bar.) Shut browser down, went to re-boot.....once again, no response. 'Hard' power-off again.

Curiouser and curiouser. Re-booted, and this time, went into Firefox. After 90 mins, everything's still A-OK. 'Hmm', I think. 'I wonder...'

Shut down Firefox, back into Chrome. After 5 mins, same problem; system locks up, won't respond to anything.

Re-booted, back into Firefox. Smooth as silk, all the way.

I've tried Chrome in some of my other distros, and it's absolutely fine. I'm guessing this means that Chrome's profile settings on the USB install have got corrupted somewhere along the line. Hence to my question:-

How do you reset the Chrome/Chromium profiles? (I'm guessing they both work the same. I have Chromium on some of my distros, Chrome on others. Two have got both...)

This isn't something I've ever needed to do before, so any help or advice from anyone who's come across this problem (and knows a 'fix') would be very much appreciated. I'm good at sorting out most things, but I wouldn't even know where to start on this one; I know disconnecting the account, and then re-syncing won't cure it...

Thoughts? Ideas?


Regards,

Mike.

---

### Post by ajgreeny on 2015-01-03
Next time it happens, assuming you can get to a terminal, see what the command **top** shows you; if you can't get to a terminal, see if you get any info by starting Chrome in terminal; it may give some helpful output when all goes to worms.

I am not sure exactly where the Chrome-browser configuration is on a system as I have never used it, but start by looking in the hidden **~/.config** folder in your home, and if you find a folder with the name **chrome-browser** in that just right click and rename it, then restart Chrome to see if that helps.  You will loose all your current setup of Chrome, but at least you should be able to use it again.

---

### Post by Dennis N on 2015-01-03
You can create a new profile (user) from Chrome's settings for testing.

**Menu > Settings > Users > Add New User**

More information:

[https://support.google.com/chrome/answer/2364824?hl=en](https://support.google.com/chrome/answer/2364824?hl=en)

---

### Post by Mike_Walsh on 2015-01-03
Thanks, guys.

@AJ; You and me, too, AJ. I'm not at ALL sure where you find the config file, but I know it's amongst the hidden ones. I'll have a look, anyroad.

@Dennis N: Thanks for that, Dennis. I hadn't realised you can have more than one user on a single, running instance of Chrome. That might be a way round it, too.....although I don't know whether you can sign a new user in with an existing user's credentials; I don't know how you go about that.

What I want to do, obviously, is to keep my bookmarks & extensions, but reset all the rest of it. Can that BE done, without having to start all over again? I know I won't lose my LastPass stuff, 'cos that's held in the cloud; not so sure about AdBlock Plus & Ghosty, though. Ghosty tends to be specific to the individual browser, 'cos even with syncing, I still have to build up Ghosty's database from scratch, for each browser.....which is a real PITA!

Regards,

Mike.

---

