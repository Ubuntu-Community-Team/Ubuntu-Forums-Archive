---
title: "After installing new video card, weird light flashes and won't let me turn on the PC!"
date: 2006-08-17
forum: General Help
---

### Post by user1397 on 2006-08-17
okay so I had a radeon 9800 pro 128 mb card, which I installed a zalman VF700 Al-Cu fan/heatsink on. the 9800 pro ended up not working (it got scratched) so i bought a new card, a radeon x1600 pro 512 mb. i installed the VF700 Al-Cu fan on it (so yes i took it off of the 9800 card) before installing it in the computer. so, finally i installed the card (and is it me or does this card not have a power slot?) but i cannot turn on the computer! it won't let me! the little tiny light on the back of the computer, the one next to the power supply's fan thing, keeps on flashing, even though it's normal behavior is to be constant.

wtf??????!!!!!!!!

edit:  here are the system requirements from the ati website:[LIST]
[*]AGP 8X or 4X graphics slot available on the motherboard
[*]Connection         to the system power supply is required (Adapter Included)
[*] 350-Watt power supply or greater recommended (assumes fully loaded         system)
[*] 512MB of system memory
[*] Installation software requires CD-ROM         drive
[*] DVD playback requires DVD drive and decoder software             (not included)[/LIST]I have an AGP 8X/4X slot, and that's where i installed it. 

Connection to the power supply?  i don't see anyplace on the card that could possibly connect to the power supply!

ionly have a 250 W power supply, but the requirement says "recommended" not requirement.

i have a Gig of RAM, so no problem there.

i can just download drivers online (btw, i have my 9800 pro drivers installed on the machine, but its the same driver for my new card (ati catalyst software)

and yes i have a dvd-rom

and yea i posted this thread in three different places, not to be a pain in the butt, but because of my urgency.

---

### Post by jazzgossen on 2006-08-18
I don't know the answer, but you will probably get better answers if you contact your power supply manufacturer (since it seems to be a problem with the PSU), or post this question to a forum about the graphics card or your motherboard.

---

### Post by barfy on 2006-08-18
your problem is with the power supply. your system isn't getting enough power to boot. try removing the extra fan and see what happens but I think you'll still have the same issue, there is no power connection on the card because it draws power right from the AGP slot thereby pulling power from the other parts of the MB. I would suggest you invest in a larger power supply from your local used PC parts vendor.

---

### Post by Greycloak on 2006-08-18
This is directly from the ATI site:

> 
System Requirements

        * AGP 8X or 4X graphics slot available on the motherboard
        * Connection to the system power supply is required (Adapter Included)
        * 350-Watt power supply or greater recommended (assumes fully loaded system)
        * 512MB of system memory
        * Installation software requires CD-ROM drive
        * DVD playback requires DVD drive and decoder software (not included)



The X-series cards DO require additional power above and beyond what the AGP slot can provide.  It does mention an included adapter, which wwould explain why you didn't see a slot for a molex power connector on the card.

As far as the power supply...don't take the recommendation lightly.  a 250 watt power supply is inadequate for any system these days.  Look for at least a 350watt.

---

### Post by user1397 on 2006-08-18
> **Greycloak said:**
> This is directly from the ATI site:



The X-series cards DO require additional power above and beyond what the AGP slot can provide.  It does mention an included adapter, which wwould explain why you didn't see a slot for a molex power connector on the card.

As far as the power supply...don't take the recommendation lightly.  a 250 watt power supply is inadequate for any system these days.  Look for at least a 350watt.okay i plan to get a larger PSU, but i'm wondering about th power cable that goes from the card to another power cable.  i believe these are called "Y Power Splitters".  if i'm correct, i have a pic of my card's accessories from newegg.com, which is the place i bought my card.  i did not buy the retail version, i bought an open box item, so i didn't get any accessories, just the card.  i circled the exact item in the attachment i have of my card's accessories.

so, how can i get this "y power splitter"?

also, i have another attachment where one component on the card is circled.  i'm wondering if that component is the one to plug the y power splitter into?

---

### Post by user1397 on 2006-08-21
okay i have solved this issue, it was a PSU issue after all. i went to a used PC parts vendor, got me a 400W PSU, installed it, and everything works fine. I was able to connect my graphics card and my graphics card's fan to the power supply, so no worries. everything's running fine (though a bit noisy :p)

---

