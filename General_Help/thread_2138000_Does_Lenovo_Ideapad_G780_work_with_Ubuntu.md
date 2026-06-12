---
title: "Does Lenovo Ideapad G780 work with Ubuntu?"
date: 2013-04-22
forum: General Help
---

### Post by OR83 on 2013-04-22
I recently purchased a Lenovo Ideapad G780 and I want to know if there are any Linux or Ubuntu drivers for the hardware. It came pre-loaded with Windows 8 and I can't stand it. Please help.

---

### Post by ibjsb4 on 2013-04-22
Hi OR83, welcome to the forums :)

I do not own one, but got some forum hits that may intress you.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Lenovo+Ideapad+G780&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Lenovo+Ideapad+G780&sa=Search&cof=FORID:9)

---

### Post by OR83 on 2013-04-22
Thanks, I tried doing a dual-boot setup of Ubuntu and it didn't work it said some file was missing so I was unable to login to my Ubuntu boot. I guess I might have to call Lenovo and ask.

---

### Post by OR83 on 2013-04-22
looks like I'm stuck with the pre-loaded junk because they don't have any drivers for Linux. :(

---

### Post by cortman on 2013-04-22
Did you try booting a live CD first? That's usually a smart first step- that way you can see what will work/not work before you actually install. Give it a try.

---

### Post by OR83 on 2013-04-22
Yeah, I tried it with my old version of 11.10 and nothing not even with kubuntu. I guess I could keep this latop with windows 8 and have my other laptop run Ubuntu I have and extra drive for it.

---

### Post by ibjsb4 on 2013-04-22
Maybe a newer kernel would do the trick.  13.04 will be out in a few days or download beta.

[https://wiki.ubuntu.com/RaringRingtail/TechnicalOverview#Download_Ubuntu_13.04](https://wiki.ubuntu.com/RaringRingtail/TechnicalOverview#Download_Ubuntu_13.04)

---

### Post by cortman on 2013-04-22
As ibjsb4 mentioned, 11.10 is old. Try a newer version such as 13.04 or 12.10, or 12.04 LTS.
If you prefer a traditional desktop (I make that assumption based on your distaste for Win8) try Xubuntu rather than Ubuntu/Unity.

---

### Post by OR83 on 2013-04-22
Yeah I have 12.10 since it came out but I dont know why I didn't try it with the newer version.

---

### Post by OR83 on 2013-04-22
Nope doesn't work it gives me the following error message at dual-boot time The following file is missing or contains errors /Ubuntu/winboot/wubildr.mbr Status 0x000007b

---

### Post by cortman on 2013-04-22
Are you trying to boot it from Windows using Wubi? It's not supported on your UEFI laptop. You need to boot to your Ubuntu CD/DVD/USB drive at the BIOS boot menu.

---

### Post by OR83 on 2013-04-22
I have to install Wubi because when I press F12 the CD/DVD is not listed it gives me what looks to be like a WLAN driver I'm not sure what it is.

---

### Post by cortman on 2013-04-23
> **OR83 said:**
> I have to install Wubi because when I press F12 the CD/DVD is not listed it gives me what looks to be like a WLAN driver I'm not sure what it is.

F12 should give you the boot menu. You need to press this while the computer is first starting up you know- before you get to the loading Windows screen.
It may be listed as "optical drive".

---

### Post by OR83 on 2013-04-23
nope it just say EFI IPV6 and the same but for IPV4 and the Windows boot

---

### Post by OR83 on 2013-04-23
no optical drive is listed in the system it has one but it's not appearing at the boot menu just what I listed above and the BIOS

---

### Post by ibjsb4 on 2013-04-23
Just to be sure we are all on the same page.  F12 must be pressed at startup.  If you get to the boot menu, then that is too late.  The boot option for CD/DVD is located in bios.

If this is not the case, then Lenovo must have another way to boot into bios.

---

### Post by cortman on 2013-04-23
I'm probably getting a bit out of my depth as I have zero experience with UEFI/Secure boot, but according to [here]("http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/Ideapad-Z580-turn-off-Secure-Boot-State-or-change-to-legacy-bios/m-p/960115/highlight/true#M73272") you need to turn it off in the UEFI BIOS before you have the option to boot from external media.

---

### Post by axept on 2013-04-23
Isn't there another way to get to BIOS? I mean, on my Fujitsu I hit F2 when it starts... Same on my old Acer. Another one it was DEL...

---

### Post by cortman on 2013-04-23
> **axept said:**
> Isn't there another way to get to BIOS? I mean, on my Fujitsu I hit F2 when it starts... Same on my old Acer. Another one it was DEL...

If I understand correctly, UEFI != BIOS. UEFI supplants/replaces BIOS. So it's a different problem here than getting to BIOS.

---

### Post by axept on 2013-04-23
> **cortman said:**
> If I understand correctly, UEFI != BIOS. UEFI supplants/replaces BIOS. So it's a different problem here than getting to BIOS.

Ouch, okay! Thought it was similar to the BIOS menu, because mine looks like BIOS, but isn't all new PC's delivered with UEFI nowadays? Mine is new..

Anyway, if not, then I've no clue other then F12 :) Sorry..

---

### Post by OR83 on 2013-04-23
I'm going to check the BIOS if there is any if not then i don't know but I'm starting to give up maybe in 2 days when 13.04 comes out it would be a different story.

---

### Post by OR83 on 2013-04-23
perhaps if I spend $80-$100 more and get a new hard drive maybe it will work I'm thinking it would be the only other possible choice.

---

### Post by axept on 2013-04-23
Fn+F2 works on some Ideapad laptops apparently.

---

### Post by cortman on 2013-04-23
> **OR83 said:**
> perhaps if I spend $80-$100 more and get a new hard drive maybe it will work I'm thinking it would be the only other possible choice.

That won't make any difference. UEFI is on the motherboard.

---

### Post by OR83 on 2013-04-25
Problem Solved! Raring Ringtail did the trick with a 64Bit Version it is now installed on my new laptop. Thanks everyone that helped.

---

### Post by diesels on 2013-05-07
i have a g780 notebook too and ubuntu 12.10 works fine. if you know how to install it.

Installationsteps:
1. deactivate secure boot in bios, but let uefi activated.
2. make disk space free from the normal partition (i did it in win 8 )
3. boot into the bios boot manager and select the uefi usb stick, if you have it on usb stick
4. in ubuntu grub2 boot manager press "e" and in the line how written "linux" in front of, write "nomodeset" as kernelparameter
so ubuntu boots in the intaller.
5. install it
6. reboot and you must set the kernelparameter again to start in the installt ubuntu
7. on desktop install boot-repair ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) and follow the steps.

---

