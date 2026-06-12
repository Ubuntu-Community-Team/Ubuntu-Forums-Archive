---
title: "Make windows XP in vmware suport sound and printer"
date: 2007-07-16
forum: General Help
---

### Post by chacham23 on 2007-07-16
I installed VMware on ubuntu Feisty Fawn, on it installed XP pro.

Its work great! except of there is no sound and cannot install printer.

I should mention that my computer is connected to another comp(xp) through a simple network(only  cable and two network cards). The internet dialup is installed on the xp and the printer also.
From ubuntu itself I can print but the vmware dont recognize my printer or the sound card.

hope u can help me.... :)

Thanks in advance.

---

### Post by chacham23 on 2007-07-16
someone???

---

### Post by strabes on 2007-07-16
Sorry for the non-answer but I find virtualbox to be easier than vmware. Maybe take a look at it.

---

### Post by jocko on 2007-07-16
Do you use vmware player, server or workstation?
In server (and probably also in workstation) you can add new virtual hardware by clicking "edit virtual machine settings".
Under the list of installed hardware click "add".
If you already have a virtual sound adapter installed, under "use physical sound adapter" try to type in the path to your actual sound card instead of "Auto Detect".
(this will probably be something like "/dev/audio" or "/dev/dsp")

If you have vmware player, I don't think there is any gui for adding hardware, but I think you should be able to do it manually.
In the folder where your virtual machine is, there should be a .vmx file.
Open it up using gedit or any other text editor, and add these two lines, if they are not already there:
```
sound.present = "TRUE"
sound.virtualDev = "es1371"
```

I have no idea how to add a printer, but I guess it could be done if you manage to set up a virtual network, so that you can share the printer from your host.
I'm not sure how to do this, but there should be some guide around here somewhere that may help you.
Or even someone that can point you in the right direction...

Hope you get it working!

---

### Post by chacham23 on 2007-07-16
> **jocko said:**
> Do you use vmware player, server or workstation?
In server (and probably also in workstation) you can add new virtual hardware by clicking "edit virtual machine settings".
Under the list of installed hardware click "add".
If you already have a virtual sound adapter installed, under "use physical sound adapter" try to type in the path to your actual sound card instead of "Auto Detect".
(this will probably be something like "/dev/audio" or "/dev/dsp")

If you have vmware player, I don't think there is any gui for adding hardware, but I think you should be able to do it manually.
In the folder where your virtual machine is, there should be a .vmx file.
Open it up using gedit or any other text editor, and add these two lines, if they are not already there:
```
sound.present = "TRUE"
sound.virtualDev = "es1371"
```

I have no idea how to add a printer, but I guess it could be done if you manage to set up a virtual network, so that you can share the printer from your host.
I'm not sure how to do this, but there should be some guide around here somewhere that may help you.
Or even someone that can point you in the right direction...

Hope you get it working!


thanks m8 it was so simple!!!!

I love ubuntu + vmware :)

---

### Post by drew buntu on 2007-07-16
I've just been reading these posts, desperately trying to get sound going in VMWare Server.  I've gone into Virtual Machine Settings, wanting to add or edit the virtual sound adapter and I came across two problems:
1. There is no current virtual sound adapter listed under hardware
2. The option to add or remove is not active

Is there something very obvious that I'm missing?  I'm trying to run Yahoo Music Unlimited in XP within VM Server.  I'm a bit new to the world of Ubuntu and though I'm getting a little bit frustrated with this, I want to stick it out and avoid a dual-boot situation.

Any assistance would be greatly appreciated!

Cheers!

---

### Post by jocko on 2007-07-17
> **drew buntu said:**
> I've just been reading these posts, desperately trying to get sound going in VMWare Server.  I've gone into Virtual Machine Settings, wanting to add or edit the virtual sound adapter and I came across two problems:
1. There is no current virtual sound adapter listed under hardware
2. The option to add or remove is not active

Is there something very obvious that I'm missing?  I'm trying to run Yahoo Music Unlimited in XP within VM Server.  I'm a bit new to the world of Ubuntu and though I'm getting a little bit frustrated with this, I want to stick it out and avoid a dual-boot situation.

Any assistance would be greatly appreciated!

Cheers!

Make sure the virtual machine is completely powered off (it's not enough to put it in suspend), otherwise you won't be able to add hardware.

---

