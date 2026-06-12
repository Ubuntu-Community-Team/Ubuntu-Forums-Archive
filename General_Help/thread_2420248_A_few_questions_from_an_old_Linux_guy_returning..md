---
title: "A few questions from an old Linux guy returning."
date: 2019-06-01
forum: General Help
---

### Post by cylent on 2019-06-01
hello.

a few questions to start with.

whats best for laptops as a distro? should i stick with ubuntu 19.04? or should i go with popOS?

my laptop is an [asus vivobook S14 S406UA]([https://in.pcmag.com/asus-vivobook-s14-s406u-review/124133/asus-vivobook-s14-s406u-review](https://in.pcmag.com/asus-vivobook-s14-s406u-review/124133/asus-vivobook-s14-s406u-review)) with the following specs:



    Processor Intel Core i5-8250U
    Graphics adapter Intel UHD Graphics 620, Core: 300-1100 MHz, Dual-Channel, 22.20.16.4708
    Memory 8192 MB  , DDR3L-1866, Dual-Channel, soldered-in, no memory slots
    Display 14 inch 16:9, Full HD 1080p IPS panel 
    Resolution: 1920x1080 
    Mainboard Intel Kaby Lake-U iHDCP 2.2 Premium PCH
    Storage SanDisk SD8SN8U256G1002, 256 GB  

1) since this is a 1920x1080 display it defaults to 100% scaling and things are small (is it HiDpi)?my main issue right now is the fractional scaling which i solved by adding the proper linux in gnome gsettings (mutter). windows uses 150% but when i boot ubuntu it only shows 100% and 200%. i wanted 125% or 150%.

so i did this line in terminal and all was well. i am also aware i can do it in dconf-editor under gnome -> mutter -> experimental.


gsettings set org.gnome.mutter experimental-features "['x11-randr-fractional-scaling']"

Since ubuntu 19.04 uses x11 i believe this is the correct line. source:  ([https://www.linuxuprising.com/2019/04/how-to-enable-hidpi-fractional-scaling.html](https://www.linuxuprising.com/2019/04/how-to-enable-hidpi-fractional-scaling.html))



should i stick with x11 or convert to wayland ? because applying this scaling line (from what i read) taxes the cpu/gpu.



2) this is a vmware question.

i have tried this in the past and really forgot the term for it but in vmware is there a way to boot a windows partition from within Linux vmware player or vmware workstation?

the thing is i wanna install ubuntu on my laptop and want vmware to boot the windows partition.

do i have to do the conversion (vmware converter method)? i still wanna boot back into windows then after if needed.

also,

3) i have disabled CSM in the UEFI settings and am able to press escape during boot to select a usb drive. i wanna be sure when i do the install it install in GPT mode / UEFI and not legacy.



please help!

---

### Post by HermanAB on 2019-06-01
Howdy,

I think that laptop can run anything.

BTW, Wayland is no more.  The latest Ubuntu runs Xorg, which is much better.

---

### Post by cylent on 2019-06-01
> **HermanAB said:**
> Howdy,

I think that laptop can run anything.

BTW, Wayland is no more.  The latest Ubuntu runs Xorg, which is much better.

What do you mean Wayland is no more? 
I know Ubuntu ditched it but fedora runs it as standard. 

I also heard x11 is more taxing on the cpu /gpu with fractional scaling this is why I am asking about Wayland.

---

### Post by cruzer001 on 2019-06-01
Actually I think xWayland is now the default.

---

### Post by crip720 on 2019-06-01
I know that in Ubuntu 19.04 that wayland is an option, xorg is default, but I also installed Unity desktop so that might be why I noticed it.  I think you have to install Windows in vmware.  Vmware will not boot up a Windows partition on your ssd/hard drive, but there are ways of accessing data on  partitions on your drive from vmware.

---

### Post by CatKiller on 2019-06-01
> **cylent said:**
> whats best for laptops as a distro? should i stick with ubuntu 19.04?  
Whichever you like best is the one to use. I'd advise using 18.04 rather than 19.04, since 18.04 is a Long Term Support release. 
> should i stick with x11 or convert to wayland ? 
Wayland *is* the future: the only real development of X11 now is to make XWayland work better. It's also now as old as X11 was when they decided it was so old and crusty that it needed replacing. Canonical feel that it's not yet ready to be the default, and I'm happy to defer to them on that. 
>  i have disabled CSM in the UEFI settings and am able to press escape during boot to select a usb drive. i wanna be sure when i do the install it install in GPT mode / UEFI and not legacy.
The boot menu when you select to boot from the USB drive should say UEFI in its description. A handy check is that when booted in BIOS mode, the background is aubergine; when booted in UEFI mode, the background is black.

---

### Post by oldfred on 2019-06-02
My standard post, but catkiller is more correct as it is aubergine.

       Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

