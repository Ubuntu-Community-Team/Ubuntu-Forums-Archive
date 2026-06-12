---
title: "Server 12.04.3 LTS portrait Mode"
date: 2013-10-09
forum: General Help
---

### Post by invictus2 on 2013-10-09
hi,
I am trying to get my server console tty screen to display in portrait mode on boot  but  haven't  been successful using fbcon;
my graphics card  is 
```

lshw -C video  *-display
       description: VGA compatible controller
       product: RV710 [Radeon HD 4350/4550]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:45 memory:d0000000-dfffffff memory:efee0000-efeeffff ioport:de00(size=256) memory:efe00000-efe1ffff



```

```
root@box:~# fbset

mode "1600x1200"
    geometry 1600 1200 1600 1200 32
    timings 0 0 0 0 0 0 0
    accel true
    rgba 8/16,8/8,8/0,0/0
endmode



```

and in /etc/default/grub i added  --->   GRUB_CMDLINE_LINUX="fbcon=rotate:3"
but that hasn't helped.... as screen buffer hasn't rotated.


fbterm -r3 does rotate the screen but I would like the default login terminal prompt etc to be in portrait mode from the get go... and searching indicates that fbcon is supposed to work...but I haven't been successful. 

Would really appreciate  any help...as I can't seem to find a answer(that has worked for me) on this relating to server os.
thanks
iv2

solution:
 kernel Frame Buffer rotation option wasn't set,
solution:
compile kernel with FB rotation enabled, install kernel--> then pass the fbcon="rotate:3" argument via GRUB ===> sorted:-D

---

### Post by DuckHook on 2013-11-02
Hi invictus2,

Thanks for this posting. For years I've been looking for a solution that rotates the console. Knew it had something to do with *fbcon*, but didn't know that *fbterm* would do the job. Your posting is a real peach.

However, I need *sudo* to invoke *fbterm* which kicks me into a root shell, where I'd rather not be. Question: what must I do to invoke *fbterm* without *sudo*?

P.S. Recompiling the kernel just to turn on rotate in *fbcon* seems to be too much cost for too little reward. I'm happy to stick with the *fbterm* solution if I can use it as a regular user.

---

### Post by DuckHook on 2013-11-04
After conducting further research, I've found the solution to my own question, or at least most of the solution at any rate, and thought I would post it for posterity.

It turns out that the solution to get *links2* working in graphics mode also works for *fbterm*. Makes sense when you think about it. Both use the framebuffer to work their magic.```
sudo nano /etc/udev/rules.d/framebuffer.rules
```and create the line:```
KERNEL=="fb0",  OWNER="root", MODE="0660"
```then add user to "video" group with:```
sudo usermod -a -G video username
``````
sudo nano /etc/udev/rules.d/90-permissions.rules
```and add the following lines:```
KERNEL=="tty[0-9]*", GROUP="root", MODE="0666"
KERNEL=="mice", MODE="0666"
```Though the last line is not strictly necessary, it is needed for any app with mouse support (like *links2*) and may as well be included.

Reboot and you s/b good to go.

---

