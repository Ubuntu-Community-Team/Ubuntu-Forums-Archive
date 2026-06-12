---
title: "Can you ACTUALLY change Grub font sizes or is that just a ruse"
date: 2022-01-29
forum: General Help
---

### Post by Cursed Lemon on 2022-01-29
Hey guys, so I've got Xubuntu running on a laptop and Grub reads the 1920x1080 resolution just fine when in UEFI mode, which is nice. However, like many people here have probably experienced, when Grub is that big, the font tends to be *very* small. 

Trying to set a font size in Grub Customizer results in a blocky, pixelated font that ignores custom color options and is possibly changing the entire resolution altogether. 

There is the *grub-mkfont* command line tool, however I'm getting the following error: 

```
user@computer: $ sudo grub-mkfont --output=/boot/grub/fonts/DejaVuSansMono24.pf2 \ --size=24 /usr/share/fonts/truetype/dejavu/DejaVuSansMono.ttf
can't open file --size=24, index 0: error 1: cannot open resource
```

I'm starting to think changing Grub font sizes is an urban legend.

Some people have said, "just lower the resolution of Grub then the font will be bigger". 

No. :)

---

### Post by dragonfly41 on 2022-01-29
I don't know about themes in standard grub, but I have played with rEFInd themes which I use for multi boots.

[https://github.com/bobafetthotmail/refind-theme-regular](https://github.com/bobafetthotmail/refind-theme-regular)

---

### Post by ajgreeny on 2022-01-29
Forget about grub-customiser which can cause more problems than it solves, and simply the line  shown below in  /etc/default/grub to get a reduced resolution in grub menu. Why do you say "no" to doing that?

Remove the # from the line
#GRUB_GFXMODE=640x480
and change it to a supported resolution that you like and fits your screen better.

You can find supported resolutions by hitting "c" when in the menu to get a grub command line, then type command ***videoinfo***.

---

### Post by Cursed Lemon on 2022-01-29
> **dragonfly41 said:**
> I don't know about themes in standard grub, but I have played with rEFInd themes which I use for multi boots.

[https://github.com/bobafetthotmail/refind-theme-regular](https://github.com/bobafetthotmail/refind-theme-regular)

I have been considering a switch to rEFInd, especially since I'd like to possibly triple-boot with Windows, Linux, and macOS.

---

### Post by Cursed Lemon on 2022-01-29
> **ajgreeny said:**
> Forget about grub-customiser which can cause more problems than it solves, and simply the line  shown below in  /etc/default/grub to get a reduced resolution in grub menu. Why do you say "no" to doing that?

Remove the # from the line
#GRUB_GFXMODE=640x480
and change it to a supported resolution that you like and fits your screen better.

You can find supported resolutions by hitting "c" when in the menu to get a grub command line, then type command ***videoinfo***.

Grub already automatically gets the resolution of the screen right.

---

### Post by dragonfly41 on 2022-01-29
I use rEFInd to triple boot, indeed quad boot, across cluster of external SSD's and HDD containers via USB.
Plus Windows 10 on internal HDD partition when I have to use it.
As for Mac sadly I don't have the bare metal needed (Apple). But interested in Macinthecloud.

---

### Post by Cursed Lemon on 2022-01-29
> **dragonfly41 said:**
> I use rEFInd to triple boot, indeed quad boot, across cluster of external SSD's and HDD containers via USB.
Plus Windows 10 on internal HDD partition when I have to use it.
As for Mac sadly I don't have the bare metal needed (Apple). But interested in Macinthecloud.

I have a Hackintosh install that I'd like to try out, I just need to reserve several hours of banging my head against a wall to try it.

---

### Post by Holger_Gehrke on 2022-01-29
> **Cursed Lemon said:**
> 

```
user@computer: $ sudo grub-mkfont --output=/boot/grub/fonts/DejaVuSansMono24.pf2 [COLOR=#ff0000]**\ **[/COLOR]--size=24 /usr/share/fonts/truetype/dejavu/DejaVuSansMono.ttf
can't open file --size=24, index 0: error 1: cannot open resource
```



That backslash I marked in red takes away the word separator special meaning of the following space and makes the fourth word of the command " --size=24"; since that does not start with a dash or double dash it can't be an option so it goes looking for a file named like that, doesn't find it and dies. Remove the backslash.

Holger

---

### Post by Cursed Lemon on 2022-01-29
> **Holger_Gehrke said:**
> That backslash I marked in red takes away the word separator special meaning of the following space and makes the fourth word of the command " --size=24"; since that does not start with a dash or double dash it can't be an option so it goes looking for a file named like that, doesn't find it and dies. Remove the backslash.

Holger

Damn you internet for leading me astray. 

Looks like that sort of worked but the results still have no subpixel shading and are ignoring my custom colors for some reason.

---

### Post by Holger_Gehrke on 2022-01-29
> **Cursed Lemon said:**
> Looks like that sort of worked but the results still have no subpixel shading and are ignoring my custom colors for some reason.

The first is not really surprising. PFF2 fonts are bitmap fonts - and I do mean bit. For each pixel there's only a 'set' or 'unset' state, no shades of grey ...
Colours should be possible, but I know too little about GRUB to help much with that.

Holger

---

### Post by oldfred on 2022-01-30
Grub fonts & themes.
[https://help.ubuntu.com/community/Grub2/Displays#Testing_Fonts_and_Splash_Images](https://help.ubuntu.com/community/Grub2/Displays#Testing_Fonts_and_Splash_Images)
How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

---

### Post by ajgreeny on 2022-01-30
I have nothing against those who wish to make the grub menu look better than a simple black screen with white text, but to my opinion it seems to be a lot of trouble for a few seconds of display at boot time, two seconds only in my system.

All I ever do is add an image, a version of my desktop image, and change the description of the OS in question by editing the line GRUB_DISTRIBUTOR= as shown below (it can be whatever you want, useful if you have a multiboot system with other versions of, for example, *ubuntu 20.04)

```
GRUB_DEFAULT=0
#Next line will make the countdown time show the menu
GRUB_TIMEOUT_STYLE=menu
#Next line changed from 0 to x for x second delay
GRUB_TIMEOUT=2
#Next line changed from true to false to allow delay countdown to show
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_DISTRIBUTOR="Xubuntu-20.04"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false
```
This works fine for me but of course, you can do whatever you want; for me, it's just not worth the bother.
I never need to, nor bother to change the line ***#GRUB_GFXMODE=640x480*** either, to get a larger font shown, though I admit my screen resolution is not very high being 1920x1080

---

### Post by QIII on 2022-01-30
> **Cursed Lemon said:**
> I have a Hackintosh install that I'd like to try out ...

This just won a free trip to a closed thread, as such installations violate Apple's ToS.

Thanks all.

---

