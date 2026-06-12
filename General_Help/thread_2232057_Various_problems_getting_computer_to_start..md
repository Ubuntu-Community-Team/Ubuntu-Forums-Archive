---
title: "Various problems getting computer to start."
date: 2014-06-29
forum: General Help
---

### Post by Jerfo on 2014-06-29
Hello there! Well, I hope I can make a sense for this because I am not too sure I'll be able to explain myself correcctly...

The problem began a couple of weeks earlier, I turned on my computer and ran my Ubuntu partition (with Trusty Tahr, up to date as far as I remember; the other partition is a Linux Mint 15, has been rather neglected for quite a while now) but it just hanged in that gray-purplish screen, since my computer is nothing new and fancy I'm used to it not being lightning fast but after a while it was quite clear that it was not just being unusually slow, so I restarted, or at least pretended to. After that, everytime I tried to start it the computer would turn of or maybe half a second and then boom, dead again, I could hear how the various noises it does were just beginning to start up and then stop, it kept doing that. It was rather late so decided to leave it at that until I had time; so, the next few days I began reading about it but not having time to actually fiddle with it just let it be. Today I finally had some time and tried the easiest and most elemental solutions of all: Make sure all the cables were correctly plugged. I tried to run it and MIRACLE! it worked... or so I thought, I just let it auto-start with Ubuntu, I saw it get up to the grub screen but I was distracted and when I turned again it had turned off. After that I tried to turn it on again, it got past the BIOS screen but never made it to the GRUB screen and nothing happened... I thought maybe Ubuntu was being funny so I thought of using the Mint partition, so I tried again, this time, after a while it got to a screen with a blinking cursor and nothing else. So I decided to use a live-USB (with 13.10) and it did took a while (somewhat longer than expected, though on there it might have been just my anxiety) and it did start, so basically my computer is now on a live session but I have no idea what to do or where the problem might be.

---

### Post by grahammechanical on 2014-06-29
So, the computer runs off of a live session but not off of the hard disk? I am thinking - faulty hard disk. To test:

Disconnect the hard disk and start the computer. Do not have the live session USB plugged in. You should get message that says "operating system not found. Insert system disk." Or something like that. That will prove that the computer hardware is fine up to that point. It eliminates CPU and RAM. Maybe.

Now try again with the live session USB plugged in. Does that work fine?

Now try with the hard disk plugged in. Are you getting those problems? If so, think about getting a new hard disk.

Regards.

---

### Post by Jerfo on 2014-06-29
Hello, thank you for your help, I did what you suggested and when I tried to boot again from the hdd  I got into grub, tried to run both Ubuntu and Mint. For Ubuntu after I chose it it changed to a blinking cursor and didn't go further; for Mint it went into the animation and seemed like it was loading, the logo changing gradualy, but nothing else happened... So I am assuming my hdd really is dying? Is there a chance this was something else which can be fixed? Some years ago I had another HDD and I remember I ran some program back then which showed it truly was faulty and needed to be replaced.

---

### Post by Jerfo on 2014-07-12
Ok, so the problem has changed: I tried turning on the computer, at first it did boot for ater a while (maybe a minute or so) I heard it all halt and it had turned off. After that it wouldn't boot, only the fans turn on, nothing else, I tried checking all the connections, unplugging all non-necessary stuff, removed battery... and it remains the same. Is it, then, a Motherboard malfunction or could it be de PSU or... well, what?

---

