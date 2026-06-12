---
title: "VNC and power management problems"
date: 2006-11-15
forum: General Help
---

### Post by Ares139 on 2006-11-15
Hello,

Ever since upgrading Dapper to Edgy, I've had three main problems.  First, my VNC password isn't saved upon reboot.  If I set a password in Remote Desktop, it will work for that session.  Once I reboot (and log back into a session), the VNC password no longer works.

Second, my power management options do whatever they please.  I have set it not to blank my screen, but it does anyway, after 15 minutes.  This is with screensavers disabled too.  Also I've set it to dim my screen when unplugged, and it doesn't.  It won't even let me dim my screen while plugged in either.  It seems to be stuck on the settings I had it on before upgrading to Edgy.  The settings "stick" in the dialog (when I reopen it, they are what I set them to), they just aren't obeyed.

Third, hibernate and suspend don't work whatsoever.  Hibernate at least *used* to work under Dapper.  Never could get suspend to work.

EDIT 1: Something else I just realized.  For some reason, as I type, in any application, sometimes a random blob of text is inserted.  This has to be some sort of key combination I'm accidentally hitting like CTRL+V.  But the thing is, it isn't always something in the clipboard.  I've hit CTRL+V after one of these blobs of text get inserted, and the clipboard's contents is entirely different.  It's a little annoying, but not a big problem.  If anyone would happen to know what I'm doing to cause this to happen, I'd greatly appreciate someone helping me out lol

EDIT 2: Hm, well on another note I found out my swap was missing after upgrading to Dapper.  Searched around a bit and figured out how to get it back.  Seems to be there, but when I do a "swapon -s" it tells me that it's there, but under "used" it says "0" - is that normal??  Several people said fixing this also fixed their hibernation problems too.  Not true for me.  The swap is there, but all I get when I hibernate is a few "device can't be accessed" errors or something like that, and then it powers down only to boot up normally instead of resuming.

EDIT 3: Well crap.  The swap stuck after a reboot, but when I tried to hibernate, my swap disappeared again.  *sigh*  Here's what I did:
1, determine your swap with 'fdisk -l'
2, do mkswap on your swap partition - RECORD THE UUID WHICH THIS COMMAND
OUTPUTS
3, now use this UUID to put into fstab and resume
files...(RESUME=UUID=<the-swap-partition-uuid-from-vol_ID
should go in /etc/initramfs-tools/conf.d/resume
4, update-initramfs -u
5, reboot normally after this finishes

Works fine until I try to hibernate, then it overwrites my swap and boots up without swap instead of resuming my session.

Please, someone help?  I'm feeling kind of lost here...  =(


Thanks!
-Ares

---

### Post by Ares139 on 2006-11-18
I really hate bumping threads, and I won't do it again, but I'm getting desperate here.  I also ran into a few more problems (missing swap, as detailed above in the EDIT lines).

Somebody??  Anybody??  This is driving me up a wall...  ](*,)

---

