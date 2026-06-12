---
title: "Deleted Menu Entries In Grub Customizer"
date: 2022-01-29
forum: General Help
---

### Post by swangnation on 2022-01-29
It's been a while since i was using Ubuntu so I'm not sure where exactly in this forum this question goes... Anyway. I have ubuntu 20.04. I went through the grub customizer, there are usually 4 entries, 2 generic and 2 recovery entries. I have always removed 2 of these as it helps my laptop to boot up quicker. As I have done in the past, I removed 2 entries and low and behold when i went to start up the laptop again, nothing would happen. It's obvious i shouldn't have deleted the entries.

How can I fix this problem?

---

### Post by Impavidus on 2022-01-29
Grub customizer again... You didn't specify which of the 4 entries you removed and I don't see how that would speed up booting.

Anyway, try [boot-repair](https://help.ubuntu.com/community/Boot-Repair). The boot info summary should give us some more details.

---

### Post by swangnation on 2022-01-30
> **Impavidus said:**
> Grub customizer again... You didn't specify which of the 4 entries you removed and I don't see how that would speed up booting.

Anyway, try [boot-repair]("https://help.ubuntu.com/community/Boot-Repair"). The boot info summary should give us some more details.


That's because I don't remember which entries i deleted. This boot repair looks interesting but I'm not sure of the correct procedure to use it. The only way i can access the hard drive is with a sata usb connector. I just plugged it in and entered the encryption password. I've added a screenshot of what is visible on the hard drive that cannot boot up. Am I to assume that I have to put the hard drive back into the laptop and then boot into the live boot repair disk?

---

### Post by ajgreeny on 2022-01-30
Unfortunately grub-customiser is fairly well known for causing more problems than it solves.

I believe it stores all the grub configuration that it replaces somewhere in the filesystem though having never used it I am not sure where, and having looked at [https://easylinuxtipsproject.blogspot.com/p/grub-customizer.html](https://easylinuxtipsproject.blogspot.com/p/grub-customizer.html)  which is worth reading I am not certain if that still happens.

I think it may be worth trying a complete purge and reinstall of grub to your system but I am completely unaware of whether or not that will get you back to where you want to be, and unfortunately removing grub-customiser does not restore the now new configuration to what it used to be. Whether a purge/reinstall of grub will do so I am not sure about either.

Keep us informed of where you get with this please; it may help other GC users who have similar problems.  Good luck!

PS:
I hope you have good,usable backups of all your files.  This is especially important as you have an encrypted filesystem and when things go wrong it could mean those files are gone for good!

---

### Post by dragonfly41 on 2022-01-30
Here I go again with suggesting rEFInd.  Emergency suggestion. I suggest using LiveUSB to install [rEFInd]("https://www.rodsbooks.com/refind/") into your partition containing grub.

It should appear in /boot/efi/EFI/refind .. alongside &#8220;ubuntu&#8221;

Reboot and select refind from menu.

If you get back into Ubuntu you can then update grub in usual way and you can then choose between usual grub or [rEFInd]("https://www.rodsbooks.com/refind/") to boot up again.

---

### Post by tea for one on 2022-01-30
Good suggestion from [COLOR="#0000FF"]dragonfly41[/COLOR], rEFInd is worth consideration.
You can even make a temporary rEFInd bootable USB Flash Drive to see if it helps.
Option 5 here [https://www.rodsbooks.com/refind/getting.html](https://www.rodsbooks.com/refind/getting.html)

@dragonfly41 - your link yields 404 Not Found

---

### Post by swangnation on 2022-02-04
I should have time today to try a few things and to also look into your suggestions. I've loaded rEFInd onto a usb drive and I believe I've place the same file in the correct area of the hard drive I'm trying to recover. I should be able to post something a little later on.

---

### Post by swangnation on 2022-02-05
hi guys, as it turned out i didn't have enough time to do much other than find out what i deleted from the grub menu and it turns out that i am missing the initrd.img-5.13.0-27-generic kernel and the corresponding recovery image.

I am assuming its a matter of downloading the kernel and copying the image to the affected hard drive?

also, since i am here i may as well ask. How do i make a bootable flash drive with rEFInd on it? I did have a quick look at the instructions but to be honest i found it a little confusing and let it go as i had little time anyway.

---

### Post by Impavidus on 2022-02-05
It's a matter of reinstalling the kernel. Your screenshot in post 3 shows some old 5.8 kernels. If you can boot one of those, that should be easy. If you can't, you need your live disk. Clean up the mess created by grub customizer, then reinstall the kernel. To do so from the live disk, boot-repair may help. Reinstalling the 5.13 kernel or recreating the entries for the 5.8 kernel would do. I can't give more details, as I don't know the details of your system.

---

### Post by dragonfly41 on 2022-02-05
To answer your question (rEFInd though might add further confusion and should be used _in parallel_ with above advice to restore grub)

[COLOR=#000000]"How do i make a bootable flash drive with rEFInd on it? "

Break that down to two questions:
[/COLOR][COLOR=#000000]How do i make a bootable flash drive?
[/COLOR][COLOR=#000000]How do I now install rEFInd on the bootable flash drive (LiveUSB)?

You should have a LiveUSB anyway lying around.
If not .. search .. I will not add links to tutorials.
Then in "Try Ubuntu" mode in Live USB install rEFInd.
Again read the rEFInd docs.

Finally with rEFInd installed in LiveUSB install rEFInd into your mashed up Ubuntu partition wherever that is on your internal drive. "[/COLOR][COLOR=#000000]Anyway. I have ubuntu 20.04.".
[/COLOR][COLOR=#000000]You can install/use Gparted in LiveUSB to inspect your internal partitions

[/COLOR]

---

### Post by swangnation on 2022-02-11
Hi guys, rEFInd hasn't actually worked although it's probably because of something i did or perhaps DIDN'T do. I have done something which might help you guys to help  me a little as my brain cells are fried from work. 

I used udisksctl to remove/unlock the pass phrase from the encrypted partition which means I can now access the data on the drive. Not sure if you guys have used it before but i ran the command

```
udisksctl unlock -b /dev/sda3
```

I then got prompted for the passphrase and entering it in, the encrypted partition was unlocked. PHEW!

Now I'm just not sure where to look for what is missing or what is needed. I'm on ubuntu 20.04

---

### Post by ActionParsnip on 2022-02-11
Why do you not have backups if your data is important?

---

### Post by swangnation on 2022-02-11
> **ActionParsnip said:**
> Why do you not have backups if your data is important?

I'm a little lazy sometimes. I really should make back ups though and I will after this error

---

### Post by swangnation on 2022-02-19
just an update guys. To my blessed relief i found one my usb sticks which contained most of the medical data i was trying to retrieve from my hd because i made a complete hash of trying to reboot the hard drive. I ended up with 2 grub configurations and neither of them could find the partition where all the data was kept. I ended up doing a fresh install. Only have 2 issues now. Cannot get out of landscape mode and trying to figure out how to make a live usb WITH my user data.

I'll close this thread off.

Not sure how to close this thread...all i can do is mark it as solved which isn't right.

---

### Post by MAFoElffen on 2022-02-19
The Thread Tools link in the upper right of the firs page of your thread... Under that, select "Solved."

---

