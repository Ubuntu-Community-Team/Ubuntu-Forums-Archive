---
title: "Asus Zenbook Duo (Second Screen Not Working)"
date: 2024-02-19
forum: General Help
---

### Post by Maheriano on 2024-02-19
I just picked up this laptop yesterday, it's the one with a screen under the keyboard:
[https://www.asus.com/ca-en/laptops/for-home/zenbook/asus-zenbook-duo-2024-ux8406/](https://www.asus.com/ca-en/laptops/for-home/zenbook/asus-zenbook-duo-2024-ux8406/)

I have a few problems with it after installing Ubuntu 23.10 and I was hoping to get some help here:
[LIST=1]
[*]the second screen does not work
[*]the Fn key does not work (F keys do the same with / without pressing it)
[*]as a result of (2) above, I cannot toggle keyboard backlight, volume, screen brightness.......
[*]the keyboard will work docked and wired (undocked) but will not work wirelessly
[/LIST]

I have updated the BIOS and didn't see any changes in there. I've disabled Secure Boot.
I'm sorry I am not posting any command line output but I really don't know what I should be typing in to give you. If you post commands, I'll try them. Thanks.

---

### Post by Maheriano on 2024-02-19
I have fixed number 4, I didn't realize the keyboard has a power switch and I just had to turn it on and then pair the keyboard via Bluetooth. It works wirelessly now but the rest of the problems still exist.

---

### Post by Maheriano on 2024-02-19
I think I actually have fixed all of it now. I realized audio also was not working initially so I following this to install Mainline:
[https://phoenixnap.com/kb/how-to-update-kernel-ubuntu](https://phoenixnap.com/kb/how-to-update-kernel-ubuntu)
I installed kernel 6.7, rebooted and everything just worked. Audio works and the second screen under the keyboard works. This is amazing.

---

### Post by miki150 on 2024-02-21
Does the bottom screen automatically turn on and off when you remove the keyboard? Does the keyboard automatically switch between Bluetooth and wired?

I want to buy this laptop and use it with Ubuntu, so please post updates if anything new pops up.

---

### Post by Maheriano on 2024-02-22
> **miki150 said:**
> Does the bottom screen automatically turn on and off when you remove the keyboard? Does the keyboard automatically switch between Bluetooth and wired?

I want to buy this laptop and use it with Ubuntu, so please post updates if anything new pops up.

I've tried peeking under the keyboard and it does seem like the screen stays on all the time, I don't believe it turns off. There is a key on the keyboard showing an X on the bottom screen but when I press it, nothing happens. However, I've been using both screens while watching television for the last 4 hours or more and I still have more than half battery which is crazy.

The keyboard does automatically switch, when I remove it from the machine, it works wirelessly almost immediately without any manual intervention. However, for some reason airplane mode automatically turns on every time you attach or remove the keyboard and I have no idea why. I have to keep using the touch screen to turn airplane mode off so that I can use the keyboard wirelessly. I will eventually look into this but it doesn't annoy me enough yet to look into.

The backlight on the keyboard also doesn't work yet but there are some newer kernels available, I just haven't tried them yet. I went as recent as 6.7 and stopped there. There were some 6.7.X which I have not yet tried. This is something else I need to look into soon because I currently have the light on in my living room so I can see the keyboard and it's a bit annoying.

One other thing I've noticed is touching the lower screen controls the top screen, the touchscreen controller doesn't seem to differentiate between screens. I have seen there's a driver fix for this already but I really don't care about this so I haven't gone looking for it. I try not to put my greasy fingers on my screen if I can avoid it.

And lastly, the "disable touchpad while typing" option doesn't seem to work at all. I constantly graze the touchpad while typing and I'll find myself typing in some other box on the screen and I have to keep correcting it. I've done it 3 times typing this message.

I previously bought the MSI Stealth and returned it because I hated it. I bought this one right after that and wasn't quite sure about it but I think I'm going to keep this one. I'm very particular about laptops and this one is pretty great. I also don't dual boot with Windows, I'm Ubuntu only so this one had to work properly and now I think it does with the updated kernel. I went so hardcore trying to buy one that I actually have a second one being shipped which I wasn't able to cancel in time but I'll just return that one for a refund since I found this one in store. I recommend this if you can find one, they seem to be sold out everywhere or backordered to March.

---

### Post by tomas.splatch on 2024-04-01
Perhaps you've already seen this, but check also the scripts in the linked GitHub repository:
[https://discourse.nixos.org/t/asus-zenbook-duo-2024-ux8406ma-nixos/39792](https://discourse.nixos.org/t/asus-zenbook-duo-2024-ux8406ma-nixos/39792)

---

### Post by xle123123 on 2024-04-12
Hi, how did you fix the issue of the bottom screen not working? I just got my laptop and the bottom screen never turns on

---

### Post by tomas.splatch on 2024-04-12
Hi, yes, I managed to get it working with these scripts on Gnome 46. [https://github.com/alesya-h/zenbook-duo-2024-ux8406ma-linux/](https://github.com/alesya-h/zenbook-duo-2024-ux8406ma-linux/)

---

### Post by adsubia on 2024-05-11
@tomas.splatch
Can you tell more about the prerequisites for these scripts regarding Ubuntu? 

Are the mutter and libwacom patches still needed to be done or have they already been integrated?
And what about this additional package gnome-monitor-config? Is this also required for Ubuntu and if yes, which commands can you recommend for this type of notebook?

---

### Post by Maheriano on 2024-09-26
Good news, it looks like the most recent 6.11 kernel release has stopped the machine going into airplane mode when the keyboard is attached / detached.

---

