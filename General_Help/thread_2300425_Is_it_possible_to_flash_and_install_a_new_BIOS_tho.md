---
title: "Is it possible to flash and install a new BIOS though Ubuntu?"
date: 2015-10-25
forum: General Help
---

### Post by EternallyAries on 2015-10-25
Hello everyone, I'm sorry if I posted this in the wrong section, but this is quite critical and I could really use some help!

A few days ago, I've decided to try out a modded BIOS install designed for Gateway NV55S model to get access to the advance menu. After installing it, my Windows will not boot at all. Causing a huge head ache to reflashing the BIOS again back to it's original form.

Luckly, I was able to boot and install Ubuntu on this modded BIOS. Letting me have a GUI interface to work with.

Either way, I can get my hands on the Gateway BIOS for my laptop, for both Windows and DOS. I've booted up FreeDOS and tried flashing the BIOS though that. But every time I tried flashing the BIOS, it kept giving me an error saying (Missing FADT!) In which, I have no idea what kind of error that is. Leaving me at a complete lost of what on earth can I do to repair this. Because my modded BIOS effected both my wireless card, (Had to connect though a Ethernet port to write this) and it pretty much disable my battery indicator for Ubuntu. There is other issues, but they ain't as bad as the fact I can't boot windows nor connect to a router wireless.

I am running out of ideas on how to flash the BIOS with this computer. I am hoping maybe there is some way to flash it though Ubuntu? It would be amazing if I can get it to be flashed though this Linux distribution.

Either way, I am gonna leave the official Gateway BIOS download in a link, just in case if anyone wants to have a look at it for me. (Includes both Windows and DOS Files)

[URL="http://global-download.gateway.com/GDFiles/BIOS/BIOS/BIOS_Gateway_1.07_A_A.zip?acerid=634883834000227449&Step1=NOTEBOOK&Step2=NV%20SERIES&Step3=NV55S&OS=ALL&LC=en&BC=GATEWAY&SC=PA_6G"]http://global-download.gateway.com/GDFiles/BIOS/BIOS/BIOS_Gateway_1.07_A_A.zip?acerid=634883834000227449&Step1=NOTEBOOK&Step2=NV%20SERIES&Step3=NV55S&OS=ALL&LC=en&BC=GATEWAY&SC=PA_6G
[/URL]
My original BIOS version is 1.07

Laptop is a Gateway NV55S

Also I should note that I'm pretty new to Ubuntu, (Known about for years) But never really got time to learn it from the inside out. So if there is a way to flash the BIOS, I'd be happy if you can Write out a guide on how to get it done properly. (Not really experience with the Terminal)

Thank you for reading and hopefully will have the answer for me!

---

### Post by Vladlenin5000 on 2015-10-26
No, there isn't. Some vendors like Gateway require Windows/DOS to flash the BIOS because they package it that way.
A BIOS update should be OS agnostic / OS independent -and- should be done in the BIOS setup itself and not through an OS.

That said, I suppose you noticed the 2 folders - DOS and Windows - in your downloaded file. It should be enough to make a bootable FreeDOS, add the DOS folder and from there run the script "update.BAT" or just run the flashing tool itself and follow instructions by selecting the pertinent ROM also in that DOS folder. If this is what you did when you noticed the error message then you should contact Gateway.

PS - It isn't the wrong section but the wrong forum altogether. 
Windows is very sensitive to hardware changes, including BIOS version update, and particularly picky with those "modded" ones. However, it's always a matter of using a recovery media or, worst case scenario, just reinstall it. Why are you messing with Ubuntu?

---

### Post by EternallyAries on 2015-10-26
Hello Vlad and thanks for the response. I've tried out both files label .FD and .ROM within the folder inside FreeDOS. Both oddly kept giving me "Missing FADT" which is an odd error in itself which I believe could be at fault with the BIOS.

I'll be giving Gateway a call as soon as possible to hopefully find out what my options are to repairing the BIOS itself.

Also I'm using Ubuntu due to the fact it was one of my few Linux Distributions laying around at the time. It's also one of my all time favorite haha, oddly enough about Windows itself, it seems to be not bootable at all. Even using a DVD to boot up a version of Windows gives me some sort of error message that kicks me into the boot option screen. So to save any hassle from losing anything from my windows HDD, I've replaced the HDD with a new one and put the old one in a air block baggy to keep it safe till I can solve this issue out.

If anyone got any suggestions for flashing the BIOS in any other possible way, I'd like to know about it and give it a shot if at all possible. It be very helpful.

Edit: I've gave a call to Gateway Technical support, and after talking to them about my problem, the guy told me that I would have to pay $99.99 dollars to get a tech guy to help with my BIOS problem. I can't believe this to be honest that's expensive haha. Either way, I guess I'll have to come up with some possible way to get the BIOS flashed though FreeDOS.

---

