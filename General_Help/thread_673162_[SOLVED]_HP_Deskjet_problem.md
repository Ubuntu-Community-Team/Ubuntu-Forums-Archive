---
title: "[SOLVED] HP Deskjet problem"
date: 2008-01-20
forum: General Help
---

### Post by editrix on 2008-01-20
This is a duplicate of a post I made to the Hardware forum, but no one's answered.

I have a Deskjet 3847 which worked fine in Windows. Then I did two things:

1. Bought cheap, no-name replacement cartridges
2. Installed the printer in Kubuntu Dapper.

According to [http://hplip.sourceforge.net/support...es/inkjet.html](http://hplip.sourceforge.net/support...es/inkjet.html) the printer is supported in HPLIP 0.9.5, and I have 0.9.7, but I couldn't find 3847 in the list of printers. So I'm using the 3840 driver.

The printer will not print in draft mode. Someone suggested it's because it's a no-name cartridge. Or, it could be because I'm not using the correct driver. I emailed HP and they didn't even answer.

Before I go out and spend my food budget for the month on genuine HP cartridges, does anyone have any ideas?

---

### Post by linuxwizard on 2008-01-20
What other printer models are listed ? Is there a 3845 ? Have you tried using some of the other printer models ? Are you using the HPLIP Toolbox their are more setting in there you can adjust ?

---

### Post by editrix on 2008-01-20
Hi, Thanks for the reply.

[QUOTE=linuxwizard]What other printer models are listed ?[/QUOTE]

Quite a few. I tried the one closest in number, because that's what we used to do back in the days of dot-matrix printers.

>  Is there a 3845 ? Have you tried using some of the other printer models ? 

Didn't try other models because I was so proud of myself I actually installed a printer without help :-(

But, if it's supported (see original post), I don't understand why the model's not listed.

> Are you using the HPLIP Toolbox their are more setting in there you can adjust ?

I didn't even know there was a HPLIP Toolbox. I've just been using whatever there is in KDE's Control Centre.

Okay, I found it. When I hit Configure, I got this:
DeskJet-3845
	Description: HP Printer 
Location:
Make and Model: HP DeskJet 3845 Foomatic/hpijs (recommended) - HPLIP 0.9.7
Printer State: idle, accepting jobs, published.
Device URI: hp:/usb/Deskjet_3840?serial=TH47A132S9040R

It's a usb printer, so shouldn't it say something in the Location line?

---

### Post by linuxwizard on 2008-01-20
Don't worry about Location line you can add USB if you want. Does the printer work now ? I see that it got detected as 3845. Can you change your print mode?

---

### Post by editrix on 2008-01-21
Aargh! I feel like an idiot, but I just solved my own problem. Sometimes, you have to ask the question just to kick-start yourself into finding the answer. Anyway, feel free to ignore what's below. It's what I wrote *before* I went searching. Short version is, I was using the wrong driver. Installed a "new" printer, 3845hpijs, and it's all hunky dory (she says as she tries to find a rock she can hide under).

                                                                                   *********************************

> **linuxwizard said:**
> Don't worry about Location line you can add USB if you want. Does the printer work now ? I see that it got detected as 3845. Can you change your print mode?

Sorry I take a long time to reply. I'm on dialup, so I can't get to the forums easily.

I wasn't clear in my first post, and apologize for that. The printer prints fine in regular mode. When I change the Properties (or whatever it's called in that particular program) to draft the heads move, the paper moves, but nothing comes out of the cartridges.

The KDE Control Centre Add Printer Wizard lists some very strange things (see attachment). I've never owned an Epson or Canon or a parallel port printer on this machine so I don't know where those came from.

Also, in the drop-down list of printers, I see there's two 3845s: one with hpijs after it and one without.
I've no idea why I didn't try one of them.

I will now, but I'm virtually out of ink (reason for original post: should I buy the expensive HP cartridges) so it won't be a fair test. Sigh!

---

### Post by linuxwizard on 2008-01-21
That is why I asked if 3845 was listed. From what I found searching that is what you needed to use for your printer. Well that's good everything is working for now. Please mark thread SOLVED.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

