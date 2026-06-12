---
title: "nvidia optimus troubles"
date: 2013-10-15
forum: General Help
---

### Post by cirwin2010 on 2013-10-15
I just bought a new laptop. The hp Envy 15t-j000 quad. 

haswell i7
gt740m

I cannot get ubuntu or any other linux distrobution I have tried to boot as everytime I get a black screen. I did eventually get ubuntu 12.04.3 LTS installed by using the nomodeset boot option. When I use nomodeset I can get to the command line but the desktop environment does not boot. I have tried just about everything I could find. I have tried using the opensource drivers, nvidia-current, nvidia-319 with bumblebee and nvidia-prime. I get the same result every single time with a black screen at boot. 

I would think that by default ubuntu would use the intel intigrated graphics over the nvidia and considering that I can't get the desktop evironment to show I wonder if that is the problem.

edit: using the command "lspci | grep VGA" only shows my intel integrated graphics.

---

### Post by oldfred on 2013-10-16
Most with Haswell have had better luck with 13.10 even though it has been beta. Will be released tomorrow, sometime.

I have seen all of these instead of nomodeset for Intel, and posted once or twice. Response was it worked but they did not tell me which one or combination actually worked??

 Force Intel Video mode as boot parameter in grub menu - change to your screen size
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60
 i915.i915_enable_rc6=1

   Asus i3 with Intel graphics, 
acpi_osi=Linux
video=1280x1024-24@75 or whatever native resolution is

   Some other Intel boot options
acpi_osi=Linux  acpi_backlight=vendor

---

