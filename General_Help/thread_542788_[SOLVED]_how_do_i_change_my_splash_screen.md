---
title: "[SOLVED] how do i change my splash screen"
date: 2007-09-04
forum: General Help
---

### Post by shortybookit on 2007-09-04
i dont have a clue about this linux stuff yet i am coming over from windows 

but i had this post in beginers talk for 2 days now i think this should be a fairly simple answer but it is not

my question how to change my splash screen isnt there a way to change it like you can change anything else--screensaver,background,theme???

answers from my other post told me to  install gnome art
sudo apt-get install gnome-splashscreen-manager

when i do this line in the terminal it comes back with CAN NOT FIND PACKAGE 

please help also how do i update my video card? the prgoam envy does not work i get an s server error then black screen then hard reboot 
I HAVE THE Intel(R) 82865G installed

---

### Post by ThrobbingBrain66 on 2007-09-04
If you have an Intel chip set, you don't use Envy....that's only for ATI and NVIDIA.  What's wrong with your video that you want to update the driver?  As far as Intel goes, you're pretty much stuck with the driver provided in the kernel.

To install gnome-splash-screen manager you must have the Universe repo enabled.
Go to System > Administration > Software Sources and check the box for the Universe repo.  Then install it with the command you previously used.

You can get GDM screens from [www.art.gnome.org](www.art.gnome.org) or [www.gnome-look.org](www.gnome-look.org)

I think I already helped you, in another thread, with your other problems about theming, did you get that all sorted out?

---

