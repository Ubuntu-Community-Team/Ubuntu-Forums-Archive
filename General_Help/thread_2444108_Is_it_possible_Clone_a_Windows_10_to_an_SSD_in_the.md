---
title: "Is it possible? Clone a Windows 10 to an SSD in the same machine?"
date: 2020-05-24
forum: General Help
---

### Post by makem2 on 2020-05-24
I have a laptop that came with a 1TB HD which had Windows 10 on it.  Later I installed an SSD drive in a caddy in the unused DVD bay and installed Ubuntu, my preferred OS.

I no longer need to use to use Ubuntu on that machine and want to pass it on to a relative who only uses Windows 10 and has no knowledge or want to use Linux.

It would be a waste to leave the machine set up as it is which means a slow HD running Windows 10 with a fast SSD sitting redundant. (250GB)

My solution, if it is possible would be to clone the Windows 10 to the SSD, change the boot order and boot from the SSD into Windows 10. The redundant Windows 10 on the HD could then be removed (re-partitioned) and used for data as a slave to the SSD.

I would then end up with a faster Windows 10, with plenty of storage.

Is it possible?

I know I could remove the SSD from the caddy and clone Windows 10 normally, However, removing the SSD means that grub can no longer boot Windows 10. I would have to re-enable the Windows 10 boot files which could be done but it seems a roundabout method when I already have a Windows 10 OS connected to an SSD, internally, I know, but does that really make a difference?

A later thought? What would happen to grub when the cloning takes place? Windows 10 can see the SSD and it's partitions but of course cannot access them. Could it reformat the SSD though?

---

### Post by dragonfly41 on 2020-05-25
Here are my first thoughts.
Clone Windows 10 into SSD in DVD caddy.
Create a Windows 10 Recovery flash drive as a precaution.
A Ubuntu LiveUSB will be useful in an emergency. Rufus in Windows can create one (UEFI compatible).
Now *physically unplug* the laptop HDD. In my tower PC I can just pull the cable but in a laptop the drive has to be pulled.
Does the SSD now boot up as Windows?

---

### Post by CelticWarrior on 2020-05-25
I would also strongly recommend swapping the drives.

---

### Post by SeijiSensei on 2020-05-25
I don't know if cloning will work; never tried it myself.  But you could download a [brand-new ISO image of Windows 10]("https://www.microsoft.com/en-us/software-download/windows10ISO") and install it on the SSD if you still know what your Product Key is.  (Most likely it's on a sticker on the bottom of the laptop.)  If you don't have it, boot up Windows and follow the steps here: [https://www.howtogeek.com/660517/how-to-find-your-windows-10-product-key-using-the-command-prompt/](https://www.howtogeek.com/660517/how-to-find-your-windows-10-product-key-using-the-command-prompt/)

Yes, the inheritor of the computer will lose whatever software you may have installed.  He or she will also lose access to any personal data you might have left behind.

And, yes, swap the drive cables.  If you can't do that, see if you change the order of the drives in the BIOS.

---

### Post by oldfred on 2020-05-25
If a newer UEFI system, you have product key inside the UEFI, so any install of Windows automatically uses it.

Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)
[https://support.microsoft.com/en-us/help/10749/windows-product-key](https://support.microsoft.com/en-us/help/10749/windows-product-key)

---

### Post by makem2 on 2020-05-25
Thank you all for your input and suggestions.

Since posting my relative has said she will pay for a 1TB SSD as they are less than £100. Possible little problem there to be sorted is the machine is SATA 2 and most available drives appear to be SATA 3. I read that that may be a problem but I would not be able to tell until the machine is booted from the new SSD.I am sure that can be sorted.

So, I will clone the windows to the new SSD and swap the drives. I will gain a 240GB SSD for my trouble lol.

Regarding the cloning, I have done that in the past with third party software but that was before I used Linux. I will give Linux clone software a try this time.

Once again, many thanks for your time.

---

### Post by kurt18947 on 2020-05-25
A SATA 3 drive should work without issue in a SATA 2 machine. The SSD will run at SATA 2 speed, I'd suspect it'll be faster than a mechanical drive even running at SATA 2 speeds.

---

### Post by makem2 on 2020-05-25
> **oldfred said:**
> If a newer UEFI system, you have product key inside the UEFI, so any install of Windows automatically uses it.

Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)
[https://support.microsoft.com/en-us/help/10749/windows-product-key](https://support.microsoft.com/en-us/help/10749/windows-product-key)

Thats good news. It's over 4 years old and uses UEFI

---

