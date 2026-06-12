---
title: "Has anyone got sound working on an A8V-MX with Edgy?"
date: 2007-01-28
forum: General Help
---

### Post by Patrick Dixon on 2007-01-28
Because if you have, please will you tell me how you did it!

The drivers all appear to be loaded and working, and I've tried just about all the settings on alsamixer, but absolutely nothing.

I've even compiled and loaded the latest alsa modules.

Motherboard bios appears to be 0503, which seems to be the latest available.

---

### Post by laidback on 2007-01-28
Have you looked in System>preferences>sound to see that you have the sound card active...bottom of splash screen there is a sound card selection box. On my machine I have 2 sound cards, onboard and PCI, using the selection box I can switch between the 2, really handy. 

Keep at it as you will solve this even though it's currently very annoying. I'm using 6.06 although I do have a disc with 6.10 on it and my sound worked there too.

---

### Post by Patrick Dixon on 2007-01-28
Thanks for the reply.  Are you using the same motherboard?  6.06 wouldn't find the Via Southbridge when I tried to install it, so I didn't even have a working network connection.  Maybe you have a different bios version, or have you changed some of the bios settings or booted with any kernel flags?

System>preferences>sound doesn't seem to have any soundcards in it - which may well be the problem.  Dunno how you solve it though.

This is meant to be a MythTV box, but no sound is a bit of a killer.  And there are only two pci slots, so adding an additional sound card is not really an option either.

---

### Post by Patrick Dixon on 2007-01-28
OK System>preferences>sound now has VIA8251 in it (nothing else).  I got this by deleting the ~/.asoundrc file that the alsa page tells you you need ;-(

However, still no sound.

HELP!  Judging by the number of unresolved sound problems on here, ubuntu seems to be a bit of a disaster where sound is concerned.

---

### Post by laidback on 2007-01-28
No I'm not using the same board, indeed mine is rather old. ECS K7S5A with an Athlon XP. One sound card is SIS and the other C media Electronics. They appear as SIS S17012 and C-Media PCI CM18738-MC6. But I doubt that's any help.

I do remember having sound problems with Mandriva which I think got solved by selecting the Alsa drivers from within the software. It was very much a matter of suck it and see. I have a feeling that you need a consitent choice throughout your system and software.

Can you get any sound from a test beep, or even at boot up?

---

### Post by Patrick Dixon on 2007-01-28
> **laidback said:**
> 
Can you get any sound from a test beep, or even at boot up?No, nothing - just the beeps from the on-board beeper.

---

### Post by laidback on 2007-01-28
I know this may sound daft but under these circumstances I go back to basics to eliminate all the possibilities.

1  Do your speakers work from another source?
2  If using a sound card is it seated properly (take it out and put it back in)?
3  Am I using the correct output channel from the card?
4  If I have 2 cards remove 1 and get the other working first.
5  If all above OK use software to generate sound, sound recorder perhaps.

---

### Post by Patrick Dixon on 2007-01-28
No it doesn't sound daft - but I've tried those!

Sound is built-in to motherboard, speakers were taken from a working windows machine.

I've just tried the install CDRom again, and I get no sound from that either.  So I'm about to file a bug.

---

### Post by laidback on 2007-01-28
I just loaded up my Edgy to see the differences. In System>Preferences>Sound there's an additional tab, the front one labeled devices. You can get this to create sounds for checking purposes. There are 4 options to set, the first 3 are set to Autodetect on mine, sound capture is set to Alsa. Press the test buttons to test for sounds. I guess you get nothing? I get nothing from the 4th (Alsa) but I can play CDs etc (one's playing right now).

Within the next tab, Sounds, the first item allows you to check for sounds as well, select a sound and it'll play it, e.g the Login Sound (quite nice actually), nothing here as well?

Perhaps a hardware issue.

Sorry I cannot be of any more help.

Don't give up though, you'll get there, I did and I'm stupid.

Laidback

---

### Post by laidback on 2007-01-28
A sudden thought, if you have a spare sound card put it in and try with that.

---

### Post by Patrick Dixon on 2007-01-28
Thanks for the encouragement, but you're right - I get nothing from any of those!!!

