---
title: "Dell u3415w goes into power save mode immediately when trying to install ubuntu?"
date: 2016-02-03
forum: General Help
---

### Post by PsychedelicWonders on 2016-02-03
i have a new dell u3415w and a new Asrock x99m Extreme4 mobo and intel 5820k build and it boots up the Ubuntu startup menu fine to either run as a LiveCD or do a full install.

No matter which option I choose it goes to a grey screen and then immediately the monitor goes into Power save mode.

Any idea why it's doing this and what the fix is so I can use ubuntu?

---

### Post by Vladlenin5000 on 2016-02-03
It's probably due to the graphics card which I guess is somehow new therefore not yet supported by the default open source driver... And, again guessing, Nvidia?

---

### Post by PsychedelicWonders on 2016-02-03
Yes graphics card & system are brand new, it's an EVGA 970 GTX with Nvidia chipset.

What can I do to fix this?

---

### Post by Vladlenin5000 on 2016-02-03
If this is your first UEFI system then this reading is a must: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
There are some new things you should be aware of, the new UEFI is different from the old BIOS.
Do not try older releases. The 14.04 LTS might be tempting (because LTS) but don't go there. Use the current release or even the yet to be released next LTS, 16.04.

Then comes the graphics card issue and for that you need to edit the Try Ubuntu (or Install...) entry in the GRUB menu and add **nomodeset** to the same line where "quiet splash" is, save and exit. This will give you video albeit a low resolution one but at least you'll be able to see something and interact with the installer. Proceed with the installation as usual.
Reboot when finished and immediately press some key in order to bring up the same GRUB menu; repeat the nomodeset procedure otherwise you won't have video as before. Then install the recommended Nvidia proprietary drivers that you can find in system settings > software properties > additional drivers tab. You can also select the "Intel microcode" for CPU in the same tab (optional). Apply and reboot when finished.

---

### Post by PsychedelicWonders on 2016-02-03
I'm pretty sure I have 14.04.3 - so don't use this one, download the 15.10?  

I don't see a 16.04 on their website? 

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

---

### Post by Vladlenin5000 on 2016-02-03
[http://www.omgubuntu.co.uk/2016/01/ubuntu-16-04-alpha-2-released-available-download](http://www.omgubuntu.co.uk/2016/01/ubuntu-16-04-alpha-2-released-available-download)
(link inside) and you can also read about what's new (not much)

---

### Post by PsychedelicWonders on 2016-02-03
It says that 16.04 is more for developers, should I just go with the 15.10?

---

### Post by Vladlenin5000 on 2016-02-03
16.04 is pretty stable right now, many people use it without any issue, but yes, it hasn't been officially released yet.
15.10 should be fine as well and you should be able to easily upgrade in April.

---

### Post by PsychedelicWonders on 2016-02-04
Ok I think I'm going to go with 16.04, especially since the LTS is right around the corner.

But am I blind?  I don't see a link to download Ubuntu 16.04 Alpha 2?

I see Ubuntu Mate, Kylin & Lubuntu, but not just the regular Ubuntu 16.04 A2?

---

### Post by PsychedelicWonders on 2016-02-04
bump

---

