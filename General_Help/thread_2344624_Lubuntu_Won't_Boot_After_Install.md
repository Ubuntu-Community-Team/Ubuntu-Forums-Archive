---
title: "Lubuntu Won't Boot After Install"
date: 2016-11-26
forum: General Help
---

### Post by neeb2 on 2016-11-26
Hey!

I had recently installed Lubuntu 16.04 onto my Acer Aspire One 11 Cloudbook with a USB, and for some reason it won't boot up correctly. 
The entire installation went smoothly with no problems at all, but when the installation finished and I rebooted the laptop this happened (sorry for the crappy pictures):
[ATTACH=CONFIG]272414[/ATTACH]
And from there the screen would either go blank or this would come up: 
[ATTACH=CONFIG]272413[/ATTACH]
And if I select "Ubuntu*"  it would go blank as well.
At this point I really have no idea what to do. I mean the install went so smoothly and then this happens. 
Some info that might help:
-I had booted with my System Boot Mode set to "Legacy" (I tried UEFI but it had said that there was "No Bootable Media"-.)
-I had just gotten this laptop 2 days ago. 
-(Ask me for anything else)

Any help would be greatly appreciated, I really want to have Lubuntu on this laptop. Thanks!

Edit: Alright so I think the best course of action would be to either figure out how to install it in UEFI or how to boot it up in Legacy. Still have no idea how to do either...

Edit 2: Alright, so I've found this: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) , and I think this might help me get started with UEFI. I have no idea if it'll work with 64bit Lubuntu though. If anyone has any other route I can take I'd be glad to know. Or if anyone has any experience with this either. Otherwise I'll try this out tommorow and keep y'all updated. Thanks!

---

### Post by fenrice on 2016-11-26
I had problems similar to you until i turned off Secure Boot and turned CSM on. Might be worth a shot if those are options are in your bios.

[QUOTE=]Hey!

I had recently installed Lubuntu 16.04 onto my Acer Aspire One 11 Cloudbook with a USB, and for some reason it won't boot up correctly. 
The entire installation went smoothly with no problems at all, but when the installation finished and I rebooted the laptop this happened (sorry for the crappy pictures):
[ATTACH=CONFIG]272414[/ATTACH]
And from there the screen would either go blank or this would come up: 
[ATTACH=CONFIG]272413[/ATTACH]-P
And if I select "Ubuntu*"  it would go blank as well.
At this point I really have no idea what to do. I mean the install went so smoothly and then this happens. 
Some info that might help:
-I had booted with my System Boot Mode set to "Legacy" (I tried UEFI but it had said that there was "No Bootable Media"-.)
-I had just gotten this laptop 2 days ago. 
-(Ask me for anything else)

Any help would be greatly appreciated, I really want to have Lubuntu on this laptop. Thanks![/QUOTE]

---

### Post by neeb2 on 2016-11-27
> **fenrice said:**
> I had problems similar to you until i turned off Secure Boot and turned CSM on. Might be worth a shot if those are options are in your bios.
Thanks for the reply! I was able to turn Secure Boot off but there was no option for CSM or anything like that so it couldn't work. Thanks though! I tried to "Select a UEFI file as trusted for executing" but it didn't have any files. I haven't the slightest idea regarding what to do at this point.

---