Ah well, I guess it will be OK with silent movies.

---

### Post by laidback on 2007-01-28
Patrick

My BIOS has an enable/disable switch for onboard sound....worth checking yours!!!

Could it be that simple?

---

### Post by Patrick Dixon on 2007-01-29
Yes mine too - but it's enabled.

---

### Post by laidback on 2007-01-29
Aghhhhhhhhhhhh!

Running out of ideas...sorry

---

### Post by laidback on 2007-01-29
Patrick,

Can I suggest that you buy/borrow a PCI sound card. Disable the onboard one within the BIOS, install the new one and try again. If it works at least you'll have sound and the implication is that there is a hardware problem with the onboard one.

---

### Post by Patrick Dixon on 2007-01-29
> **laidback said:**
> 
Running out of ideas...sorryYes me too.

I have a sound card on the way.  The problem is that even if it works it will only prove that there is either a driver or hardware problem with the on-board sound.  And given the lack of responses from anyone who has got sound on this motherboard working, I'm assuming it's a bug with the driver.

---

### Post by laidback on 2007-01-30
I have obtained a copy of The Official Ubuntu Book. Now there is a section entitled...Ubuntu has not detected my old sound card...page 216. Now I'm not suggesting that you have an old sound card but the story goes that it could be a kernel problem. In other words the kernel you are using doesn't have the correct driver for your card..hence problem.

Can you try..at a terminal

$ alsamixer

If you have the correct/driver installation alsa will let you set your sound paramters (it's a coloured screen that pops up) . If it doesn't appear or you get an error message then I think you can conclude that there is a hardware/driver issue. It would appear that that can be resolved but it's going to be a search for the right kernel module for your system.

I do have an interest in the mobo that you are using as any future system that I might build is expect to be on an Asus board. I've been looking at the M2N series. Although I have to admit that I find it very difficult to understand the differences between the various products, M2N8-VMX , M2N-MX, M2NPV-MX etc....another can of worms I expect.

---

### Post by Patrick Dixon on 2007-02-01
alsamixer runs.  The problem seem to be that it recognises the sound 'card' and loads the driver (via82xx) - but either the driver doesn't work with this motherboard/kernel, or the hardware is broken.

---

### Post by laidback on 2007-02-01
Patrick,

Kernel issue I think.

See my message in your forum email.

---

### Post by Patrick Dixon on 2007-02-02
Update
--------

I have got sound working with a pci card, but this is not a long term solution as it takes up 1 of the 2 slots I require for DVB-T cards!

On further investigation, I have discovered that the on-board sound (via82xx) is actually working but just very, very quietly.  I've turned up everything in alsamixer, but it's still only audible with ear to speaker - not problem with amp or speakers as these work fine with the pci soundcard.

Any ideas - anyone?

Please ....

---

### Post by laidback on 2007-02-03
Patrick,

Progress, I'm pleased.

Try Volume Applet, I have version 2.14.3 which must have come from synaptic I reckon.  It says it uses Gstreamer 0.10 if that helps.

I have had a situation as follows, set mute on in Kaffeine/gxine etc and you cannot hear anything from anywhere else no matter what you do. The answer is to go back to the apps and set mute off. Perhaps you could go through your sound apps to check that mute is off everywhere.

The Ubuntu help people say this shouldn't happen so I guess it's something to do with my system, I just avoid the issue now.

Worth checking.

---

### Post by Patrick Dixon on 2007-02-06
Finally traced this to a motherboard fault which is now fixed and I have sound at normal volumes!

Thanks laidback for your help.

---

### Post by laidback on 2007-02-07
Patrick,

I'm so pleased. Are you able to say what the actual fault was?, I may come across it too next time I build a new system.

Really please with your outcome.

Kindest regards

laidback
:)

---

### Post by Patrick Dixon on 2007-02-07
I'm not 100% sure what the fault was.  The case has no audio connectors on its front, so there was no jumper fitted to the motherboard.  I fitted a spare jumper with some flying leads that I had. and it all came alive.  Maybe there was a short between two of the header pins or something?  All very odd.

---

