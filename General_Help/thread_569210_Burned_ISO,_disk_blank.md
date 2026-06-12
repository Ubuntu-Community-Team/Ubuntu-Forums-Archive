---
title: "Burned ISO, disk blank"
date: 2007-10-06
forum: General Help
---

### Post by rivalarrival on 2007-10-06
This is actually the first time I've tried burning an image in Ubuntu...

Short version: Burned to CD, ejected, put it back in, disk is blank

Long Version:

Trying to burn an iso image (edubuntu server image, not that it matters) with Ubuntu Feisty. I was pleasantly surprised to see the right-click > write to CD option. Completed OK (didn't see any options about dummy-burning or simulation only)

The disk is blank. Tried again with a different disk, same thing.

Tried wodim file.iso at the console, it gave me every indication that it was working, but returned the disk blank.

Hardware is known-good - I ended up burning it from my windows installation - but I'd like to figure out WTF is going on here.

Any thoughts?

Thanks!

---

### Post by ryanVickers on 2007-10-06
Could you try K3B?  Also, make sure you burned it as a disk image and not as a file - but it would still have data on it then anyways...

Also, are your sure the disk image was complete and good?

Edit: I just thought of this - are the disks *really* blank - like you can still write to them, or are they completely wrecked?  If they are just blank and still usable, then there's a different problem, like it doesn't do anything :), but if they are wrecked, then it "burnt" it, but skipped all the data or something:confused: ...

---

### Post by rivalarrival on 2007-10-06
Absolutely positive the ISO was good - burned it in windows on the same hardware. Disk is definitely blank - nautilus brings up the burn wizard.  Also by physical inspection: on a burned disk, you can see the difference between the burned inner tracks and the empty outer tracks - nothing on the disk (or it's full to the edge...)

I'll try K3B and be right back.

Edit:

They are absolutely, completely blank. I've dealt with coaster issues (this drive and generic CD-Rs don't get along, and it likes to take its time writing lazily along at 4x. If you push it, it coasters your disks)  Coastered disks would mount in windows, but with 0 bytes on the disk. 

With the current problem, it's like the damn thing is in simulation mode. It spins the disk, the lights blink appropriately, but the disks come back the same as when I put them in.

I might mention that this is my absolute first attempt at burning CDs in Ubuntu... I probably have to beat the "Stupid Genie" out of the computer...

---

### Post by ryanVickers on 2007-10-06
It should work ok - It's really the best - most options, most modes... only defect is it's not a gnome app :p

But I have to ask again, out of curiosity at least...
>  Edit: I just thought of this - are the disks *really* blank - like you can still write to them, or are they completely wrecked? If they are just blank and still usable, then there's a different problem, like it doesn't do anything :smile:, but if they are wrecked, then it "burnt" it, but skipped all the data or something:confused: ...

---

### Post by d_xtremw on 2007-10-06
maybe you can try downloading another copy of the iso file or downloading a different iso altogether  so you can start tracing the root of the problem. maybe (although unlikely) something might even be wrong with your burner drivers in ubuntu

---

### Post by Lord Illidan on 2007-10-06
What speed? Generally I always use 4-8x..never go above that limit.

---

### Post by ryanVickers on 2007-10-06
In theory, any speed should be fine, but I recommend 4x, no faster.

---

### Post by rivalarrival on 2007-10-12
Well, it appears to be a hardware problem after all...

I just got a coaster while burning in Windows, and the replacement I burned was completely blank. 

Looks like an intermittent problem with the writer.

Thanks everyone!

---

### Post by ryanVickers on 2007-10-12
I'm still interested if the disks came out truly blank (still usable) or if it wrecked them also... ;)

---

### Post by skclewis on 2007-10-22
Rival and Ryan,
Hope you can help me too.  I am having the same problem.  I have downloaded the ISO from three different mirrors and still cannot get the image to burn. I have used ISORecorder V2RC1 as recommended by the download page as well as InfraRecorder 0.43.1.0 unicode x86 since I am running Windows XP Pro SP2.  With ISORecorder I get an error message 80004005 which tells me nothing (can't even find out anywhere what the code means).  InfraRecorder starts then spits out a blank disk,  I have also used Nero with the same results.  Anyone have some help here?

---

### Post by bitterbug on 2007-10-22
Infra Recorder (under windows) was spitting out burned but useless disks for me as well when trying to burn Gutsy. K3b would completely lock the system after burning, but at least the disk would be good. Even REISUB wasn't capable of recovering the machine :(

It's an LG DVD Multi (+/-/RW/RAM) burner in my case. What brand are you using?

---

