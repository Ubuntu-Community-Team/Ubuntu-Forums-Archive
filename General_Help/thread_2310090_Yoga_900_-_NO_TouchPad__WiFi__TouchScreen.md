---
title: "Yoga 900 - NO TouchPad / WiFi / TouchScreen"
date: 2016-01-16
forum: General Help
---

### Post by green6 on 2016-01-16
Hi .

I would be appreciated for help.

After installation Ubuntu on Lenovo Yoga 900  TouchPad / WiFi and TouchScreen doesn't work.

I tried to install Kernel - linux-4.4.tar.xz and still no results .

6pack of beer for solution :)

Thank you

---

### Post by Bucky Ball on 2016-01-16
*Thread moved to **General Help**.*

We are all volunteers here. No beer required or necessary for support. 

Doughnuts, on the other hand ... :)

What did you install from, disk or USB, and how did you create the install media?
 Which release are you using? 
You say you tried to install another kernel from a tar.xz file. How and any particular reason for trying? 
Do you know that installing the 4.4 kernel worked and you are booting into that kernel? 
How did you install the kernel if you have no access to touchscreen, wifi, trackpad? Can we presume your keyboard IS working?

PS: Check out the second, pink link in my signature below. Might give you some tips for future posting/problem solving. Good luck.

---

### Post by green6 on 2016-01-16
Doughnuts then! :)

Thanks Bucky Ball for quick reply.

Before on other laptop I was using 14.04 and worked fine but on lenovo doesn't work TouchPad(I'm using USB mouse) , WiFi , TouchScreen(that is not big deal)

So I downloaded version 15.10 and Kali linux and it's this same story.

I tried to find solution and here([https://bbs.archlinux.org/viewtopic.php?id=204355](https://bbs.archlinux.org/viewtopic.php?id=204355)) some people manage to fix it using patch kernel.4.4([https://www.kernel.org/](https://www.kernel.org/))

Maybe I'm doing something wrong .

I tried as well that([https://allanbogh.com/2015/12/23/installing-ubuntu-16-04-daily-on-a-lenovo-yoga-900/](https://allanbogh.com/2015/12/23/installing-ubuntu-16-04-daily-on-a-lenovo-yoga-900/))  and doesn't work

---

### Post by Girya on 2016-01-20
I just got the touchpad touchscreen and wireless working on my Yoga 900. I found a thread in the i2c kernel message board started by Kevin Frenni. One of the members on the board suggested inserting this line ```
dev->sda_hold_time = 30;
```in the file linux-4.4/drivers/i2c/busses/i2c-designware-platdrv.c after this section of code:


	 *```
 Try to get SDA hold time and *CNT values from an ACPI method if
	 * it exists for both supported speed modes.
	 */
	dw_i2c_acpi_params(pdev, "SSCN", &dev->ss_hcnt, &dev->ss_lcnt, NULL);
	dw_i2c_acpi_params(pdev, "FMCN", &dev->fs_hcnt, &dev->fs_lcnt,
			   &dev->sda_hold_time);
```
I compiled, installed the kernel, rebooted and Touchscreen, Touchpad and wireless all worked. :D

A nice bonus was the boot time was much faster. 

Good Luck, Kevin

---

### Post by philip33 on 2016-02-04
Upgrade to kernel 4.5 rc2 and everything will work fine!

---

### Post by Bucky Ball on 2016-02-04
> **philip33 said:**
> Upgrade to kernel 4.5 rc2 and everything will work fine!

Fairly random and doesn't input much. Like to elaborate? Can you substantiate this (perhaps because this has worked for you on a Yoga 900)?

---

