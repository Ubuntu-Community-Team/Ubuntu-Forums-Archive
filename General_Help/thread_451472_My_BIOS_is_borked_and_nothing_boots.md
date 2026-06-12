---
title: "My BIOS is borked and nothing boots"
date: 2007-05-22
forum: General Help
---

### Post by FuturePilot on 2007-05-22
Well after Feisty randomly froze on me, I had no choice but to do a hard reboot. Well after I turned the computer back on it won't boot anything. Some of the images on the BIOS screen and in Grub are corrupted and there's random weird looking characters and random capitalized letters. So it's pretty messed up.

The problem is I can't find a DOS flash utility for my MB. It's an Asus P5LP-LE MB with a Phoenix Award BIOS. I checked Asus's website for a download, but apparently my MB doesn't exist as it's not mentioned anywhere. So right now I kind of stuck with a bricked computer:cry:

If anyone can help me it would be greatly appriciated.

---

### Post by Shazaam on 2007-05-22
You can try unplugging the pc completely (even remove the powercord), touch the pc frame, and use the reset jumpers on the mb to reset the bios (switch jumper pins, count to 5 seconds, then switch back). Or remove the mb battery, wait 10 seconds and replace the battery. This WILL reset the bios back to defaults so you will have to go in and setup the bios again. Try this before attempting a reflash.
Is this an HP pc? This is all I could find (not usefull if you cant boot into your pc).

[http://h10025.www1.hp.com/ewfrf/wc/genericSoftwareDownloadIndex?cc=us&dlc=en&lc=en&softwareitem=pv-34940-4&jumpid=reg_R1002_USEN](http://h10025.www1.hp.com/ewfrf/wc/genericSoftwareDownloadIndex?cc=us&dlc=en&lc=en&softwareitem=pv-34940-4&jumpid=reg_R1002_USEN)

Carefull you CAN brick a pc with the wrong bios.

---

### Post by southernman on 2007-05-22
It sounds as if your having a video issue... card going bad or monitor on the fritz.

None the less, I did a quick google and found this forum posting [here]("http://forums.driverguide.com/showthread.php?t=21296&highlight=ASUS+P5LP-LE"), the last poster (pcrepairguy) might have something that'll work for your situation too.

HTH's in some way...

[edited]

[HP forums link]("http://forums1.itrc.hp.com/service/forums/bizsupport/questionanswer.do?threadId=1110942&admit=-682735245+1179854668398+28353475")

[Google search that gave the above link]("http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=f1C&q=Asus+P5LP-LE+MB+flash+utility&btnG=Search")

---

### Post by FuturePilot on 2007-05-22
Yes this is an HP. The problem is those updates are useless since I can't boot anything.

---

### Post by southernman on 2007-05-22
You can't get her up with a dos disk?

The link given to hp forums seems to have a link to [this page]("http://www.esupport.com/techsupport/award/awardutils.htm"). I didn't post all the links from that forum, thinking you might read through the thread.

DOS her till your blue in da face. ;P No pun intended with the "blue" part! ;)

---

### Post by FuturePilot on 2007-05-22
Thanks for that link. What are the steps to get it going from a DOS disk? It looks like you need the BIOS flash files, which I don't have.

---

### Post by southernman on 2007-05-22
The last link I gave you is for the flash utiltiy... according to the previous thread link I gave ya - be sure to use the "latest bflash"

Now... go to this link (that enfamous thread I keep mentioning) and read through it. Little over half way down, you'll find a post from Scott Coghill (Mar 24, 2007 16:47:08 GMT   10 pts) he has attached the .bin file. Download it!

Read through the rest of the post and see how to proceed.

[edited] enfamous link I didn't post: [http://forums1.itrc.hp.com/service/forums/bizsupport/questionanswer.do?threadId=1110942&admit=-682735245+1179854668398+28353475]("http://forums1.itrc.hp.com/service/forums/bizsupport/questionanswer.do?threadId=1110942&admit=-682735245+1179854668398+28353475")

---

### Post by Minus0 on 2007-05-22
> **FuturePilot said:**
> Well after Feisty randomly froze on me, I had no choice but to do a hard reboot. Well after I turned the computer back on it won't boot anything. Some of the images on the BIOS screen and in Grub are corrupted and there's random weird looking characters and random capitalized letters. So it's pretty messed up.

The problem is I can't find a DOS flash utility for my MB. It's an Asus P5LP-LE MB with a Phoenix Award BIOS. I checked Asus's website for a download, but apparently my MB doesn't exist as it's not mentioned anywhere. So right now I kind of stuck with a bricked computer:cry:

