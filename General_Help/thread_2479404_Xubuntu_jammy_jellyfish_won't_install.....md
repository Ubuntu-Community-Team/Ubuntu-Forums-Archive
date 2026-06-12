---
title: "Xubuntu jammy jellyfish won't install...."
date: 2022-09-23
forum: General Help
---

### Post by jakemaverick911 on 2022-09-23
So, d/l'ed latest xubuntu today, burnt the disc and it won't install all even run from the optical drive.

Menu comes up but keeps falling over part way through. AMD system although I suspect it could be a graphics card issue, Radeon VTX3D 1GB HD5450 DDR3 SDRAM Graphics Card.

I have gone to the onboard graphics and that hasn't helped at all. Is it possible physically removing that card may help? I'm sure I've had similar problems with graphics card when trying to install before.

I also saw some error messages flash up, can't think exactly now, but something like a library or volume could not be found. I've burnt two discs so I don't think that's a problem... so bit stuck right now :-( Hope somebody can help!

---

### Post by QIII on 2022-09-23
Hello.

Laptop with hybrid Intel/AMD Graphics?  Desktop with an AMD APU and a dedicated 5450?

Any messages that might have popped up that said "something like" are not helpful for diagnosis.  Exact messages are.

It would be very helpful if you could include details when requesting assistance.

---

### Post by jakemaverick911 on 2022-09-23
yes, apologies for that just abit frazzled and i just didn't recall exactly what it said by time i logged in here, will try again tomorrow and jot it down...exact spec of PC though

G7 Power Extreme 580W Desktop PSU ATX Power Supply Unit
Radeon VTX3D 1GB HD5450 DDR3 SDRAM Graphics Card
2 x 8GB ram = 16GB
usb3 card
120 GB ssd
Gigabyte GA-F2A68HM-HD2 FM2+ / FM2 Motherboard with Amd A6-7400 APU

not sure if that helps at all. just had all my kit stolen so this is just a spare PC they didn't manage to nick :-( so bit of a mess atm, please bare with me

---

### Post by QIII on 2022-09-23
Please use the default font and color unless there is something to which you would like to draw special attention, and then only sparingly.

From what URL did you download the image?  [Did you verify your download?]("https://ubuntu.com/tutorials/how-to-verify-ubuntu#1-overview")  Have you burned all images from the same download?

Unless your hardware is damaged, none of what you have there should be an issue in and of itself.

---

### Post by jakemaverick911 on 2022-09-23
sorry i did not realise, must have happened when i copied and pasted the text for system spec. my eyes aren't great atm, really struggling.

[https://cdimages.ubuntu.com/xubuntu/releases/22.04/release/](https://cdimages.ubuntu.com/xubuntu/releases/22.04/release/)

was where i got it, did not know about verifying. I shall look into that tomorrow but it looks a bit complicated at first glance. getting bit late now tonight! thanks for your help.

---

### Post by grahammechanical on 2022-09-23
The information in this link may help.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

See the heading Changing the CD's boot options. See section 6 - F6 Other options. Select nomodeset. The installer may then run without a video mode being set. 

Regards

---

### Post by jakemaverick911 on 2022-10-06
Thanks Graham! Sorry for delayed reply but i've been ill/ laid up all week and not had the strength to do much. Just got back to it today and seems I don't have that option in Xubuntu. Here's the strange thing though, trying it from a usb optical drive now and it was whirring away for over an hour, getting quite hot. At one point it did say it was downloading something extra, then screen went black for 50+ minutes. So I ejected the disk...then the graphics flashed up! So I popped disk back in and click the install button...then it was just whirring away for ever. So had to cancel in the end. I know from previous installs it doesn't take anywhere near that long. With the desktop/ home/ graphics finally flashing up when I ejected the disk, I don't think it's a graphics issue. Although was a different monitor this time. I think xubuntu just doesn't like my hardware :-( I'm looking to get another system though...so hopefully install will work on that one!

---

### Post by jakemaverick911 on 2022-10-06
so i just tried the early version before this jellyfish...that seems to work fine! Only trouble is it wouldn't detect my windows installation and other files automatically and I have no backup atm. So had to cancel it, couldn't risk it. Is there a problem with detecting windows 10?

---

### Post by tea for one on 2022-10-06
> **jakemaverick911 said:**
>  Is there a problem with detecting windows 10?
Is Windows 10 hibernating or encrypted (bitlocker)?

---

### Post by jakemaverick911 on 2022-10-06
> **tea for one said:**
> Is Windows 10 hibernating or encrypted (bitlocker)?


ah, forgot to mention...when i tried with jellyfish earlier tonight i did notice in the text that it did say windows hibernating! I didn't know on that, I just did re-start- very new to windows 10. So after that I did a cold start and booted from the optical, so it shouldn't have been. I'm not sure on encrypted or bitlocker, how do I tell? It was on the drive when I bought it. Just had all my kit nicked :-( So it's cobbling stuff together atm, just to get back online and keep working.

---

