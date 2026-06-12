---
title: "[SOLVED] Wubi, I love my Computer. Are you safe?"
date: 2008-05-21
forum: General Help
---

### Post by jackhe22 on 2008-05-21
Hello people of the world,

I love Ubuntu. I use it on VMware. I really have always wanted to use Ubuntu on my machine, but its a game's machine with lots of valuble files on it. I was convinced to Wubi, as no partitioning was nessersary. Is it safe for a valuble game's machine?

PLease reply!

So far I have:
Wubi-8.04.exe
ubuntu-8.04-desktop-i386.iso

Thanks! :confused:

---

### Post by ago on 2008-05-21
yes it is safe, just avoid hard reboots. Anyway you should always backup, whether you use wubi or not.

---

### Post by jackhe22 on 2008-05-22
Okay Thanks!

I am now typing this in Wubi!

The only thing that scared me is that earlier today the power went out while booting Wubi! I was scared out my pants!

One more question:
I have a GeForce 7600GS, and the Desktop Effects dont work.
I have now realized that I need the one from the site, but is it safe?

Thanks!

---

### Post by Twilight in Zero on 2008-05-22
You have to enable the restricted drivers, I think. ATI had restricted drivers, I'm not sure about NVidia. Go to System -> Administration -> Hardware Drivers.

---

### Post by jackhe22 on 2008-05-24
Yay!

I have effects on Extra, flash player and Kstars on!

Thanks for all the support from you lot!

Gonna go and install TuxPaint now!

---

### Post by jackhe22 on 2008-05-27
Hold Up! I have taken it off as It put itself to Hibernate and messed everything up. The Computer keeps freezing now, so I ran chkdsk C:/r and am back to normal. I also Defragged. But I am thinking of putting it back on again.... I did it a second time and succseeded but my brother who is not very smart with computers tried booting up Ubuntu in safe mode (messed it up) They say third times a charm.... Still. Should I?

---

### Post by ago on 2008-05-27
Hibernation is not supported by wubi (see FAQ/guide)

---

### Post by jackhe22 on 2008-05-27
Oh great: Its still freezing in Windows, so I ran chkdsk again and there is no difference. PLEASE HEEEEEEELLLLLLP!!
I am typing this on my MacBook.:(:confused:

---

### Post by ago on 2008-05-27
try to run ntfsfix from linux before running chkdsk

---

### Post by jackhe22 on 2008-05-28
Just out of Interest,
ago, do you actully work at Wubi? because the Screenshots on the website have ago in them!

---

### Post by ago on 2008-05-28
> **jackhe22 said:**
> Just out of Interest,
ago, do you actully work at Wubi? because the Screenshots on the website have ago in them!

Yes I wrote most of wubi, with help from other devs (see the credits section in the faq for a full list). The "ago" in the login screenshot actually is there bause that is my windows username, and when I took the screenshot I forgot to delete it.

---

### Post by jackhe22 on 2008-05-28
Cool!,

Later tomorrow after backing up, I will try it for the last time. If it dosent work this time, i will just use XUbuntu on my old Packard Bell.
May I also add - I would Love for Ubuntu Studio to be on Wubi...

---

### Post by ago on 2008-05-28
You can install Ubuntu studio packages from ubuntu. Only flavors that come with a live CD can be supported at the moment.

---

### Post by jackhe22 on 2008-05-28
> **ago said:**
> You can install Ubuntu studio packages from ubuntu. Only flavors that come with a live CD can be supported at the moment.
Okay thanks!
A friend said to me that Wubi 7.04 had a UbuntuStudio Option. As much as I love editing films and music, I dont like using Beta programs....

---

### Post by ago on 2008-05-28
Yes because 7.04 was using the alternat installer, while 8.04 uses the LiveCD one.

---

### Post by jackhe22 on 2008-05-30
Yes! I am back in Wubi now, and have never been happier!
Cheers Ago!
Gonna install the Ubuntu Studio programs now!

---

### Post by jackhe22 on 2008-05-30
Last thing though...

In the top corner of Ubuntu is says I have sound (icon), and I dont.
The card is a Sound Blaster Audigy

---

### Post by ago on 2008-05-30
> **jackhe22 said:**
> Last thing though...

In the top corner of Ubuntu is says I have sound (icon), and I dont.
The card is a Sound Blaster Audigy

Check the appropriate support forum, this is unlikely to be a wubi-related issue. You might have to add an appropriate driver and/or change your configuration.

---

