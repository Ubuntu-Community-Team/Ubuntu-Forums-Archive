---
title: "Live for 20.04 no persistent session"
date: 2020-04-21
forum: General Help
---

### Post by georgesgiralt on 2020-04-21
Hello,
I would like to try the new LTS version before it goes official. So I downloaded the beta ISO image and using Rufus on a Windows machine made a USB stick for it. 
Then I created a "casper-rw" 4GB file (dd was of help) formatted it with mkfs and started a Lenovo Thiknpad E450 laptop with the stick on.
I edited the Grub command line to, at first, put the "persistent" word after the 3 dashes. No good.
I then tried to put the "persistent" word between splash and the dashes. No good.
I tried to replace "quiet splash" with persistent but still no good.
So I'm asking here, what I did wrong ? (this method worked well for 18.04) 
I will be glad to hear for all the help and advice you can provide ! 
Thanks a lot for it !

---

### Post by sudodus on 2020-04-21
If you have a current version of Rufus (3.9), it can create a **partition** for persistence. There will be the label 'casper-rw'. This will provide persistence with the current daily iso file (alias release candidate).

I don't remember exactly, but it is possible that the beta iso file was made before [this bug](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1863672) was squashed. Anyway, if you change the label to 'writable' (without quotes), persistence should work.

I have not tested a **file** for persistence recently, but I think that it will also work with the file name 'writable' instead of 'casper-rw'. (it is easy for you to test it.)

If you have a working Ubuntu system, you can also use [mkusb](https://help.ubuntu.com/community/mkusb). It creates the new label 'writable' for Focal Fossa, to be released as 20.04 LTS.

See the following link for more details:

[How is it easier to make a persistent live drive with Ubuntu 19.10?](https://askubuntu.com/questions/1181854/how-is-it-easier-to-make-a-persistent-live-drive-with-ubuntu-19-10)

---

### Post by georgesgiralt on 2020-04-21
Thank you VERY much for pointing me to the right direction !
Renaming the "casper-rw" file to "writable" (and of course, putting the word "persistent" in the Grub linux line) did the trick !
I searched a long time without luck. So your help was very valuable !
For the record, it is easier for me to have a file instead a partition for the persistence because I can easily move the file away and have one for each computer I plan to try the new version on. 
I have two laptops and one main computer with very different hardware (Nvidia cards on the main and one laptop, Intel on the other) so I like to try Nvidia support and switching on the laptop so fitted... 
Having a file dedicated to the changes made on one computer can help track things for me.
The link you provided is very interesting and I will read it again to get the most of it. 
Thank you and stay safe !

---

### Post by sudodus on 2020-04-21
Proprietary graphics drivers (e.g. nvidia drivers) do not work in a live or persistent live drive, because the driver is selected by the kernel before the overlay for persistence is activated. So I think you should use the same USB drive and can use the same file (or partition) for persistence in all cases.

You may need the boot option 'nomodeset' to boot with nvidia graphics, if the graphics chip is fairly new.

If you want to have a working proprietary nvidia driver installed, you need an installed system, which is possible also in a USB pendrive or SSD connected via USB. There are details at [this link](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/942312#942312).

---

### Post by georgesgiralt on 2020-04-21
"Proprietary graphics drivers (e.g. nvidia drivers) do not work in a live or persistent live drive, because the driver is selected by the kernel before the overlay for persistence is activated. "
Yes, I've seen that. 
But I can check which version of the drivers get selected or proposed in the driver list. And check the known issues or functionality before committing to the new version. And I taulk about the Nvidia cards but there are the Realtek Ethernet cards and the WiFi also. And I don't talk about ACPI issues.... 
I can check if the previous fixes are going to play the part or not. 
Have a nice day wherever you are !

---

### Post by sudodus on 2020-04-22
Good luck with your testing and checking for known issues before committing to the new version, and  please share your results here after your tests. 

It is morning now, and I'm fine here in Sweden. I wish that you stay safe and that you have a nice day :-)

---

