---
title: "Hard drive not seen after switching it to a SATA 3 port."
date: 2013-12-24
forum: General Help
---

### Post by Blix775 on 2013-12-24
So I've been using this 2TB hard drive for storage for about two months now. It's replacing a 1TB hard drive that failed. Well, my motherboard has 2 SATA 3 ports that I had completely forgotten existed. So I got a new case yesterday and said to myself "Why have you not connected your new SATA 3 hard drive into one of those SATA 3 ports?" And so I did! ...Well, after I did that, my Lubuntu installation is not detecting the hard drive anymore. Everything in my setup is the same except I moved that hard drive into a SATA 3 port. I was thinking about just installing everything from scratch so that it would see it but then I would have to redownload my whole steam library of games and I don't want that. For some reason the backups of my games some times do not work in linux and linux insists in downloading the game after it supposedly used the backup to restore the game. Weird thing but it has happened many times although not with all of my games. So I'm wondering if there is just some easy way to tell Lubuntu to look for the hard drive in one of the two SATA 3 ports instead of the old ones. Can anyone help me with this?

PS: My motherboard is a p6x58D Premium just in case that helps.

---

### Post by oldfred on 2013-12-25
Are you sure case is USB3 compatible.

We have seen some drive caddies that do not work with USB3 or do not work with large drives. Not sure what is in the case that makes a difference but some do not work where others do.

---

### Post by electrohandyman501 on 2013-12-25
1st thing I would look for is make sure in your bios settings that the specific SATA port is enabled. Not all motherboards have all SATA ports enabled by default.

After you have the SATA port enabled you may be able to see the drive, but it may not be identified the same as before. 
To change the drive identification, I think you can edit a config file with that information in it, but I don't know the name of it or where it's at. I seem to have read about it in other threads.

---

### Post by Blix775 on 2013-12-25
I'm not using the front pannel USB3.0 in the case because my motherboard does not have the pins for that. It only has two USB 3.0 in the back. 

I'll see if there's any mention of that in the Bios although when booting up it lets me know that there is a drive in the SATA 3 connection where it would previously say no hard drive found.

I'll check these recomendations out. Thanks

---

### Post by cincibluer6 on 2013-12-25
My bet is on the BIOS too. I struggled for a bit with the same thing then realized that Dell didn't enable 2 to begin with, just the 1.

---

### Post by Blix775 on 2013-12-26
My Bios does not give me any features to turn them on or off. This motherboard is from 2009 so I think its bios may lack some new options that may have become common lately. I'll run the Lubuntu disc live and see if it actually sees the drive while live. If it does, I'm reinstalling. ='[

---

### Post by Blix775 on 2013-12-27
Lubuntu does not see the hard drive no matter what. It seems my motherboard just doesn't work the way Lubuntu expects it to. I tried running lubuntu from the live cd but it did not see the drive so it's not a problem with the current configuration. Thanks anyways.

---

