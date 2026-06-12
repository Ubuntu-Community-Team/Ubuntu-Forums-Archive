---
title: "CD Mounting/ CD Drive Problem."
date: 2013-03-30
forum: General Help
---

### Post by radicalg on 2013-03-30
Hi there,

First off, I am a relatively new user of Ubuntu- so pardon me if I am sounding like a bit of an idiot. I've been using Ubuntu for approximately ~8 months or so on my desktop PC, no problems whatsoever. I decided about two weeks ago that it was time to upgrade from 12.04 to 12.10 and do a clean install, and it seemingly went well.

Two nights ago, I decided I needed to install a copy of Windows 7 on the side...but when I hit F12 as I usually did to boot from CD, all that came up was this:

[http://i.imgur.com/VjjkM2w.jpg](http://i.imgur.com/VjjkM2w.jpg)

Now, my general guess was that it'd be something to do with hardware...but given that I've never had this problem before, and that the tower is relatively new...it didn't make a whole lot of sense to me. I did a bit of browsing on the Dell forums, to no avail...this error pops up when the hard drive fails as well (sans the CD part), so all I could come up with is stuff for the hard drive. Given that, I figured I'd test if the DVD drive was working other than just opening/closing while using Ubuntu. No luck. It did not want to mount. I'm not sure if this is something related to the installation, since I never used the DVD drive in the two weeks this copy has been installed. I looked on the forums here for any solutions...nothing that I could find. DVD/CD/etc will not mount- no matter the disk. I'm not particularly savvy with all this, so any help at all is appreciated. I'm fine with replacing the DVD drive, but I want to be confident it's that before I go out and replace it.

(By the way...yes the drive was working before I reinstalled two weeks ago...that's how I installed it.)

Thanks so much in advance,
Phil.

---

### Post by dabl on 2013-03-30
This problem has nothing whatever to do with Ubuntu -- it's all about the BIOS and the optical drive (and possibly the Win 7 DVD).  A classical troubleshooting problem.

- Verify that the optical drive works (in _some_ OS) -- check cables, try other bootable CDs, play a music CD with Ubuntu, etc.

- Verify that all BIOS settings that are involved are set correctly (boot sequence, bootable devices, SATA channels, etc.)

- Verify the Win 7 DVD boots on some other computer (doesn't absolutely eliminate the possibility of a reading problem on your particular optical drive, however)

---

### Post by sudodus on 2013-03-30
Welcome to the Ubuntu Forums :-)

When you try to boot from the CD/DVD drive, Ubuntu is not involved at all, and Ubuntu won't write anything to the bios. Have you changed any setting in your bios menus?

Have you checked the connection (cable etc)?
Check with more than one CD/DVD disk!

It is probably a hardware error.

---

### Post by radicalg on 2013-03-30
> **dabl said:**
> This problem has nothing whatever to do with Ubuntu -- it's all about the BIOS and the optical drive (and possibly the Win 7 DVD).  A classical troubleshooting problem.

- Verify that the optical drive works (in _some_ OS) -- check cables, try other bootable CDs, play a music CD with Ubuntu, etc.

- Verify that all BIOS settings that are involved are set correctly (boot sequence, bootable devices, SATA channels, etc.)

- Verify the Win 7 DVD boots on some other computer (doesn't absolutely eliminate the possibility of a reading problem on your particular optical drive, however)


1) I'll give the cables a check. Like I said, I cannot mount/play CDs/DVDs in Ubuntu...nothing happens.
2) Right...nothing strange going on with the BIOS settings...I don't see anything odd going on there. Didn't change anything, ever.
3) It does. I also gave a go with a fresh copy of Ubuntu and Mint. Nothing.

> **sudodus said:**
> Welcome to the Ubuntu Forums :-)

When you try to boot from the CD/DVD drive, Ubuntu is not involved at all, and Ubuntu won't write anything to the bios. Have you changed any setting in your bios menus?

Have you checked the connection (cable etc)?
Check with more than one CD/DVD disk!

It is probably a hardware error.

I have not changed any settings whatsoever. Didn't think it would write to the BIOS, wanted to check though. I will check the connection...only thing I can think of, at this point. I have an old disk drive in an older tower of mine, so I'll have to try hooking that up later if this one has indeed "died".

---

### Post by sudodus on 2013-03-30
I have had to replace a couple of CD/DVD drives. Good luck with the old drive :-)

---

### Post by dabl on 2013-03-30
It's looking bad for the optical drive, huh?  FYI I've had two successful computer builds using one of [**[color=green]these[/color]**](http://www.newegg.com/Product/Product.aspx?Item=N82E16827135204).  One was an older Intel mobo, the other is the Asus mobo in my signature.

---

