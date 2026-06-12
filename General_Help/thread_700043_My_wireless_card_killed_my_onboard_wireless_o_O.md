---
title: "My wireless card killed my onboard wireless o_O"
date: 2008-02-18
forum: General Help
---

### Post by Rippy on 2008-02-18
PCMCIA wireless card: Netgear WG511T
Onboard wireless card: Broadcom bcm4306
Laptop: Dell D400
Ubuntu: Gutsy, though it should be irrelevant

Ok, so a little while ago I got wireless working just great on my laptop. I had to use ndiswrapper to do it, but I was not pleased with this because I wanted to be able to do some network security testing, and you cannot set a card to monitor mode using ndiswrapper.

So I ordered the wireless card I mentioned. In the meantime, I got [BackTrack]("http://www.remote-exploit.org/backtrack.html") booting off of a USB drive. The card comes in the mail, and I start using it in BackTrack to avoid doing anything to my precious Ubuntu wireless setup. With great jubilation, I can get the card working in BackTrack, and I succeed in setting it to monitor mode and back. Pleased with my victory, I eject the card and start Ubuntu, hoping to do some web surfing.

LITTLE DO I KNOW, MY HOPES ARE ABOUT TO BE CRUSHED.

I start it up, and I can't access the net. ifconfig and iwconfig both display the onboard wireless as up and running, and ndiswrapper -l does indeed say that the bcmwl5 driver is installed. And yet, I can't get scan or connect to networks. Frustrated, I start up in Windows, a generally more wireless-reliable OS. Nothing.

So my question is this: Did my wireless PCMCIA card kill my onboard wireless? I'm terribly confused. What I'm really hoping is that there's some kind of toggle on the laptop, one of the "Fn" buttons, that automatically turned off the onboard wireless when it detected another card in the PCMCIA slot. Unfortunately, it's a used laptop and i haven't had it for long, so I'm not familiar with those buttons.

Is that a possibility? Or is it... MURDER?

Thanks! (Sorry, I think I made that more dramatic than it had to be :P)

-Rippy

---

### Post by Rippy on 2008-02-18
bump?

---

### Post by danwood76 on 2008-02-18
It might be that your BIOS automatically switched of the internal wireless when you inserted the other card.

Have a look in your bios menu for a wireless option.

Otherwise (I know this may sound stupid) make sure you have your wireless switch set to on, or button pressed to enable it.
Does windows recognise the internal wireless card as a network connection?

You could just switch completely over to your new card of course.

---

### Post by Rippy on 2008-02-18
Alright, I found the wireless section in my BIOS, but it's still enabled. As for the button, this laptop doesn't have a button for toggling wireless, though it can be done with Fn+F2 (The little radio tower icon). I made sure that thing was set correctly.

Windows still recognizes the card, and what's even more strange is that windows can detect APs with it. In Dell's wireless utility, I can go to the "Site Monitor" (I think) tab and, after a few seconds, some access points come up. I know it's not just remembering past access points because it also picked up a neighbour's AP I've never seen before. Sometimes when I try to then connect to my access point, it connects but I can't access the net. The rest of the time, it just doesn't connect at all.

I know that, if it comes down to it, I can just use the wireless card for everything, not just BackTrack. But it's kind of a pain, to have to constantly disconnect it to carry it around with me (it won't fit in the laptop bag unless it's disconnected).

But anyway, thanks for the help with this strange problem. It's not the first time this laptop's wireless has given me weird, unexplainable problems.

---

