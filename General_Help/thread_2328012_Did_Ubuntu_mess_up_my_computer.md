---
title: "Did Ubuntu mess up my computer?"
date: 2016-06-16
forum: General Help
---

### Post by Ramon_C on 2016-06-16
Hello guys Im sort of afraid ubuntu messed up my computer but Im not really an expert on ubuntu, let alone operating systems which is why Im looking to you guys for help. Long story short, Windows10 messed up and refuse to boot with it proper disk (which my computer did not come with) so i made ubuntu bootable from a thumb drive and installed it that way. After installation it asked to restart, which I let it do. After that, this screen pops up every time after booting up (see picture below). However whenever I boot my computer up, it will not let me see bios or choose what drive to boot from at all. Is there any way in general I can fix this problem? Before anyone asks how im making this threa if my computer is messed up, I am currently using a pretty crappy laptop :) [http://i.imgur.com/XRlHdmf.jpg](http://i.imgur.com/XRlHdmf.jpg)

---

### Post by ajgreeny on 2016-06-16
What are the specs of this lowly laptop?

Maybe it is not high-spec enough to run the unity DE of Ubuntu, which is what I assume you are running from the colour and image of the wallpaper.

---

### Post by Ramon_C on 2016-06-16
> **ajgreeny said:**
> What are the specs of this lowly laptop?

Maybe it is not high-spec enough to run the unity DE of Ubuntu, which is what I assume you are running from the colour and image of the wallpaper.

I ment that im currently using a laptop, sorry for the miscommunication. However the computer that is having troubles should me the specs required. Heres what I have on specs: 

Processor: Intel i7-6700k
Motherbord: MSI B159
Memory: 16gb (2 8gb memory modules)
Video Card: NVIDIA GTX960

Thats all I can remember off the top of my head.

---

### Post by ajgreeny on 2016-06-16
No problem with those specs, I agree.

I think, however, that you may need to make sure that you have the proprietary nvidia driver installed for that new graphic card.

Try booting with the **nomodeset** option from grub menu.  Hit "E" when the grub menu appears to edit the boot for this single boot and using the cursor keys go to the line for the kernel where "quiet splash" is seen and replace those two words with **nomodeset** or just add it after them, then hit Ctrl+X or F10 to boot.

With luck that will give you a GUI that is usable and allow you to "Additional Drivers" and install the recommended one for that new card.

---

### Post by Ramon_C on 2016-06-16
I just tried that but it would not let me open up anything. On my computer f11 is to get to bios, and delete to get to boot menu. It would not let me open either of them up. Any other suggestions?

---

### Post by grahammechanical on 2016-06-16
That image that you posted shows the default Ubuntu desktop background wallpaper. Although it does look like it has been flipped from left to right. I have to ask some questions.

When you installed Ubuntu did you select for automatic login? By not having automatic login we get a log in screen with the same default background. But with automatic login the log in screen is by-passed. So, it could be that you are getting to a Ubuntu desktop without the Unity top panel and the launcher on the left side of the screen. It is important to work out how far in the loading process Ubuntu is getting.

If that is the Ubuntu desktop wallpaper you can try right clicking the wallpaper. Does that bring up a menu? If so, you can select Change Desktop Background. Doing that will open System Settings at the Appearance section. But from there you can get to System Settings>Software & Updates>Additional Drivers tab. You need to be connected to the Internet and to allow time for the utility to find the drivers. Then you can change video drivers. You might try the open source video driver first.

You do not tell us what version of Ubuntu you are using. If it is not 16.04 it could be that the OS does not have a proprietary video driver for that video adapter. It all depends on the versions of the proprietary video drivers being offered by Additional Drivers.

Regards.

P.S. If Ubuntu is the only OS we do not see the Grub boot menu. We have to press Shift to bring up the Grub boot menu. Then we can edit the boot parameters and add the nomodeset option.

---

### Post by banceu_sergiu_ione on 2016-06-17
That definitely looks to be 16.04 Ubuntu with Display rotation of 180 and it may also have a not fit resolution set.

I would try also as grahammechanical said but not at all, i would try 1st  right click on desktop - change desktop background -  all settings - displays > 

1st - rotation to normal or see how windows pop up and if need any rotation
2nd - marge displays if you run more then 1 display
3rd - chose the best resolution for your display in mode to can see the Launcher bar ( if your Launcher is not on auto-hide > check: behavior in appearance )

Otherwise you might had got a bad install of OS . Try reinstall and if you get same error, get an older version and see if run better.

---

