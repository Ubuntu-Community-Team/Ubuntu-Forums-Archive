---
title: "Live CD wont boot"
date: 2007-08-02
forum: General Help
---

### Post by bjb.butler on 2007-08-02
Hello, I am trying to get the Ubuntu Feisty live CD to boot, but it just hangs on a black screen. I know that it is my video card, i have an nVidia GeForce EN8500GT.

I want to boot the live cd with the 'vesa' driver, but i dont know how. Also, once i get it instlled, how do I tell it to again use the vesa driver when i first boot so that i can manually install the nvidia driver?

---

### Post by merlinus on 2007-08-02
Did you try Safe Video Mode?  Also, the text-based Alternate Install cd should get you to a CLI where you can select the vesa driver.

-merlin

---

### Post by bjb.butler on 2007-08-02
ok, thank you. I am in the live cd via 'graphics safe mode'. I am now going to install the distro. But once its installed and i try to boot into the OS, i am going to get a black screen. How do I choose 'vesa' when i boot up so i can go get the nvidia drivers?

thanks in advance

---

### Post by merlinus on 2007-08-02
Press "Esc" when prompted to display the grub boot menu, boot into recovery mode, login...then enter:

(or Ctrl-Alt-F1 to get to prompt)

sudo dpkg-reconfigure xserver-xorg

You can probably go with the default for most screens, but select "vesa" for your video driver.

Then:

startx

or reboot...

This should at least get you to a GUI, then you can search how to install the correct video drivers for your card.

-merlin

---

### Post by bjb.butler on 2007-08-02
ok i will try that out soon (its installing right now) .

im not sure if it was because i am in a live cd, but i tried installing the drivers for my card  

([http://www.nvidia.com/object/linux_display_ia32_100.14.11.html](http://www.nvidia.com/object/linux_display_ia32_100.14.11.html))

but i get an error saying that i was using an X Server...How else would I install the driver without being in X ?

---

### Post by merlinus on 2007-08-02
After install, following the directions in my previous post will get you to a CLI and allow you to install the driver.

Then  sudo dpkg-reconfigure xserver-xorg

will give the nvidia option.

-merlin

---

### Post by BeerMit on 2007-09-02
I too am having trouble booting my live CD (7.04) (64bit)
Im thinking it has something to do with video cards
Im running two Nvidia 7600 GTs
Ubuntu seems to boot fine using the noapic and nolapic commands
However, i cant see anything on my screen at all
I here Ubuntu start
but my screen is blank

please help
im getting rather discouraged

-----
Athlon 64 X2 5200
GA-M57SLI4
2x Nvidia 7600 GT
4GB G.skill DDR2 800
500GB Seagate SATA

---

