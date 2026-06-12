---
title: "Help flashing BIOS with flashrom"
date: 2017-07-01
forum: General Help
---

### Post by paeschli on 2017-07-01
Hey guys, here's a long story so go straight to the second paragraph for my question :p

Couple of days ago, I wanted to install Lubuntu 17.10 on an old Windows laptop I had laying around. It was the first time I tried booting Linux on a computer with UEFI on it. It didn't quite work at first and without looking for much advice online, I decided to switch over to 'Legacy BIOS' instead of UEFI. After a 'No bootable device' message on start-up, I managed to make Lubuntu boot. As I should have expected, it's very unstable, booting up takes 10 minutes, shutting it down is impossible (the Lubuntu shutdown logo stayed on my screen the whole night before I manually shut it down) and I can't get the touchpad to work. So, what if I want to get back to Windows 10? Well, the problem is I can't access the BIOS anymore, Fn+F8 that I used to access the BIOS doesn't work anymore, I tried numerous other key combinations, all without success. In other words, I can't boot anything up from USB anymore, all I get at startup is a Packard Bell image that flashes rapidly, a screen that flickers on and off for 10 seconds before a  10 minute boot-up...

So, what I would like to do now is re-flash the BIOS since that would reset to BIOS to UEFI mode. I downloaded a zip file from the manufacturers website and would like to flash it with flashrom. But what should I flash, the zip file, the exe file inside or something else?

What would my command look like, something like this?
```
flashrom -wv /path/to/bios/file
```

The laptop in question is a Packard Bell EasyNote ENTG71BM.

---

### Post by CatKiller on 2017-07-01
It would probably be the .exe file.

Before you do that, though, you might try simply resetting the BIOS to default rather than flashing it. The user manual suggests that F2 would enter the BIOS, btw. If there isn't a BIOS reset jumper (which there probably isn't given that it's a laptop) you can often achieve a similar result by removing the CMOS battery and then powering the computer on. The CMOS battery is a CR-2032, like a large watch battery.

---

### Post by Autodave on 2017-07-01
If you can get into the BIOS like CatKiller suggested, usually on the main page of it you will find an option to "restore factory default" or something similar to that. I would give that a shot first.

---

### Post by paeschli on 2017-07-02
Managed to get it to work with a long press F2 on start-up and the instructions in this video: [https://youtu.be/cVbUrzYD8PE](https://youtu.be/cVbUrzYD8PE)

For anyone who would have the same problem on a Packard Bell or Acer laptop:
- F2 to enter BIOS
- In the boot settings, make sure that Secure Boot is turned on. It should be under the Boot tab.
- Go to Security tab and look for &#8220;Select an UEFI file as trusted for executing&#8221; and click enter.
(- If it is impossible to select the category in the security tab&#65279;, set a superuser password&#65279; first)
- Select an UEFI file as trusted for executing HDD0-EF&#304;-UBUNTU-shimx64.efi
- The important one is shimx64.efi here. Select it and click enter.
- F10 SAVE and exit

---

### Post by CatKiller on 2017-07-02
Glad you got it sorted.

Don't forget to mark the thread as Solved to help other people with the same problem find a working solution.

---

