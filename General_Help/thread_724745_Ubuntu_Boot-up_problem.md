---
title: "Ubuntu Boot-up problem"
date: 2008-03-14
forum: General Help
---

### Post by hostmax on 2008-03-14
Hi everybody,

My computer chipset is i845G (which supports onboard VGA), but due to some manufacturer method to reduce the product price, my motherboard does not have a VGA port for the onboard graphic (in other words,I can not use my onboard graphic card) ... I have a nVidia GF4 AGP instead ... and I disabled the onboard VGA in BIOS to save shared memory !

I got an Ubuntu 7.04 CD, as I was trying to boot into it, the X Server got an error saying that I dont have any graphic card !
Next time, I came into the BIOS and re-enable the onboard graphic, the Ubuntu CD boot up and showed another error : My VGA does not have any screen !!!

As some older version of Ubuntu (6.05) the bootup process works fine, but since then, i got no luck at all!
Can you please help me on how to solve that ?

Thanks,

---

### Post by {BzF}~JOKesTER on 2008-03-14
Try Temporaily Removing The AGP Card.

The Onboard Graphics Will Automagically Come On - Now Try And Install.

Tell Me How It Goes -{If This Helps Please Hit "Thank"}:)

---

### Post by hostmax on 2008-03-14
Hmm.... didn't I mention that the onboard graphic does not really exist ?? My motherboard has no VGA port !!!! Moreover, when I tried enabling the onboard graphic, Ubuntu reported VBIOS error !!! :(

---

### Post by {BzF}~JOKesTER on 2008-03-14
> **hostmax said:**
> Hmm.... didn't I mention that the onboard graphic does not really exist ?? My motherboard has no VGA port !!!! Moreover, when I tried enabling the onboard graphic, Ubuntu reported VBIOS error !!! :(

Wiw - No I Didn't Get What You Said The First Time - Sorry.

Thats A Diffucult One....

Hmm...

Try Using Your BIOS Reset Switch - And Than Go Into The BIOS And Disable The Onboard Graphix 

Also Make Sure That An IRQ Is Not Dedicated To The Graphics Card.:)

Hope This Helps!!:)

---

### Post by hostmax on 2008-03-24
The Ubuntu 5.05 worked perfectly for my case ...... but later versions suck !

There is no use in disallocate IRQ for onboard-VGA :D

I asked my friend and he recommended ......... returning to Windows :(

---

