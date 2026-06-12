---
title: "Virtual Box"
date: 2007-08-05
forum: General Help
---

### Post by bjb.butler on 2007-08-05
I have a nvidia geforce EN8500GT video card, with the recomended drivers from nvidia installed.

I have windows xp running in virtual box , and it works fine, but the max res. is 1280x768, Which is a little low and i want windows to expand to the entire screen. i tried running the nvidia driver cd for windows but it says it cant find any hardware to go along with the drivers. Is there a way to increase the screen resolution?

thanks,bj

---

### Post by apswartz on 2007-08-05
Have you installed the guest tools?
See Virtualbox User Manual, page 45 (available from virtualbox download page)

---

### Post by dreadlord_chris on 2007-08-05
That's because VBox (and all the other virt apps out there) only emulate hardware - which basically means that *inside* the virtual environment you don't have an NVIDIA card - you have an emulated virtual GPU...

---

### Post by soxs on 2007-08-05
In the left top corner (of the virtual machine window) there should be a button named machine, engine or something like that. Click and the first menu item shows you the option to use your guest system (WinXP) in full screen mode. (Some stuff may differ, as I use the german version) and of course install the guest additions before...

---

