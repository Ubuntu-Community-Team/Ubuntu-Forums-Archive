---
title: "Ubuntu Randomly Freezes"
date: 2016-06-29
forum: General Help
---

### Post by Jamie_Edwards on 2016-06-29
Hi guys,

Just a quick note, the following is quite long but very detailed in information of what my predicament is and the process that has lead up to my issue. I do apologise xD

So I've been trying to install and use Ubuntu on my PC since I first got my new motherboard back in October of last year but numerous issues have arisen since.

The first issue was due to the motherboards efi not using the correct boot setting and constantly used Windows Boot Manager as apposed to GRUB. Anyway, I managed to finally figure out what I needed to do after searching forums after forums.

Now onto issue two. Issue two was that the motherboards IOMMU is deemed faulty and because of this every time I booted either from the liveUSB OR the SSD, I'd get an AMD-Vi error (and by an I mean a c**p tonne of errors) during boot.

After a while I figured out that I needed to tell grub to set itself to use "iommu=soft".

WOO! I thought, I think I've fixed the system and can now use it... Oh how I was very wrong.

I still have an existing issue with that when the monitor turns off and goes black, if I wriggle the mouse or press a key nothing happens. Not a thing. Even so, I then found out I can bypass this by just setting the screen to sleep to off and that seems to be working.

Anyway! Now the most current and perhaps the most frustrating issue to date... Ubuntu freezes. OK fair enough, all operating systems freeze every now and then but this is different. It's almost completely random. After about 10-20 mins Ubuntu just seems to not like me anymore does two things

1) Stops accessing the SSD AND HDD. Of course, this is a guess as I cannot actually tell but the "HDD Access" LED stops blinking.
2) No matter what I do, wriggle the mouse, press keys... Ubuntu doesn't respond. 

I've even tried doing that pressing ALT+PRINT SCREEN and then pressing REISUB... Guess what? Does nothing.

What on Earth is going on?!?!?!

As you have guessed, this is highly disruptive and highly frustrating! I want to be able to develop applications with Ubuntu, not mucking around with it trying to get it working.

Which is why I'm asking for you guys help. Does anyone know what is happening and more importantly, how to fix it?

System Information:
Motherboard:        MSI 970 Gaming Mainboard
CPU:                   AMD FX-4300 Black Edition Quad-Core
GPU:                   EVGA nVidia 550ti
RAM:                   G.Skill Sniper Series 8Gb (2x4GB)
SSD:                   Kingston HyperX 250GB SSD
HDD:                   Western Digital Caviar 500GB

Hope all that helps and any information you need just say and give me the commands and I'll provide it!

Thanks!

---

### Post by HermanAB on 2016-06-29
Since the motherboard was hardly used and is likely OK, I would put an oscilloscope on the power supply and see if it is stable.  If you don't have access to a scope, swap the PSU with one from your junk box or another computer and see.

Another thing to try, is to install Windows or PCBSD on the machine and see if that also freezes.

---

### Post by Jamie_Edwards on 2016-06-29
I wouldn't have thought it would be the PC as it's a Corsair CX430M.

Also, I've already got Windows on here as I already said in the first part of the thread I had trouble with the motherboards EFI which would boot Windows Boot Manager as apposed to GRUB. Windows 10 runs a treat though.

---

### Post by kansasnoob on 2016-06-29
Do you have the nVidia proprietary driver installed?

You can check by opening the Additional Drivers UI.

---

### Post by Jamie_Edwards on 2016-06-30
yeah I do.

---

### Post by kansasnoob on 2016-06-30
**Before beginning be sure you understand how to install ppas and use ppa-purge!**

**Ask any questions before beginning!** Since I don't have that exact GPU I can only guess, but I have had good luck with the nvidia PPA below :)

Now, if [this]("http://www.ubuntumaniac.com/2015/11/install-nvidia-linux-display-driver_22.html") is right you need the 358.16 driver which doesn't appear to be available in the standard Ubuntu repos. But I recommend that you NOT use the instructions there because that driver is also available in this ppa:

[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa?field.series_filter=xenial](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa?field.series_filter=xenial)

**But first of all do some more research using nvidias own tool**:

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

**Please take time to read and study before jumping in head first!**

I suspect you'll want to switch back to the nouveau driver before beginning but that's just my poorly educated guess.

---

### Post by Jamie_Edwards on 2016-07-05
So I tried that and installed the most recent version on the ppa and it's still crashing randomly :L

---

### Post by Jamie_Edwards on 2016-07-08
So I switched to Linux Mint 18 and the random freezing became less frequent, but they still happened so I scoured the internet again and found the following command I could try using:

```

amd_iommu=on

```

I entered that into GRUB at about 8:30PM and it was all hunky dory until exactly 10:00PM, this is when Mint froze.

I have no idea what could be happening.

My IOMMU is enabled at 64MB

---

### Post by Jamie_Edwards on 2016-07-09
Anyone got any ideas at all?????

---

### Post by banceu_sergiu_ione on 2016-07-09
I had counter an interference between Windows power safe setup and Ubuntu when I had windows installed too. This is not data prof supported.
But what I had notice is that windows power safe setup was somehow active while I was booting on Ubuntu and same time my pc was going in sleep/suspend while use Ubuntu even if my setup power safe in Ubuntu was disabled ( i mean never go in suspend or sleep or hibernation ... )

What i did was to set the windows power setup to never go suspend/sleep and had put off the fast boot option on windows. Also on windows i know that there is an option do turn off the disk after a time not use to save power, check it and disable.
You can try to set off all the power saver in windows and see if this still happen. Might not resolve your issues but not much to change and its all reversible
You can also try and see if, in UEFI you got the set of disk as save power .. I suggest you put it max performance.  I say this as you said that your disk look to turn off at certain point.

---

