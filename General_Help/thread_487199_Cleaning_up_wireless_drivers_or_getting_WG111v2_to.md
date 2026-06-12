---
title: "Cleaning up wireless drivers or getting WG111v2 to work"
date: 2007-06-28
forum: General Help
---

### Post by DeathOnJuice on 2007-06-28
Hey, everyone. I just installed  a NetGear WG111v2 (0846:6a00 in lsusb model, Realtek chipset), and although it has worked well for the most part (after configuring it Wireless Manager), the connection has been dropping several times per day. A sudo /etc/init.d/networking restart fixes it, but that takes a while and it drops again later in the day. Although this happens to everyone in my house, my problems seem to be the most frequent. I'm going to try to get ndiswrapper working before I return it (I've heard a few horror stories about that with this card, but some successes), so I have two questions.

1. Has anybody made this card work flawlessly on Feisty? What driver do you use?

2. Nevermind, I figured this out. Pretty much, to remove ndiswrapper, just delete it from /etc/modules (if it's in that file) and /etc/modprobe.d.

3. Could this be a router, modem, or cordless phone problem? Everybody in the house does have these problems. Three of us have them quite frequently, but one who uses a Vista machine says that he only has problems when a cordless phone is in use. However, he doesn't use his computer as much as us, so that could be the reason.

---

### Post by DeathOnJuice on 2007-06-28
Bump.

---

### Post by DeathOnJuice on 2007-06-28
Bump.

---

### Post by DeathOnJuice on 2007-06-29
Bump.

---

### Post by DeathOnJuice on 2007-06-29
Bump.

---

### Post by Genecks on 2007-07-02
I'm curious. Do you have any filtering or security on your router?

I was just thinking about electronics and computer science. I suppose the router and USB adapter would communicate and bicker before validating each other. This could perhaps drop the connection more and perhaps put too much stress on the USB when it comes to Linux. Maybe there are some programming and hardware errors when it comes to using certain devices. Maybe the drivers weren't built well enough, so things screw up; but yet in Windows things seem to work perfectly.

When I first used Kubuntu, my wg111v2 wireless USB network adapter was working fine. I didn't have to set a single thing up. However, I later implemented MAC filtering, and for some odd reason, things aren't working like they should be. You would think they would work, but they aren't.

I'm starting to think that maybe using ndiswrapper with the correct files provided by the manufacturer will help resolve any type of program/software/firmware error that's been going on lately.

Or it could be a great conspiracy, where people sent others to update the netgear BIOS with faults, so you can no longer use it in Linux. Because I'm paranoid, I'll mess with the netgear.

==UPDATE==

I recently messed with my router. I turned off MAC filtering. Afterwards, I checked Kubuntu to see if there were any improvements. No improvements were made. I changed another setting on the router. I enabled broadcasting. Before it was turned off, so people average people couldn't tell there was a wireless router in this place of establishment. After doing that, I retried connecting with the wireless USB. This time, it actually worked. The wireless USB worked.

This, however, says a couple things:

1. Broadcast has some problems.

I don't know what those problems are, though. I'm thinking this might be WIndows related. IN other words, the router is more attuned to WIndows than it is LInux. I'm not too knowledgable about wireless products and their interaction with operating systems, so I can't give much input on that realm.

*excuse the typos, the keyboard settings in LINux are not fast enough.

---