### Post by Vladlenin5000 on 2015-10-26
[http://www.chtaube.eu/computers/freedos/bootable-usb/#why-freedos](http://www.chtaube.eu/computers/freedos/bootable-usb/#why-freedos)

^^^
This always worked for me. And [this]("http://www.chtaube.eu/computers/freedos/bootable-usb/#advices-for-doing-a-bios-or-firmware-upgrade") advice is spot on.

---

### Post by coldraven on 2015-10-26
> **Vladlenin5000 said:**
> [http://www.chtaube.eu/computers/freedos/bootable-usb/#why-freedos](http://www.chtaube.eu/computers/freedos/bootable-usb/#why-freedos)

^^^
This always worked for me. And [this]("http://www.chtaube.eu/computers/freedos/bootable-usb/#advices-for-doing-a-bios-or-firmware-upgrade") advice is spot on.

I wish that I had read that before I bricked my HP laptop trying to update the BIOS with a FreeDos USB stick. It crashed halfway through :(
Formally* my advice would have been to use Windows to update the BIOS **before **deleting it in favour of Ubuntu.

Edit: *that should be formerly

---

### Post by sammiev on 2015-10-26
> **Vladlenin5000 said:**
> [http://www.chtaube.eu/computers/freedos/bootable-usb/#why-freedos](http://www.chtaube.eu/computers/freedos/bootable-usb/#why-freedos)

^^^
This always worked for me. And [this]("http://www.chtaube.eu/computers/freedos/bootable-usb/#advices-for-doing-a-bios-or-firmware-upgrade") advice is spot on.

+1 @ Vladlenin5000

I have used this method twice in the last year with no issues.

---

### Post by Vladlenin5000 on 2015-10-26
> **coldraven said:**
> Formally my advice would have been to use Windows to update the BIOS **before **deleting it in favour of Ubuntu.

Agreed but even better is to avoid this kind of devices altogether anbd always prefer manufactorers/assemblers that do it right. Yes, the old "vote with your dollars" thing... Of course, our "lobbying power" is akin to the one of an European trotskyst  party but things will change someday somehow...

---

### Post by EternallyAries on 2015-10-27
I actually could not figure out how to get the .image file to be bootable for me. I am truly not entirely great with the terminal as of yet haha. Any advice on how to get the image working? I did get FreeDOS working on a bootable DVD though, so I'm not entirely sure what different about the USB version. But if it can remove the FADT error I'm getting, I'm all for getting the USB device bootable for DOS!

---

### Post by Vladlenin5000 on 2015-10-27
The page I posted earlier has easy to follow instructions. Just download and extract. The extracted *.img file is all you need. then do

```
dd if=[COLOR=#008000]FreeDOS-1.1-memstick-2-256MB.img[/COLOR] of=[COLOR=#0000ff]/dev/sdz[/COLOR] bs=512k (example)
```

Replace [COLOR=#008000]green[/COLOR] with the actual name of the file you extracted and [COLOR=#0000ff]blue[/COLOR] with the actual name of the of the destination USB Flash drive. Tip: Insert the USB Flash Drive then open the Disks app/tool, click on the drive and you'll see the *Device */dev/sd...
*** Be extremely careful and triple check the output device name. ****
The dd command has the nickname of "disk destroyer" for a reason: No confirmation dialog and everything in the output drive will be lost and replaced by the input image contents.

---

### Post by EternallyAries on 2015-10-28
Thank you for explaining on how to get FreeDOS to boot from the USB flash drive. It works wonders now! Sadly I still get the "FADT" error and I have no clue on how to repair this. Flashit.exe does have two working commands though after going though them on my keyboard.

Both /z and /x gives off a list of commands after typing "Flashit.exe /z or /x" But the question is, none of the commands work at all. Some state that there is no such command while other state the same "FADT" error. I'm at a complete lost to as what on earth can I do to get Flashit.exe to flash my BIOS. At least now I got an easy access USB flash device to add any missing files if required. Maybe someone here can enlighten me on some ideas to get pass this brick wall of mine?

---

### Post by Vladlenin5000 on 2015-10-28
Most likely it's something related with the BIOS you tried before in which case the expected result is the same irrespective of the media used.
Flashing a wrong BIOS often bricks the system. In that case not even the $99.99 engineer would be able to correct it without replacing the chip (unlikely) or the whole motherboard.

---

### Post by buzzingrobot on 2015-10-28
Fedora 23 will debut the capability of updating firmware. This page ([https://beta-lvfs.rhcloud.com/](https://beta-lvfs.rhcloud.com/)) is apparently the core of it.  Since it's a Red Hat project, they might get some vendors on board, eventually.  

Sorely needed in Linux, but will need to acquire a foolproof reputation before users risk their hardware with it.

---

### Post by mdurham on 2015-10-28
Just a guess, could it be that the software won't allow an earlier bios to be installed? FATD Found Advance Date Time ????? Total guess though.

---

### Post by LostFarmer on 2015-10-28
On my ASUS x401a1 laptop, i replaced the bios  (ebay $30) due to the bios program bricking itself.  Used the firmware to change efi boot option and afterward would not post.  It now works just fine running Win8.1,Win10 with Mint.  The embedded Win key is missing.  First hand , the bios chip can sometimes be replace with success.

---

### Post by EternallyAries on 2015-10-29
Well after a couple of hours trying to flash it though DOS, I can safely say it is near impossible to flash this poor laptop. (At least to my DOS experience level) The FADT error is very undocumented from my researches though and from what I seen, Not very many has had this error before.

But from what Vlad had mention, it could indeed be the BIOS itself. It's a very big possibility that the BIOS I've installed does not include any ACPI table information within it. Causing the reason why not a single version of Windows will boot up. (Not entirely sure if Windows 2000 or lower had the usage for ACPI) I should also note that any Linux Distribution I start up (Like Gparted or Fedora along with Ubuntu) that on every boot up that it says an error something like this "Can't load ACPI tables" sadly, I would need to take a recorder to read it due to how fast it flashes off the screen.

I could very well replace the motherboard myself (Since the BIOS chip is integrated into the motherboard itself) from buying a used but working one on Ebay or so. Found one with a low price around $40.50 dollars.

[http://www.ebay.com/itm/Gateway-NV55S-AMD-Motherboard-NV55S15u-NV55S02u-NV55S13u-NV55S17u-P5WS5-LA-6973P-/131639072652?hash=item1ea64cd78c:g:m2wAAOSwo0JWMBtD](http://www.ebay.com/itm/Gateway-NV55S-AMD-Motherboard-NV55S15u-NV55S02u-NV55S13u-NV55S17u-P5WS5-LA-6973P-/131639072652?hash=item1ea64cd78c:g:m2wAAOSwo0JWMBtD)

It's a great price to get an extra fan whenever the current one inside my main gateway laptop breaks down. By replacing the motherboard I should be able to boot back into Windows again with no problem.

[Off topic]

I do must say though, if replacing the motherboard manages to fix the issue, I might still stick with Ubuntu as a dualboot option, been having a blast messing with the operation system and personally liking it a bit more over Windows itself. Plus learning the terminal a lot as well, so it's really becoming fun and easy to get into this.

[On topic + Side note]

I should also mention something that I noticed on the bottom of my gateway laptop sticker, it has the words "Acer Group" Which is odd, did not expect to see Acer having any relationship to Gateway, but you learn something new every day. Either way if anyone here got any information about replacing a motherboard and any brick walls I could possibly run into, I'd like to know before ordering it.

Also about Fedora flashing the BIOS, that's quite nice to have the option to flash the BIOS though Fedora itself. I'm personally a fan of the Fedora OS operation system, so I honestly can't wait to have such option within the operation system.

---

### Post by mdurham on 2015-10-29
I found a reference to FADT here: [https://www.freebsd.org/doc/handbook/acpi-overview.html]("https://www.freebsd.org/doc/handbook/acpi-overview.html")

---

### Post by EternallyAries on 2015-10-30
> **mdurham said:**
> I found a reference to FADT here: [https://www.freebsd.org/doc/handbook/acpi-overview.html](https://www.freebsd.org/doc/handbook/acpi-overview.html)

Thanks for the link mdurham! Yeah many of my problems came from the ACPI, like missing battery icon, using only a single core of my laptop. and many other issues.

Luckily, I must inform everyone who posted here. I was able to flash my BIOS successfully. In a very VERY dangerous route.

From how I did it though, well after putting myself in the mind set of buying a new motherboard to replace the BIOS itself. I decided to try out the one flash program that did not support laptops at all. Which the name is Flashrom. The link to it is here,

[http://flashrom.org/Flashrom](http://flashrom.org/Flashrom)

Quite the nifty program if you ask me though, I would recommend not a single soul to do this on a laptop. But since I was gonna replace the motherboard itself, I decided to take a crack at it.

I was able to use my .ROM file from the DOS folder to flash it though Flashrom. Even though with all the warnings I've gotten from the program. I actually laugh when I was force to enter this one interesting command to allow me to flash my BIOS.

```
**flashrom -p internal:laptop=force_I_want_a_brick**
```

Either way, I was able to flash my BIOS successfully And I was very happy that Flashrom went well without a hitch. I guess my Gateway NV55S laptop can be consider supported with Flashrom.

But yeah, this was consider a last ditch effort and I would not recommend anyone to flash the BIOS on a laptop with this program. If you have other options to flash a laptop BIOS though other means, (Unlike me) then give it a shot and hope for the best.

Thank you all for those who has posted here and offered me your assistants. I am very happy I was able to solve my issue, and now I can continue with my day to day task again.

---

