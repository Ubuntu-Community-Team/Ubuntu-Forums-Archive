---
title: "MotoRokr Z6m + USB (or bluetooth) + Hardy = Sees hardware but can't do anything"
date: 2008-05-26
forum: General Help
---

### Post by Stochastic on 2008-05-26
So I've been attempting to get my new Motorola Rokr Z6m (note this is NOT :roll: the linux-based Z6, but rather the old CDMA motorola system) to be recognized or even readable by Hardy.  I can't seem to do it, I've been able to get the bluetooth address seen by "hcitool scan" and I've been able to get the hardware address via USB through moto4lin (in the preferences dialog) but I have not been able to connect either way.  I'm wondering if I'm missing a step, or if I need to go about things in a different manner?  I'm new to fancy phones and this is the first one I've ever attempted to connect to my computer, so treat me like a bit of a newbie.

---

### Post by all2ez on 2008-07-07
Not sure if you figured this out yet, but I have the same phone and it works great in Ubuntu (I'm on gutsy).  I never figured out the bluetooth but never really needed to because the usb is more practical anyway.

You may have the same problem that I had at first, which is that I didn't realize that there has to be a microSD card in the phone before you can do really anything.

Once you get the card in there, you can format it through the phone  (Phone Info > Storage Devices, Scroll to Memory Card-microSD, press Options, Scroll to Format and press Select).  After that your phone will act like a basic usb drive when you connect it to your computer.  Mine auto-mounts to /media/PhoneName and an icon shows on the desktop.  You can then copy music into the My_Music folder (subfolders are ok too).

I use Amarok to manage my music and it can access the phone as a media device and transfer files to it also (after some configuration).  This has the advantage of automatically creating subfolders and custom filename formats to keep things organized.  Checkout [http://amarok.kde.org/](http://amarok.kde.org/) for more info on that if you haven't used it before.

There is a big annoying catch though.  The songs on your card can't be used as ringtones, only songs on the phone's actual internal memory can be selected in the ring details.  The internal memory isn't even big enough to hold a full song and I don't think there is any possible way of accessing that memory through Ubuntu or through phone itself (other that seeing the status).  

I cut a couple of song intros and got them on when I first got the phone.  I think I used Audacity to edit the songs to about 30 seconds of intro and then got them onto the phone using the Jump software from Motorola which I put on my Vista computer (I have to use windows at work).  I think I was also able to push a file on there using the Bluetooth on my Mac OS X also.  I know the file transfer worked but that was about six months ago so I don't remember if the file went to the phone or to the card.

If you or anyone else has figured out the Bluetooth I'd love to know how to do it but it's not a priority for me so I haven't bothered working too hard on that.

---

