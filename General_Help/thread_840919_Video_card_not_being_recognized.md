---
title: "Video card not being recognized"
date: 2008-06-25
forum: General Help
---

### Post by Kakteed on 2008-06-25
Okay, so, currently I am dual-booting Windows XP and Ubuntu8.0. I set this up two days ago, and I can boot into both OS without a problem. The problem is, though, that Windows XP will not recognize my video card. My video card is a Radeon X1650. I thought it might just be that the drivers weren't updated, but when I looked around it showed that Windows wasn't recognizing my video card. I can still see a graphical user interface in Windows, however, so I assume it is using my motherboard's onboard video? How do I make it recognize my video card?

Also, it doesn't seem to realize that my motherboard has audio, and so I can't get any audio at all when in Windows XP. Audio is working, however, on Ubuntu. I know that this isn't a Windows forum, but I didn't know where else to ask.

---

### Post by Kakteed on 2008-06-25
Does anybody have any advice for me? Or can point me in the right direction?

Please, I would really like to fix this!

---

### Post by VMC on 2008-06-25
> **Kakteed said:**
> Does anybody have any advice for me? Or can point me in the right direction?

Please, I would really like to fix this!

Here is a link to someone with your video card. He actually got it to work. Hope it works for you:
[http://ubuntuforums.org/showthread.php?t=691559](http://ubuntuforums.org/showthread.php?t=691559)

---

### Post by Kakteed on 2008-06-25
Thank you very much! :)

EDIT: That appears to be how to get the card working in Ubuntu... I already have it working in Ubuntu (I think??).

---

### Post by VMC on 2008-06-25
> **Kakteed said:**
> Thank you very much! :)

EDIT: That appears to be how to get the card working in Ubuntu... I already have it working in Ubuntu (I think??).

I'm sorry. I'm so use to it being reversed! What versions of the XP drivers do you have?

Here is a couple of links that may help. One labeled vista, but it appears to be for XP.

[http://www.xpvistaworld.com/radeon_x1650_series_205.htm](http://www.xpvistaworld.com/radeon_x1650_series_205.htm)

[http://driverscollection.com/?H=Radeon%20X1650&By=ATI](http://driverscollection.com/?H=Radeon%20X1650&By=ATI)

---

### Post by Kakteed on 2008-06-25
I have already downloaded and installed the second one, and XP still appears not to recognize the video card. Am I just out of luck, or should I try the other one? Is there something specific I have to do, other than just run the .exe and let it install automatically?

Thank you so much for taking the time to help me, I appreciate it a lot.

---

### Post by AmericanYellow on 2008-06-26
Okay, I had the same problem before several times with my graphics card and audio card. Read everything here first before doing it.

The first thing you should do is check Windows "Device Manager" to see if Windows detects your card or not or whether you just need the correct drivers.

Right click "My Computer". Go to "Properties". Click the "Hardware" tab. You should see something that says 'Device Manager' or Device something (I am not in Windows while typing this so I am going off memory). Then right-click the first icon that appears (which should be your computer's name) and select 'Scan for new changes'. After that, check the list of devices and see if you can see your graphics card or at least a yellow question mark. If you see a yellow question mark that says "Video Device' or "VGA compatible' or something related to a video device that it most likely your video card and you just need the proper drivers.

If you don't see anything that indicates that your card is not being detected, you should shutdown the computer, power down the box (the power switch in the back of your computer), disconnect every cable connected to the computer (the monitor, speakers, usb devices, even the power cable...Everything), and press the power button to dissipate any remaining power in the computer. After about 5 minutes, reconnect everything, but make sure to connect the power cable last. Then turn on the switch in the back of the computer. Let the computer sit for another 5 minutes after turning on the switch in the back. Then power on the computer. Make sure you go to Windows first and check "Device Manager' to see if your card is detected. If not, you should repeat this once more.

After repeating and Windows still doesn't detect your card, you should disconnect all cables again, open the computer box itself, remove the video card and re-seat it in its slot. While doing this, you should clean the inside with "pressurized air in a can" that you can usually get in computer stores (especially if the inside is really dusty-this sometimes can be causing your motherboard and other devices to behave abnormally). After this close the computer and reconnect everything and hopefully your card will be detected when you check Windows 'Device Manager'.

For me, this worked. If this doesn't work, you should open up the computer, remove the card, close it, log in to Windows, then shutdown the computer, and put the card back in. You might also want to try putting the card in a different slot if possible.(the slot might have gone bad).

Lastly, Windows still doesn't detect your card, reinstall Windows. After this your card should be detected.

Remember, every time you disconnect the power cable press the power button to dissipate any residual power in the computer. Also, static energy can damage your computer so do not perform this on carpet and don't wear anything that can generate static energy. (To take extra precautions you could wear gloves, but I think thats excessive).

If you have done everything above and nothing worked, you can try taking the computer apart completely and putting it back together. And what I mean is disconnecting all internal hard drives, CD/DVD drives, Ethernet or wireless cards and anything you can, then reconnect everything. 

I did all this once and it got my card working also. I discovery that my computer was really really dusty inside and that my motherboard was detecting my card right. By taking everything apart and reconnecting it "reset" my box in a sense. If you don't feel like disassembling your computer, you can try reinstalling Windows first.

Good luck!

---

