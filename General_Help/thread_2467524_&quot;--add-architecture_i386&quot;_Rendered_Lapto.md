---
title: "&quot;--add-architecture i386&quot; Rendered Laptop Unbootable?"
date: 2021-09-29
forum: General Help
---

### Post by webmanoffesto on 2021-09-29
I'm working on an HP ProBook 450 G3 (64 bit). 
I wanted to get Wine and Sketchup running. 
In an attempt to do that (maybe unnecessarily) I ran --add-architecture i386.
Now when I boot the laptop it just goes to a text "login" and my username and pw seem to not work.
I can't even get to a boot menu which will let me use a flash drive to reinstall Ubuntu.
Can you tell me how to fix this, or at least to get to a state where I can reinstall?

---

### Post by GhX6GZMB on 2021-09-29
[https://support.hp.com/my-en/document/c05018074](https://support.hp.com/my-en/document/c05018074)

---

### Post by webmanoffesto on 2021-10-03
Okay, I get to the HP Computer Setup screen. Advanced / Boot Options.
The directions you directed me to say "Select Advanced > Boot Options > Legacy Boot Order > Legacy Boot Mode."
Does that mean I should uncheck "UEFI Boot Order" and leave "Legacy Boot Order" checked?

---

### Post by webmanoffesto on 2021-10-06
Okay I did that. Now on boot I get 
"Boot Device Not Found. 
Please install an operating system on your hard diskk. Hard Disk - (3F0)
F2 System Dignostics."

I managed to boot Ubuntu 20 off a Flash drive.

I've struggled with this laptop in the past. Yes it is Legacy boot. And the last couple of times I reinstalled, I had to do an only-one-partition reinstall, legacy boot.
I had to create an EFI system partition, which I guess had to be GPT disk. Was it flagged esp and boot? Something like that. I only do this once or twice a year and I'll have to go and see what notes I can find.

What should I do now?

---

### Post by GhX6GZMB on 2021-10-06
Well, you managed a USB boot. That's always the first/biggest hurdle and it's done. Legacy or UEFI doesn't matter. And HPs are normally easy to install.

Did you even run the installer? It's on the desktop after USB boot.

---

