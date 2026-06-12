---
title: "Ubuntu 14.10 Crashing"
date: 2015-06-04
forum: General Help
---

### Post by quinlan2 on 2015-06-04
I installed Ubuntu 14.10 on my Dell Inspirion 570. The processor is an AMD Althon(tm) II X2 245 Proccesser x2 and it will be running fine and it will randomly crash with this screen
Is it a hardware problem? If so what do I need to replace? I already replaced the hard drive. And if it's a software problem how can I fix it?
[IMG]http://i288.photobucket.com/albums/ll179/nitroxko1/20150604_1048271_zpsge98ejtj.jpg[/IMG]

---

### Post by dino99 on 2015-06-04
i had the same kind of crash at boot time with one system of mine some time ago. And i found that the ram voltage set in 'auto' mode by the bios was the culprit. Since i've set it manually to the required voltage, i now can boot without such crash. Maybe you hit the same crappy (AMI) bios setting.

---

### Post by quinlan2 on 2015-06-04
I'm a bit of a newbie, how do set the manual voltage?

---

### Post by matt_symes on 2015-06-04
Hi

Does it still crash if you use a different kernel ?

Kind regards

---

### Post by quinlan2 on 2015-06-04
I'm about 50% sure its not a software problem. I've changed the hard drive before.

---

### Post by matt_symes on 2015-06-04
Hi

> **quinlan2 said:**
> I'm about 50% sure its not a software problem.

Does this mean you have no idea if it's software or hardware ? You're a bit unclear here.

Have you tried another kernel ? The software is crashing somewhere in the high resolution timer interrupt handling code.

Kind regards

---

### Post by quinlan2 on 2015-06-04
Well currently I can't boot the computer at all. Or access the BIOS.

---

### Post by matt_symes on 2015-06-04
Hi

> **quinlan2 said:**
> Well currently I can't boot the computer at all. Or access the BIOS.

As you cannot get into the BIOS, i assume it is not even POST-ing (the text displayed at the very start of the boot process if the POST text).

Are you getting any beeps from the PC ? These are called beep codes and can be used to identify an issue.

Open up the PC and re-seat all the cards including the memory.

Check all the cables are securely connected and try to boot again.

If it still will not POST then start removing the cards and unplug hard drives one by one until you have the bare minimum of cards (1 memory stick and the graphics card) and trying to boot after you remove/unplug each item.

Does it POST and can you get to the BIOS screen ?

Kind regards

---

### Post by quinlan2 on 2015-06-04
Okay I opened the PC and re-seated all the cards and unplugged and re-plugged all cables. Now I can get to the BIOS screen, what should I do now?

---

### Post by matt_symes on 2015-06-04
Hi

> **quinlan2 said:**
> Okay I opened the PC and re-seated all the cards and unplugged and re-plugged all cables. Now I can get to the BIOS screen, what should I do now?

You obviously had a hardware issue there.

Personally i would assume that was the problem and continue to use Ubuntu with the same kernel you were using before and see if you get the same kernel crash.

If no more kernel crashes then you be assume that re-seating your hardware has fixed the problem.

If you still get problems then i would try another kernel before messing with anything in the BIOS just to lessen the chance of - but not eliminate - a kernel bug.

If you still get issues then try a BIOS upgrade. After that i would start tweaking settings in the BIOS.

You may also want to raise a bug report.

Kind regards

---

### Post by HermanAB on 2015-06-05
First thing I would have done is try to boot a USB stick and see if that works or not.

---

### Post by matt_symes on 2015-06-05
Hi

> **HermanAB said:**
> First thing I would have done is try to boot a USB stick and see if that works or not.

This is a good smoke test for these types of issues as well.

Kind regards

---

### Post by mörgæs on 2015-06-05
> **matt_symes said:**
> 
You may also want to raise a bug report.

I don't think developers are going to look at a report for 14.10. I would leave this one and do a fresh install of 15.04.

---

### Post by matt_symes on 2015-06-05
> **mörgæs said:**
> I don't think developers are going to look at a report for 14.10. I would leave this one and do a fresh install of 15.04.

Maybe you're right here. 

I've been sticking to LTS releases on all the machines that i need to work for a while now because, in part, i know that bugs are more likely to be looked at.

Kind regards

---

