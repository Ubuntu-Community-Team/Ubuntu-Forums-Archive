---
title: "bricked laptop"
date: 2023-08-20
forum: General Help
---

### Post by Old Jimma on 2023-08-20
Hello Communty:

My laptop is bricked.

Here is what happened:
[LIST]
[*]I removed software,
[*]as a consquence, the laptop would no longer boot,
[*]I got help here with that.... but things went wrong, and
[*]my laptop is a brick now.
[*]
[/LIST]

What should I do, or try before laying it to rest in peace?

Thanks,
Old Jimma

---

### Post by dragonfly41 on 2023-08-20
I'm turning in for the day. But before you dump it try inspecting content using LiveUSB.

---

### Post by Quarkrad on 2023-08-21
If you boot up using a live USB, like dragonfly41 says, then you can test your hard drives and RAM to make sure they are OK.  There are numerous testing tools around to see to what degree, if any, your actual laptop is bricked.

---

### Post by Rubi1200 on 2023-08-21
As suggested, use a liveUSB to try Ubuntu and see if the hardware still responds.

While on the live medium, use the links in my signature to run the boot info script and the system info script.

Paste the links to the results so we can see what is going on.

Thanks.

---

### Post by MAFoElffen on 2023-08-21
+1 with the two reports. 

Bricked to me means it will not even go to the BIOS Post. Even with that, if you clear the CMOS, you can usually reset the BIOS settings to POST. Though with a laptop, to do that may take some disassembly.

I have come into quite some nice equipment, (bought as parts) when people thought they bricked their hardware or fried their mainboard, and after testing, it turned out they didn't. One of those happened to be a $10,000 enterprise server that I picked up as salvage for $20. (IT salvage is 20 cents a pound...) That eneded up being a very nice server that I used for years. Another was a Dell Precision Engineering Class Laptop... That Dell support told them had a bad motherboard, but just needed the CMOS cleared and the OS reloeaded.

You'd be surprised.

---

### Post by Old Jimma on 2023-08-21
Hello Ubuntu Forum Respondents:

Reply to MaFoElffen: I inserted the start up USB, and got the system to the boot menu. From there I  choose the USB HDD .... that's the live USB that I know works because I've tested it on several other machines. When I choos the USB HDD, it returns to the boot menu. Perhaps some background might be useful for you. Please see "Reply for Everyone Else" below.

Reply for Everyone Else: I inserted the live USB with Ubuntu 22.04 (that works. I've tested it). When I choose the USB HDD live disk, it returns to the boot menu.

Background for all: Atfer removing Proton VPN app, the laptop would  no longer boot, and I sought help on the forum here:[HTML]https://ubuntuforums.org/showthread.php?t=2489362&p=14154139#post14154139[/HTML]

If you look toward the middle of that thread, you'll see that I receive advice with specific instructions to try a boot repair and then remove some of what seemed to be duplicate entries. After I did that the laptop became a brick.

If it was bad advice... I'm ok with that. Nobody's perfect, especally me. And I harbor no ill feelings. 

I'm just trying everything I know I can to to try to unbrick the laptop.

I look forward to your advice.

BTW: I inserted the boot repair USB and that works: I've put the report at: 
[HTML]
http://paste.ubuntu/com/p/FMvNNY5TgN /
[/HTML]
From there it asks me make sure my BIOS is set up to boot USB in EFI mode. This is a Lenovo T420 laptop. I can't find any info on how to do that.

Am I bricked?

Should I use this brick for parts?

THanks,
Old

Thank you!

Old

---

### Post by #&amp;thj^% on 2023-08-21
> **Old Jimma said:**
> 
From there it asks me make sure my BIOS is set up to boot USB in EFI mode. This is a Lenovo T420 laptop. I can't find any info on how to do that.

Am I bricked?

Should I use this brick for parts?

THanks,
Old

Thank you!

Old
Bios on those old T420's can be a mess to deal with, on mine after i press the power on I start spamming the the [F2] until the Bios comes up

---

### Post by Old Jimma on 2023-08-21
Dear Ubuntu Friends:

I have disassembled the laptop and have declared it bricked.

I sure wish I knew what I did to it to make it briked!!

Old JImma

---

### Post by yancek on 2023-08-21
>  From there it asks me make sure my BIOS is set up to boot USB in EFI  mode. This is a Lenovo T420 laptop. I can't find any info on how to do  that.


Best option at that point would have been to do an online search for the manual on that specific machine.  Any computer sold within the last 8-10 years should be UEFI compatible and the settings vary with computer manufactuer. 

>  I receive advice with specific instructions to try a boot repair and then remove some of what seemed to be duplicate entries

I saw that post and wondered how you would determine which one to save and which to delete.  Did you save the most recent entry?  Did you test boot with each to see which was the correct system?

When you go into the one time Boot Options, you should see UEFI Boot Options and Legacy options and if you don't see both then it likely isn't EFI capable.  From the information you posted above though, it would seem to be.

---

### Post by #&amp;thj^% on 2023-08-21
Mine and his has
 Applicable Brands [https://pcsupport.lenovo.com/us/en/products/laptops-and-netbooks/thinkpad-t-series-laptops/thinkpad-t420/4178/solutions/ht103672-understanding-drivers-bios-uefi-and-firmware#Applicable_Brands_HT](https://pcsupport.lenovo.com/us/en/products/laptops-and-netbooks/thinkpad-t-series-laptops/thinkpad-t420/4178/solutions/ht103672-understanding-drivers-bios-uefi-and-firmware#Applicable_Brands_HT)

Lenovo Laptop, Desktops, & Tablets
Driver
BIOS and UEFI
Firmware (Mobile Phones/Tablets)
Unless your MoBo went south I'll bet it's not bricked, I had mentioned Bios on those vintage had very buggy bios.
It happened twice to me, I think sudodus will remember that one.
If all the hardware is still intact, just re flash the Bios....Mine been good for two years now it stays on 24/7 outside needed reboots from updates.

---

### Post by MAFoElffen on 2023-08-22
On my ThinkPad T520 (same generation, with a larger screen), on boot, press the Blue "ThinkVantage Button, near the Power Button. That will bring it straight into the BIOS settings.

Wait one, and I'll reboot this T520 and tell you where the BIOS mode is and what the options are. They should be the same...

EDIT --
It brings you to a menu, which says to press <F1> to enter the BIOS setup utility. From there go to Boot. on that page, in boot mode, the options are:
Both
UEFI
Legacy

Select UEFI...

For the CMOS battery on that. It's under the keyboard. If you do have that that off yet, take off the memory and hdd cover off the back, the screws for the keyboard are under those. Slide the keyboard towards the screen to unlock it. Will come up from the lower side, by the touchpad. You should see the cmos battery near the screen. unlpug it. Wait about 30 seconds. Then plug back in. Reasssemble and test. 

Attached picture shows what it looks like. See the battery in the yellow plastic? follow the wires to where it plugs into the motherboard and unplug the white plug... I have a toolkit that has plastic tools to do that, but to do onsite services, I made extras  from plastic coat hangers and from chop sticks to do that. Flat on one end, and sharpened like a pencil on the other...

Like this: [https://www.amazon.com/SANHOOII-Antistatic-Spudger-Opening-Repairing/dp/B095HDVBVB/ref=sr_1_8?keywords=spudger&qid=1692698570&sr=8-8](https://www.amazon.com/SANHOOII-Antistatic-Spudger-Opening-Repairing/dp/B095HDVBVB/ref=sr_1_8?keywords=spudger&qid=1692698570&sr=8-8)

---

