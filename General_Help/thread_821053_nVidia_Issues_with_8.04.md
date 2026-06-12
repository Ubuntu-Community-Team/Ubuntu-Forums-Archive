---
title: "nVidia Issues with 8.04"
date: 2008-06-06
forum: General Help
---

### Post by 64Media on 2008-06-06
I'm running Ubuntu 8.04 and I can't get my resolution past 640x480.

I know I should be able to, but when I try to adjust the resolution, that's the biggest one they have.

---

### Post by Sef on 2008-06-06
What NVidia card do you have?

---

### Post by 64Media on 2008-06-06
I believe it is the GeForce 7900 GT/GTO, as it is displayed in the nVidia Server X Config settings.

---

### Post by Seamus on 2008-07-15
I am installing Ubuntu 8.04 on a friends computer and having the same issue.

Default resolutions are working,but as soon as I try and use the restricted drivers I get the following error message:

"Can not display this video mode"

I have to exit and restart in safe mode and disable the restricted drivers.

Graphics card =

1# lspci -v | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV45 [GeForce 6800 GTO] (rev a2) (prog-if 00 [VGA controller])

Any help appreciated as always!

If I can't get the Nvidia working, surely I can default back to the Intel onboard graphics card (this is a bog standard Dell so assuming it has one in it)

---

### Post by jonian_g on 2008-07-15
Run in a terminal

sudo displayconfig-gtk

Where it says "Model" choose the model of your monitor. If it's not in the list click add, then find the cdrom that came with your monitor, put in the drive and locate the *.inf file. This will add your monitor model on the list, select it and press ok. Enable the restricted drivers and you will be able to choose higher resolutions.

If you don't have the cdrom select one of the generic models.

---

### Post by ellgor on 2008-07-16
Hi,

You could try this, check to see if you have a package called nvidia-settings (synaptic) install if not, then, open a terminal and type in:

gksudo nvidia-settings

a new window will open with the nvidia settings for you to adjust, hope this helps.

Regards,Ellgor.

---

### Post by jimv on 2008-07-16
I have a 7800 and the only way I got it to work was with EnvyNG.

So in a terminal, type 'sudo apt-get install envyng-gtk'

Then type 'envyng -t' to run it in text mode (best option for crappy resolution)
The press 1
Then it will install the driver
Then reboot

---

