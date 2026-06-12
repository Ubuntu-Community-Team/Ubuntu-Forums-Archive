---
title: "Problem with Samsung S630 - No Auto Detect"
date: 2007-04-23
forum: General Help
---

### Post by samichx on 2007-04-23
Having had a fair share of trouble setting up Samsung printers - only to find pride in overcoming the challenge I've been left in a bit of a pickle. 

The Samsung S630 Camera in not automatically detected, it's not even detected as a card reader. I've checked the unit and connector using another computer (XP-PC) and it all works with the software packaged with the camera. The software does not seem to function properly in Wine yet - even if it does work I'm hoping there is an OSS solution out there.

This endeavor has been undertaken with a copy of Feisty although it also does not work on my girlfriends Dapper release. I've been through the loops and would appreciate any assistance.

(BTW If you are a fellow S630 user don't let this stop you from using a solid, cost-effective unit)

---

### Post by samichx on 2007-05-23
Problem Solved - as well as numerous others having to do with reading USB devices. Input the following command in the terminal:

sudo modprobe -r ehci_hcd

Or add that as a command in the sessions section of the System > Preferences menu.

---

### Post by cocobaby on 2007-06-06
hey i just got this camera and i cant load my pictures to my computer, it is saying i/o device error...is this the same problem you were having and if so do you know how to fix it? im really so slow with computers! please help and please dont tell me to buy a card reader :(

---

### Post by samichx on 2007-06-07
You shouldn't have to buy a card reader, although you may want to remember that your camera has the card slot as well as the onboard memory, which do not mix when you plug it in. Whether you have a card in OR use the onboard memory the following procedure applies.

1) Startup your PC/Laptop without the device being plugged in or turned on.
2) when logged in open a terminal window and type sudo modprobe -r ehci_hcd 
enter your admin password accordingly
(alt-f2 does not do the trick even with gksu)
3) Plug in the connection wire to the PC and camera in no specific order.
4) Turn the camera on using the button on the top.
-------- This is where people normally have problems, modprobe should have fixed them preemptively. -------
5) When the Camera asks you to choose between "Computer" or "Printer" you should choose Computer, 
(this might seem obvious although there are Pictbridge programs elsewhere that may require the other option.)
6a) It worked and if you want to import it will ask. Otherwise you can acess the memory as disk or disk1, 2... on your desktop. Which is probably your safest bet. Congrats, and don't forget to unmount before unplugging!

6b) If it does not respond, YOU have done something wrong. Don't worry though, if you're smart enough to choose Ubuntu you can try these steps again until auto-detection works. It's not just the camera, its also card-readers and storage devices.

6c) In the special case it does respond by making the screen go black on the camera, but Ubuntu still will not accept it I would suggest the following. Search the forums more for your specific error, and implement the remedy found there.

---

### Post by samichx on 2007-06-07
@cocobaby
I'm sorry, that error didn't happen with mine. It generally is good to find a card-reader for when your batteries die and you need to access the card. Although my friend had a similar problem. So try this:

1) Get gparted (apt-get install gparted) - this will allow you to view and augment partitions.
2) Plug in the camera the way you did (hopefully according to my guide
3) Open GParted and you'll find a tab on the right (hda, sde, etc.) find your camera/card - it will be marked as unallocated. Otherwise there is a problem, Close Gparted.

That's the problem.

My same card inserted into an MP3 player with SD or a reader is FAT16. Other devices are normally FAT or FAT32. the File allocation tables system is central to devices right now. If you formatted it as NTFS, or any other jib-jab then it will not be accessible through the Samsung USB.
At Canadian Wal-Mart locations the photo machines or desk staff can usually help you erase your SD and format as FAT16 or whatever their default is, although with a proper card reader you could do the same from home.

I'll tell you this - when it does work for you this camera is the best. The videos offer decent quality and format for editing in Ubuntu, and the Samsung High-Def lenses keep your pictures crisp and clean as opposed to my last digital camera. This is a low-cost high-end camera, and you get what you pay for - quality parts with some minor frustrations.

Let me know if you solve it.

---

