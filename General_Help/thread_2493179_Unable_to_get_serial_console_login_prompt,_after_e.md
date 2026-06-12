---
title: "Unable to get serial console login prompt, after enabling serial console parameters"
date: 2023-12-06
forum: General Help
---

### Post by appusony on 2023-12-06
Dear All,

Some help please here. earlier was working in embedded linux, now that I switched to x86, BIOS based linux.

Now that I am using x86, BIOS based Linux. I am trying to or wanting to get serial console login prompt, I am getting kernel logs - but I am not getting serial login prompt with "GRUB_CMDLINE_LINUX="console=tty0 console=ttyS0,115200n8, ignore_loglevel” -> this is in Ubuntu 22.04, I am using custom Linux kernel & the kernel version is 6.1.49, after this I am not getting serial console login prompt & neither even GUI console login also.

Whenever I am not getting either of the logins - may I know please, is there anyway to recover this please?

may I know please, is that can we get only one console login or so ie., either serial console login or GUI login in ubuntu 22.04?, but in my case, I am not getting any logins except neither serial console login or nor GUI login.

Any advises/inputs or pointers, would be highly appreciated here please.

Many many thanks in advance,

Best Wishes,

---

### Post by MAFoElffen on 2023-12-06
First...  When I am using a serial console, the first time I did that, I saw a box prompt and it did "nothing"...

I was testing cloud images, and i set them up for serial console... 

I thought for sure that something was wrong. I spent almost a whole day rebooting it and changing different things. I was getting no where. I was so frustrated, and feeling defeated.

Then I hit the <Enter> key. Could hurt right?

It took off and started working. I have to tell you I felt like a fool. Serial console will sit there, waiting for initial input before it starts displaying anything. 

I learned.

It couldn't be that simple could it?

Does it display any Grub2 boot menu at all?

---

### Post by appusony on 2023-12-07
Thank you so much for your quick replies,

I did hit the [COLOR=#000000]<Enter> key. but still I was unable to get the serial console prompt., I believe I should be able to get login prompt both on serial console & Ubuntu GUI login.

Yes I get the grub menu.

I remember , I used to make some rootfs changes in embedded platform  changing inittab adding console parameters there would get serial login prompt.

But this ubuntu x86 desktop environment, is very new to me, if any idea please , any hacky way would do, -> if any changes or serial console parameters that needs to be added in roofs of ubuntu 22.04


Many thanks in advance,

Best Wishes,
Srini


[/COLOR]

---

### Post by MAFoElffen on 2023-12-07
Is this a Live/Physical Machine or Virtual?

For physical, on of my old servers that were Legacy BIOS, there was a BIOS setting that enabled serial console. But when I enabled that, then the motherboard disabled the iGPU. On some machines, it just changed the Serial console as the primary display. Even though, any other attached Video cards still worked. I did this with older machines where I was doing debug output for traces to the serial console...

On virtual machines, even though I can set up cloud images to do either, I find that they either do one or the other, but not at the same time... Such as like trying to do a primary and secondary.

---

### Post by appusony on 2023-12-08
It's is a live/Physical machine.

Thanks a lot for your inputs, Highly appreciate for your inputs & your valuable time -  "[COLOR=#000000]there was a BIOS setting that enabled serial console. But when I enabled that, then the motherboard disabled the iGPU. On some machines, it just changed the Serial console as the primary display. " [/COLOR][COLOR=#000000]I will try this and keep you posted.'[/COLOR] [COLOR=#000000]

Best Wishes,
Srini

[/COLOR]

---

