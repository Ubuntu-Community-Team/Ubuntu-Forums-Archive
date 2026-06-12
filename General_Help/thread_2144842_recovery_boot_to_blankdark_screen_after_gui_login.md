---
title: "recovery boot to blank/dark screen after gui login"
date: 2013-05-13
forum: General Help
---

### Post by thaitang on 2013-05-13
I ran a way-overdue update on an older laptop I rarely use, which has xubu 12.04 installed. Update went fine and I booted/logged in fine for two sessions afterward. Now, however, the laptop boots in recovery mode and when I choose to resume normal startup I go to the login window, and after entering passw the screen simply goes black and then just dark, and the numlock is enabled.

I can tty (f1-6) fine. Tried another update/upgrade but nothing changed. For some reason after the bios details scroll by I am no longer presented with a grub menu from which to choose how to boot. I need to press the ESC key to get that to pop up. And sure enough the recovery option is selected by default. I can choose to boot regular (non-recovery), go to the regular login screen, but the same problem ensues.

I have googled, found a lot of propbs with ubuntu 12.04 lightdm/gdm, 2d/3d and wallpaper chooser issues. But having installed xubu I do not think those issues should be affecting me. The only "xubuntu" specific problem I could google was a discussion about hardy heron problems on this forum that went unresluved by the looks of it.

So any help would be appreciated.

Come to think of it, I had a problem with my desktop a while back. Although the details are kind of fuzzy, I lost my desktop that time also. Again a pure xubu 12.04 install. I was able to run livecd fine and so relented and re-installed fresh and got ny desktop back. Hwever, its a crapshoot everytime I login whether I get the usual gui login or get dumped to a tty, at which point I simply login and restart, hoping to get the gui login next time around. Sometimes it takes a few rounds to do so.  just assumed that perhaps my onboard (NVIDIA) graphic card might be on the way out on the used MB I bought for that pc. Ironically I bought a used MB to accomdate using nvidia chipset. Anyways, different problem, but eerily both issues are video related (or so it seems) with pure xubu 12.04 installs. But it must be an isolated prob on my end since nothing on google turns up.

anyway, any advice help I would sure appreciate it.

graphix card is an Intel. I

---

### Post by thaitang on 2013-05-18
Oh well, with nothing left to try I thought I might as well try a re-install, but I first went for bohdi, which although installs fine in vbox, stalls during harddrive installation. Next up was CrunchBang, and well I have nothing but good things to report. Not only did it install slicker-than-snot on the laptop with GUI desktop (yeah I mistakenly was thinking the vido chip might be toast), but after trying the same install on my PC, I have not had a single video hiccup, being dumped to shell and having to restart hopin xubu would initialize the gui desktop on the next go-round. I have probably re-booted/started the pc about 50 times since without a single hitch.

So for me, which appears to be some kind of isolated case since nobody seems to be reporting similar probs, CrunchBang (openbox really I guess) seems to have solved the issues I was experiencing.

---

