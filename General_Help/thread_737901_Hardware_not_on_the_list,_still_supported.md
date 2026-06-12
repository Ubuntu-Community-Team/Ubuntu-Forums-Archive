---
title: "Hardware not on the list, still supported?"
date: 2008-03-28
forum: General Help
---

### Post by TRS on 2008-03-28
First off. Hi all!

I guess one can call me a newbie when it comes to all things linux (and in some ways (sub-user level or what you may wanna call it) computer illiterate), I've been a windows user as long as I can remember, and thus I'm rather uncertain on a few things.

I'm keen on trying out a Linux distro, and quite frankly, Ubuntu is the one I've heard the most about, so here I am. But as it can be/is so much info incoming at once, I get information overload and have to take a walk to clear up, and anyhting usefull picked up is lost, so I think I'll take my time in learning it, as I do want to try it for myself if it works on my hardware, as I cannot make an informed decision based on other peoples experiences.


My computer contains an Athlon 64 3200+ (Winchester core if that matters), which I have deduced will work with Ubuntu (so far so good I guess).
I also run a GeForce 6800GT video card, which wasn't on the compatability list (the model, as far as I could see), but it had "GeForce 6 series" listed, so I assume my card should work fine then?
My motherboard wasn't listed either, and for the record, this is a Gigabyte K8NS Ultra-939 nForce3 250

I also have some other components, like an IDE controller (yes, It's been a while since I updated my rig), and a network card (my motherboard has one built in, but I run 2 for internet connection sharing).

I'm assuming all these components will (or can?) work if I can find drivers for them? Or is there some other issue that may arise like it simply just doesn't like some of my hardware? (That sounds really weird in a way, but I've encountered a good deal of weird things, so better safe than....well not so safe)

For instance the nvidia site has linux drivers listed for my series, and since my motherboard has an nvidia chip as well, I can only guess that I'll be covered on the chipset drivers as well.


Also I'm wondering about the 32bit/64bit thing. I'm currently (which is what I'm changing from) running win2k with Service Pack 4 32bit (don't even know if there is 64bit for win2k). Will I need, or at all gain anything by installing a 64bit version of Ubuntu?

If it matters, I'm currently running 1GB of ram, but will be running 4GB when I next upgrade my computer (will be a new one that is, and as my "motto" is: rather have more than need more :))

Regards,
TRS

---

### Post by mlapaglia on 2008-03-28
pop in an ubuntu live cd and you'll get a very good feel for what is and isn't going to work. You video card has been made within the past few years so it should be supported just fine. IDE and network should also be fine. i run a athlon x64 dual core with ubuntu and it works well.

64 bit will give you an advantage if you are using programs that really need 64 bits. since ubuntu is open source you'll find most if not the majority of everything is made for x64 platforms. you'll run into trouble with java and flash plugins for firefox, but nothing that doesn't have a decent work around.

---

### Post by TRS on 2008-03-28
I took your advice and downloaded the image and ran a little test.

The hardware information looked to have all my cards and such listed. Both ethernet's, the sound and gfx, and even the IDE-controller was there. Also all the partitions were showing.

I tried watching one of the samples (with Mandela), and sound worked like it should, as did video.

It ran a little slow with starting up etc, but I guess that's just the fact that it was loading it all from a CD.

The one thing I noticed was that I could change resolution, but not the refreshrate. Is this just a result of having "generic drivers" kind of? So if I install and get the nvidia drivers it will be sorted?

All in all it looked to be ok, I didn't get any error or anything as if there were any hardware issues (I imagine I would get a message if there were?).

I think I may give this a real shot once I sorted backup's of my data.


Regards,
TRS

---

