---
title: "Dual Booters - Heed My Words..."
date: 2024-11-13
forum: General Help
---

### Post by Shibblet on 2024-11-13
I have been a "Dual-Booter" for many years now... I started with Ubuntu 8.04 and WUBI (look it up.)

Now, I feel like an old pro when it comes to installing Linux alongside Windows.

So, I bring you the first step in everything you should do before you attempt to install Linux and dual-boot.

Macrium Reflect Free: [https://www.majorgeeks.com/files/details/macrium_reflect_free_edition.html]("https://www.majorgeeks.com/files/details/macrium_reflect_free_edition.html")

This is the last "free" edition of Macrium Reflect.  Macrium Reflect is a drive imaging program that you can use to make an image of your hard drive.

[LIST=1]
[*]Install this program on Windows.
[*]Use it to make a "boot USB"
[*]Boot from the USB into Macrium Reflect "Restore" Program
[*]Back up your Windows hard drive to a safe location.
[/LIST]

Now, you may be thinking "Duh... of course we should make a back-up of our hard drive before we try installing a secondary OS.  And you'd be right.  But the reason I use Macrium Reflect, is because if there are any issues, you can boot from the USB you created, and be back to your usable Windows desktop in (usually) under 5 minutes.  (Time/speed depending on if you have an SSD or HDD...)

One of the things you can end up playing "fast-and-loose" with is the boot partition (EFI) of your hard drive.  Windows has an EFI partition, and so does Linux, in general.  Most of the time you can install your Linux /boot/efi partition, in it's own partition... but you need to be really careful during your Linux installtion, to either choose or create that partition.  

So... making sure you have a good drive image that you can restore from can save the day!  Linux, in all intents and purposes, is a consistent learning experience.  You will always be learning.  This is a great way of keeping your problems to a minimum, and restorations as short (as in time spent) as possible.

---