If anyone can help me it would be greatly appriciated.

I recently ran into something similar, although with a different motherboard.  Try these steps and after each one try to boot up and see if there is progress:

1)Reset the CMOS 
 [http://h10025.www1.hp.com/ewfrf/wc/genericDocument?lc=en&cc=us&docname=c00379422#N822](http://h10025.www1.hp.com/ewfrf/wc/genericDocument?lc=en&cc=us&docname=c00379422#N822)
 a) If this doesn't work, try to remove the battery for a few minutes as well and see if it improves.
2) Remove all unnecessary PCI cards.  You seem to have on board video and sound.  If you have an extra video card and sound card added in, remove them.  Same with network cards and anything else you may have.  
3) Remove all hard  drives and CD-ROM's.
4) Remove as much RAM as possible.  The goal is to get as bare bones as possible to eliminate something else from possibly being the cause.
5) Download a new bios: [http://members.driverguide.com/driver/detail.php?driverid=939384](http://members.driverguide.com/driver/detail.php?driverid=939384)
6) Your going to have to find this on your own, as I don't know the name or if its possible.  But on my bios (Award), when it went corrupt it looked for the flashing util (in this case it was awflash.exe).  I burnt that and the bios a cd, popped it in, and eventually it took.  I had to mess with it a bunch (I flashed it about 20 times at one point :( )... but I'm working just fine.  Hopefully one of these steps will resolve it for you, apologizes in advance if you already attempted these.

---

### Post by Minus0 on 2007-05-22
On a side note, please please make sure you download the right bios.  I did a quick search, you may want to spend a little more time on it.

---

### Post by FuturePilot on 2007-05-22
> **southernman said:**
> The last link I gave you is for the flash utiltiy... according to the previous thread link I gave ya - be sure to use the "latest bflash"

Now... go to this link (that enfamous thread I keep mentioning) and read through it. Little over half way down, you'll find a post from Scott Coghill (Mar 24, 2007 16:47:08 GMT   10 pts) he has attached the .bin file. Download it!

Read through the rest of the post and see how to proceed.

[edited] enfamous link I didn't post: [http://forums1.itrc.hp.com/service/forums/bizsupport/questionanswer.do?threadId=1110942&admit=-682735245+1179854668398+28353475]("http://forums1.itrc.hp.com/service/forums/bizsupport/questionanswer.do?threadId=1110942&admit=-682735245+1179854668398+28353475")
Thank you very much. I think I might be getting somewhere. I made a floppy but I don't have a floppy drive on the computer. I do have a USB floppy drive but I can't get it to recognize that.

---

### Post by southernman on 2007-05-22
> Thank you very much.Your welcome futurepilot... Glad to have been some sort of help.
> I do have a USB floppy drive but I can't get it to recognize that.I am sure you have tried this, but feel compelled to suggest it anyway. When you power up this busted box, just keep hitting the delete key... that's *usually* the way into the bios during it's normal post.

If your able to get in there, see if you can set your boot up sequence to either usb or removable media as the first option.

I've never tried it and don't recall reading about anyone doing so but, I wonder if it would be possible to put the dos files and your new rom file onto a cd... and boot it up that way. *shrugs*

Hang in there... you'll get this done. Only then no one will be able to be in the same room your in as your head will be huge and chest poking out!  ;)

I feel your pain. My dad's box has gone bezerk too. It just keeps restarting... over and over. I've swapped out everything except the processor (don't have a compatible one), and the same thing. Getting ready to see if I can get into dos on it, flash the bios... hoping that'll solve it. *sighs*

Anyhow... good luck getting yours going.

---

### Post by FuturePilot on 2007-05-22
Ok I'm sooo close to fixing this. I found a regular floppy drive from another computer and I'm using that. When I start the BIOS flash utility it loads the BIOS.wph file. But that's as far as it gets because then it tells me there is no platform signature. After doing some searching it seems that I need another file: platform.bin But I can't find it. It's specific to the MB.

---

### Post by southernman on 2007-05-22
What you need is a file called 287233.BIN - I can't link you to it as it's an attachment on that forum link I gave you. That bin file is the bios version 3.17

You'll have to go back in this thread and find the link again... when I asked you to read the entire thread. The describe what they did, nearly step by step.

---

### Post by FuturePilot on 2007-05-22
Yeah I already got that. You need to rename it to BIOS.wph. It loads that file but then says there's no platform signature.

---

