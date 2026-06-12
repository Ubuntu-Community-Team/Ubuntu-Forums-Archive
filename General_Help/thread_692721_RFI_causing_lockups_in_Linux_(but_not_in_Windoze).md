---
title: "RFI causing lockups in Linux (but not in Windoze)?"
date: 2008-02-10
forum: General Help
---

### Post by bthoward on 2008-02-10
I'm sure this is a new one...  Anyway whenever I light up my Ham Radio transmitter (especially on 20 meters) with only 100 Watts it locks up my Mythbuntu box.  The other two computers in the room keep running no sweat and this box had no problems a few months previous when running Windoze.  

When it crashes I get no mouse response and no way to do anthing but to poke the hardware reset switch on the front panel.  Anyone have any tips on what I could do in order to get a better clue as to what is causing this?  

I've installed ferrites around every cable coming to and going from the computer except for the USB lines.  I'll bring some more home here at some point in time and install some on those lines as well here soon...

Any tips or ideas are greatly appreciated!

---

### Post by Rhubarb on 2008-02-10
On a lot of computers the 5.25" and 3.5" disk drive bays don't have any RF shielding.
There's a chance that some RFI is getting inside the case.

Boot up your Mythbuntu box, disconnect all the USB devices, then turn on your ham radio.
See if that messes with it.

... And just to point it out, OS makes no difference to RFI susceptibility.

---

### Post by bthoward on 2008-02-10
I'm an electrical engineer who is often redesigning products to ensure that they pass EMC standards.  Not only do they have to pass but we have to pass the class B standards which are 10dB lower than most other commercial products.  

I realize that the OS has nothing to do with RFI getting into the box BUT it is however true that the linux OS on the box takes a dive when the RF enters the box and Windows takes it in stride.  Which tells me it has to do with a driver going bonkers and not handling it properly and just going out to lunch and taking the system with it.  

I was just hoping that there would be a way to find out what subsystem it is that I need to work on protecting better or possibly if there was a different driver that I could try such as maybe its something so simple as a mouse and keyboard driver that take a dive on me...  I've yet to try SSHing into the box when its locked up to see if its just the input methods that have died...  

Maybe I'll go for that sometime...  I just got done working quite a few stations but I did all that with only 7 watts of power...  The little rig never causes anybody any problems!  But this computer gets unhappy with only 100 Watts...

BTW all front bay covers are in place still and chassis grounded.

---

### Post by Rhubarb on 2008-02-10
Another way to check if it's a linux driver issue, is to put a live CD into a windows box to see if it makes any difference.

As you pointed out, sshing into the mythbuntu box would be another test.

Perhaps your mythbuntu box is in a node, and your windows boxes are in anti-nodes or similar?  - Which depends on your transmitter setup etc.

Maybe you could put your mythbuntu box in a Faraday cage (even though it the case should act as a Faraday cage anyway).

Let us know how you get along anyhow.

---

### Post by tom3393 on 2008-02-10
I have the same problems.... only i wasn't dealing with just 100 watts, but 500.but  here is what I have found/did to resolve the problem.

Move all audio cables as far from the RF lines as possible. You should ensure
that all audio cables are shielded. Now, I found that USB devices (mouse and keyboard)
were more susceptible to RF than ps2 devices, so i installed the adaptors to convert
to PS2, I know, it doesn't make sense ! but i can't deny the results. 

I also have a Radio works Line isolator between the K2 and the Amp. Since its almost
impossible to get a ground rod down here on top of the mountain, I use an MFJ artificial ground
to help with the RF problem. All equipment is grounded to a common point then connnected
to the MFJ which tunes the ground

The ferites around the keyboard and mouse line will help... the more wraps you can make the
better the results. With RF there can be multiple causes, and it take time to locate all the
problems. I have at time  threatened to junk the whole thing, it can be that frustrating.

The rig here consist of the Elecraft K2/100 driving a Ameritron AL-811 running about 400-500
watts on RTTY and sometimes on CW. 

Good Luck and patience my friend !

---

### Post by bthoward on 2008-02-10
The box is a dual boot...  Booting into windows no problem.... Booting into linux problem....  Same computer, same cable setup, same location, same transmitter.

---

### Post by bthoward on 2008-02-10
Yea its a bit frustrating.  I really need to spend the time and run a good ground system.  In the past for a simple 100 watt station its never really required much more than using the ground lead from the house (a terrible ground I knwo but its only 100 watts).  

K2/100 is a nice lil radio!  When I'm getting ticked about having to restart the shack computer  (which also runs the TV for the house) I switch over to my K1 and run a whole whopping 7 watts.

Here in the next several months my K3 should be showing up!  Gotta admit I'm excited and I'd like to have this sorted by then!!!  Unfortunately with working full time in engineering and finishing off my mba in the next 6 months I've been busy!  Actually right now I'm procrastinating writing a paper by writing this post and would much rather be out finishing my 2 meter quad right now!

Anyway all in due time.  

At the moment I'm not 100% sure if I'm running USB or PS perhiperials but that will be somthing I'll check.  I usually try to stick to PS2 as they just flat out work more often.  You know those weird times when you're debugging something and rip all the USB drivers out of the loop and poof your keyboard stops working...  hihi...

Anyway appreciate the positve remarks that you found your issue and was able to fix it!!!  

Oh and as far as audio the only audio I have is a cable that runs out of the sound card and into the radio for RTTY work.  I already suspected this as a possible RFI source so I first disconnected it.  The problem was still there.  I've still since transformer isolated the audio going both directions because its both good practice and a small margin of improvement probably.  

There is another audio run but that is a USB to CAT5 extender that then runs into the living room to a USB hub plugged into the USB hub is a USB to Toslink sound card and an IR receiver to get the audio and remote control commands for Myth to do its job.  I should probably split the TV off and get a separate ham shack computer but for now this box seems to run all these things perfectly seamlessly.  The TV runs on a "second monitor" and I can use it as a workstation without interferring wtih TV operation at all!  MUCH more than I can say for Windows MCE!  But like I said my separate mail server and separate firewall box both running Mandriva have no issues what-so-ever.  (No I don't think that its a Mandriva vs. Ubuntu thing).

Anyway again thanks for the hope!!    .....And the ideas!

---

