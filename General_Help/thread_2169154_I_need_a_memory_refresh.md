---
title: "I need a memory refresh"
date: 2013-08-20
forum: General Help
---

### Post by Quackers on 2013-08-20
I'm running Ubuntu 13-04 on a macbook pro with retina.
The Ubuntu install is new and seems to be using the Gallium graphics driver.
My laptop has a discreet graphics card and a Nvidia GT650 (I think it is).
I assume the system is using the discreet graphics card (as I'm not sure graphics switching is possible) but how can I confirm which graphics card is being used currently?
Thanks (it seems I've forgotten too much).

---

### Post by papibe on 2013-08-20
Hi Quackers. Welcome back ):P

To see if you have switchable graphics run this command:
```
lspci -nnk | grep -iA2 vga
```
If you see both the Nvidia card and the Intel integrated graphics, you do.

AFAIK, 13.04's nvidia-current does not support switchable graphics, so you may need to to use [Bumblebee]("https://wiki.ubuntu.com/Bumblebee") (or look for selecting options in the BIOS like some Lenovo laptops do).

Nvidia has declared that Optimus support is [coming]("http://www.phoronix.com/scan.php?page=news_item&px=MTM0NzE"), but I think you would have to install it from their website which it may be a good short time solution, but it does not go well with kernel updates.

Does that help?
Regards.

---

### Post by Quackers on 2013-08-20
Thanks papibe - I definitely have switchable graphics as it's a 15 inch retina. Output from message below

md@md-MacBookPro:~$ lspci -nnk | grep -iA2 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
	Subsystem: Apple Inc. Device [106b:00f7]
	Kernel driver in use: i915
--
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK107M [GeForce GT 650M Mac Edition] [10de:0fd5] (rev a1)
	Subsystem: Apple Inc. Device [106b:00f2]
	Kernel driver in use: nouveau

Both cards are shown but I was after confirming which is currently in use, as I'm not sure but would suspect the onboard Intel card.
As you said I don't think I can use the nvidia card at the moment but am not absolutely certain.

---

### Post by papibe on 2013-08-20
If you install Bumblebee, you could use your Nvidia card and even the proprietary driver from 'Additional Drivers' tab on 'Software and Updates'.

Regards.

---

### Post by Quackers on 2013-08-20
Thanks, that's the kind of guidance I was after.
However, I have read one or two horror stories about the nVidia drivers causing considerable problems with the retina laptops.
I'm just being careful.
Bumblebee does look like the way to go though - thanks for pointing me to it :-)

---

### Post by oldfred on 2013-08-21
This site has some info on Mac of different types with Linux. Looks like you may have issues.
[http://www.phoronix.com/scan.php?page=category&item=Computers](http://www.phoronix.com/scan.php?page=category&item=Computers)

And welcome back. :)

---

### Post by Quackers on 2013-08-21
Thanks oldfred and nice to be here too ):P
To be honest the only actual problem I'm having so far is that closing the laptop lid leads to suspending but on return the system is either unresponsive or it doesn't come back at all. I'll investigate that.
The installation wasn't as difficult as I was led to believe and all seems to be well.
This graphics thing isn't a problem as such because performance is currently good. It's just me wondering which card is being used and whether to install the nvidia driver or not.

---

