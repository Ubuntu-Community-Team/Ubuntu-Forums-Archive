---
title: "Display problems."
date: 2012-12-22
forum: General Help
---

### Post by Luigi2012SM64DS on 2012-12-22
Hi. I am having display problems. When i go into the file manager the folder graphic doesn't show up (its just blank with the title). Please see the attached file

---

### Post by sudodus on 2012-12-22
I haven't seen that before!

Which version of Lubuntu is it?

Have you tried
```
sudo apt-get update
sudo apt-get upgrade
```
and if necessary
```
sudo apt-get dist-upgrade
```
and reboot?

---

### Post by Luigi2012SM64DS on 2012-12-22
> **sudodus said:**
> I haven't seen that before!

Which version of Lubuntu is it?

Have you tried
```
sudo apt-get update
sudo apt-get upgrade
```
and if necessary
```
sudo apt-get dist-upgrade
```
and reboot?
Its Lubuntu 12.10
I installed the updates in one install but it didn't make a difference. I tried using a live usb and same problem. The graphics card is a NVIDIA Quadro4 580 XGL. I tried installing the NVIDIA display drivers but it didn't work and screwed everything up(Screen Resolution was changed 640x480 and programs and text was incredibly small and hard to read.)
One more thing checkboxes don't appear properly either. they appear as if you clicked on them but you are still holding down the button an when you move your coursor over them he appear fine.

---

### Post by sudodus on 2012-12-22
I run Lubuntu 12.04 (or should I say lubuntu-desktop in a system with several desktops installed). I have only tested Lubuntu 12.10 briefly, and at that time it worked properly in my computer.

Since it is the same problem with the live session booted from a standard iso file, it should not be the proprietary driver either.

Have you tried various boot options?

Can you download the iso and test with Lubuntu 12.04?

What about the file browser? Try to install thunar or nautilus, and see if that works better than the default pcmanfm

---

### Post by Luigi2012SM64DS on 2012-12-23
I tried installing Ubuntu itself and it won't even load unity and gives me an internal error.

---

### Post by sudodus on 2012-12-23
Ubuntu might need too much horsepower ...

- Have you tried various boot options?
[[COLOR="Red"]https://help.ubuntu.com/community/BootOptions[/COLOR]]("https://help.ubuntu.com/community/BootOptions")

- Have you tried another file browser (Thunar, Nautilus)?

It helps suggesting ways to solve your problem, if you tell us about your computer:

- Kind of computer (brand, model ...)
- Motherboard
- CPU
- RAM
- graphics chip/card (you already told us) VIDIA Quadro4 580 XGL
- internet chip/card

I know that some people have problems with the version 12.10, which is still new. ***It is well worth trying Lubuntu 12.04*** (unless that version has problems with graphics or wifi). The Lubuntu specific packages have no long time support (LTS), but most packages belong to the general Ubuntu 12.04 LTS, and can be expected to get very good support.

Lubuntu 12.04 will get full support until October 2013, and by that time I'm sure there will be a good candidate for upgrading to a new version.

Good luck :-)

---

### Post by Luigi2012SM64DS on 2012-12-23
> **sudodus said:**
> Ubuntu might need too much horsepower ...

- Have you tried various boot options?
[[COLOR="Red"]https://help.ubuntu.com/community/BootOptions[/COLOR]]("https://help.ubuntu.com/community/BootOptions")

- Have you tried another file browser (Thunar, Nautilus)?

It helps suggesting ways to solve your problem, if you tell us about your computer:

- Kind of computer (brand, model ...)
- Motherboard
- CPU
- RAM
- graphics chip/card (you already told us) NVIDIA Quadro4 580 XGL
- internet chip/card

I know that some people have problems with the version 12.10, which is still new. ***It is well worth trying Lubuntu 12.04*** (unless that version has problems with graphics or wifi). The Lubuntu specific packages have no long time support (LTS), but most packages belong to the general Ubuntu 12.04 LTS, and can be expected to get very good support.

Lubuntu 12.04 will get full support until October 2013, and by that time I'm sure there will be a good candidate for upgrading to a new version.

Good luck :-)

I will redownload the lubuntu iso. I cannot try the lubuntu 12.04 as it always gives me a kernel panic.
Computer: Compaq D510 SFF
Motherboard: Compaq 07E4h
CPU: Intel Pentium 4
Ram: 1GB
Graphic: NVIDIA Quadro4 580 XGL
Intrernet Chip: (do you really need to know?) Intel PRO/100 VM NIC
Edit: What option should i choose in the boot options?

---

### Post by Luigi2012SM64DS on 2012-12-24
how do you switch the graphics driver? like from nv to vesa or whatever.

---

### Post by sudodus on 2012-12-24
If you used ***jockey-gtk*** before, you can use it to switch back too. If in text mode, you can use ***jockey-text***.

```
jockey-text -help
``` prints some help info.

If you installed a downloaded proprietary driver, look at this link.

[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1948324[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1948324")

It may not reflect exactly what you want to do, but it might give you hints and help you along the way.

Try if possible to use the built-in free driver!

Good luck :-)

---

### Post by Luigi2012SM64DS on 2012-12-24
EDIT2: I was able to install the NVIDIA graphics driver and now everything appears correctly BUT i cannot set my resolution to 1360 x 768. it only goes up to 1024x 768 and xrandr won't let me create a custom resolution.

---

### Post by Luigi2012SM64DS on 2012-12-24
> **tashalb said:**
> I face same problem but solve.
How? Next time please say how in ONE post.

---

### Post by Luigi2012SM64DS on 2012-12-24
bamp

---

### Post by vasa1 on 2012-12-24
> **Luigi2012SM64DS said:**
> How? Next time please say how in ONE post.
I'm not sure that that poster had anything useful to say. The two other posts made elsewhere by the same poster don't really contribute anything.
You may consider asking your question at the Lubuntu mailing list as well: [https://lists.ubuntu.com/mailman/listinfo/lubuntu-users](https://lists.ubuntu.com/mailman/listinfo/lubuntu-users)

---

### Post by sudodus on 2012-12-26
> **Luigi2012SM64DS said:**
> EDIT2: I was able to install the NVIDIA graphics driver and now everything appears correctly BUT i cannot set my resolution to 1360 x 768. it only goes up to 1024x 768 and xrandr won't let me create a custom resolution.

I think the driver does not cooperate 100% with your card. Is it still better than using the standard built-in driver?

1. Consider vasa1's suggestion about the Lubuntu mailing list.

2. When there a such compatibility problem, I suggest that you try another linux distro, that can be run as a live session. Run it live and don't bother to install anything until it works better than your present installed Lubuntu system.

Knoppix, which is meant to run live or persistent live, is known to have good hardware detection. It is also good for aging computers.

---

### Post by Luigi2012SM64DS on 2012-12-26
> **sudodus said:**
> I think the driver does not cooperate 100% with your card. Is it still better than using the standard built-in driver?

1. Consider vasa1's suggestion about the Lubuntu mailing list.

2. When there a such compatibility problem, I suggest that you try another linux distro, that can be run as a live session. Run it live and don't bother to install anything until it works better than your present installed Lubuntu system.

Knoppix, which is meant to run live or persistent live, is known to have good hardware detection. It is also good for aging computers.
I will try that. But first how do you install nouveau drivers? i want to try that.

---

### Post by sudodus on 2012-12-26
> **Luigi2012SM64DS said:**
> I will try that. But first how do you install nouveau drivers? i want to try that.
[URL="https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia"]

By default Ubuntu will use the open source video driver called Nouveau for your NVIDIA graphics card. This driver lacks support for 3D acceleration and may not work with the very latest video cards or technologies from NVIDIA. See

[COLOR="Red"]https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia[/COLOR][/URL]

So when you run a live session booted from the install Lubuntu CD/DVD/USB drive, nouveau should jump in automatically, if it can recognize your chip/card as one of those supported from nvidia. You can test it this way.

And as I wrote earlier, in your installed system you get it back in different ways depending on how you installed your nvidia proprietary driver.

---

### Post by Luigi2012SM64DS on 2012-12-27
> **sudodus said:**
> [URL="https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia"]

By default Ubuntu will use the open source video driver called Nouveau for your NVIDIA graphics card. This driver lacks support for 3D acceleration and may not work with the very latest video cards or technologies from NVIDIA. See

[COLOR=Red]https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia[/COLOR][/URL]

So when you run a live session booted from the install Lubuntu CD/DVD/USB drive, nouveau should jump in automatically, if it can recognize your chip/card as one of those supported from nvidia. You can test it this way.

And as I wrote earlier, in your installed system you get it back in different ways depending on how you installed your nvidia proprietary driver.
Oh. Well when I used the NVIDIA drivers everything displayed correctly just i couldn't change the resolution. XrandR all ended with an error.
BTW i tried Knoppix and it worked perfect but i would like something im familiar with. :D

---

### Post by sudodus on 2012-12-27
> **Luigi2012SM64DS said:**
> Oh. Well when I used the NVIDIA drivers everything displayed correctly just i couldn't change the resolution. XrandR all ended with an error.
BTW i tried Knoppix and it worked perfect but i would like something im familiar with. :D
Knoppix is based on Debian (like [KLX]Ubuntu) and it uses LXDE (like Lubuntu), so many things are similar. It won't take a long time to get used to it :-)

---

### Post by Luigi2012SM64DS on 2012-12-27
> **sudodus said:**
> Knoppix is based on Debian (like [KLX]Ubuntu) and it uses LXDE (like Lubuntu), so many things are similar. It won't take a long time to get used to it :-)
Yeah, but to me lubuntu seems easy to use. So how do i fix resolution from 1024x768 to 1360x768?

---

### Post by Luigi2012SM64DS on 2012-12-28
Anyone?

---

### Post by sudodus on 2012-12-28
> **Luigi2012SM64DS said:**
> I will redownload the lubuntu iso. I cannot try the lubuntu 12.04 as it always gives me a kernel panic.
Computer: Compaq D510 SFF
Motherboard: Compaq 07E4h
CPU: Intel Pentium 4
Ram: 1GB
Graphic: NVIDIA Quadro4 580 XGL
Intrernet Chip: (do you really need to know?) Intel PRO/100 VM NIC
Edit: What option should i choose in the boot options?
Let's have another look at your hardware. I have been running Ubuntu 10.04 and newer Lubuntu and Linux Mint on a similar Compaq SFF (but with a Celeron 3 GHz cpu). I am surprised that you get a kernel panic with 12.04. I was looking for a wifi chip/card/stick, that might cause trouble. There should be no problem with your ethernet chip.

I guess that the problem is to make Lubuntu cooperate with the graphics card.

The boot option to start with is ***nomodeset***. You could try the others too. Maybe you can start the computer with one or more boot options and avoid kernel panic. And in that case Lubuntu 12.04 could be the best version.

By the way, is there a working built in graphics chip? In that case, disconnect the graphics card, and test if the computer will cooperate better with Lubuntu.

I found this link (browsing for ***ubuntu and nvidia quadro4 580 xgl video card***:

[[COLOR="Red"]http://voices.yahoo.com/issues-ubuntu-1010-maverick-meerkat-upgrades-6942024.html[/COLOR]]("http://voices.yahoo.com/issues-ubuntu-1010-maverick-meerkat-upgrades-6942024.html")

>  Older Nvidia Cards (Nvidia-96) do not work with Ubuntu 10.10 Maverick Meerkat...Yet
The X server that runs the graphical interface in Ubuntu 10.10 runs version 1.9. Nvidia has yet to issue an update to drivers for the older set of video cards for the new X server. An update has been sent for Nvidia-173, and Nvidia developers have stated the new drivers for the Nvidia 96 cards are in development. If you are using an older Nvidia video card, then you may want to hold off doing the upgrade until the new drivers are released. Here are some of the cards that still use this older driver: GeForce 6800 Ultra, GeForce 6800, GeForce 6800 XE, Quadro4 580 XGL, Quadro NVS with AGP8X, Quadro4 380 XGL, Quadro NVS 50 PCI, GeForce2 Integrated GPU, GeForce 7300 LE, Quadro NVS 110M.

These are just a few of the cards that run Nvidia-96 drivers. It is a little bit of a shame that there could not be better coordination between vendors that provide drivers for hardware. But this is what you get when dealing with closed source operators like Nvidia.

Ubuntu 10.10 has passed end of life (no more security updates), but you could check if Ubuntu 10.04 LTS works better. It's end of life is April 2013, so it's no good alternative, but if it works with a proprietary driver suggested, you could try to use that version of the nvidia graphics driver in the modern Lubuntu (you might also find it packaged at the nvidia web site).

If you want to try this detour, download the newest subversion, 10.04.4 LTS [[COLOR="red"]http://releases.ubuntu.com/lucid/[/COLOR]]("http://releases.ubuntu.com/lucid/")

---

### Post by windscape on 2012-12-28
Hi,

The information here [https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution") worked for me to get the resolution right for my monitor with an intel integrated graphics on Xubuntu 12.10.

---

### Post by Luigi2012SM64DS on 2012-12-28
OK. i am downloading the 12.04 LTS lubuntu. How would i use the nomodeset boot?

---

### Post by sudodus on 2012-12-29
> **Luigi2012SM64DS said:**
> OK. i am downloading the 12.04 LTS lubuntu. How would i use the nomodeset boot?

It is pretty well described in this link

[[COLOR="Red"]https://help.ubuntu.com/community/BootOptions[/COLOR]]("https://help.ubuntu.com/community/BootOptions")

*Edit*: Unfortunately, Lubuntu 12.04 has no LTS.

Ubuntu 12.04 has 5 years LTS, Xubuntu 12.04 has 3 years LTS, Lubuntu has only 18 months support of the Lubuntu specific packages.

---

### Post by pj_kare on 2012-12-29
The original problem with the missing icons may have been fixed with the instructions on this page-> [http://askubuntu.com/questions/216065/lubuntu-12-10-icon-display-problems](http://askubuntu.com/questions/216065/lubuntu-12-10-icon-display-problems)

My GF had the same problem on her laptop (looked exactly as your picture shows) and this fixed the problem. This answer may be too late to be of any use, but we just found your post while looking for an answer to a question of our own. (We are trying to find out if we can have icon view in one folder and either compact view or thumbnail view in another folder, as far as we can see we can only have one choice, same view for all folders.)

---

### Post by sudodus on 2012-12-29
> **pj_kare said:**
> The original problem with the missing icons may have been fixed with the instructions on this page-> [http://askubuntu.com/questions/216065/lubuntu-12-10-icon-display-problems](http://askubuntu.com/questions/216065/lubuntu-12-10-icon-display-problems)

My GF had the same problem on her laptop (looked exactly as your picture shows) and this fixed the problem. This answer may be too late to be of any use, but we just found your post while looking for an answer to a question of our own. (We are trying to find out if we can have icon view in one folder and either compact view or thumbnail view in another folder, as far as we can see we can only have one choice, same view for all folders.)

1. Thanks for the tip.

2. In pcmanfm it is like that, but you can save how you want to view individual folders in nautilus. And you can install nautilus in Lubuntu, and test if you like it.

```
sudo apt-get install nautilus
```
You may want to run nautilus without letting it manage the desktop, in that case you can create an alias for it:

```
alias nautilus='nautilus --no-desktop'
```

---

### Post by pj_kare on 2012-12-29
> **sudodus said:**
> 1. Thanks for the tip.
 
2. In pcmanfm it is like that, but you can save how you want to view individual folders in nautilus. And you can install nautilus in Lubuntu, and test if you like it.
 
```
sudo apt-get install nautilus
```
You may want to run nautilus without letting it manage the desktop, in that case you can create an alias for it:
 
```
alias nautilus='nautilus --no-desktop'
```
 
Thanks for your tip also, We use Icon view for some folders, thumbnail for others, but neither are pratical for folders containing large numbers of files, such as mp3 collection, for those folders we prefer compact view.

---

### Post by Luigi2012SM64DS on 2012-12-29
My bad. The kernel panic happened on my other computer. Not this one. Anyways everything displays correctly in 12.04 Lubuntu and it has better visuals! I'll try that sub pixel thing in April 2013 when i have to update. Thanks! 

One more thing. My volume buttons my my keyboard control only the "master" volume in alsamixer. i want them to control "master mono". Anyway to change this?

---

### Post by sudodus on 2012-12-30
> **Luigi2012SM64DS said:**
> My bad. The kernel panic happened on my other computer. Not this one. Anyways everything displays correctly in 12.04 Lubuntu and it has better visuals! I'll try that sub pixel thing in April 2013 when i have to update. Thanks! 

One more thing. My volume buttons my my keyboard control only the "master" volume in alsamixer. i want them to control "master mono". Anyway to change this?
My solution to the frugal audio and other controls in Lubuntu is to install xubuntu-desktop and use those of Xubuntu ;-)

---

### Post by Luigi2012SM64DS on 2012-12-30
> **sudodus said:**
> My solution to the frugal audio and other controls in Lubuntu is to install xubuntu-desktop and use those of Xubuntu ;-)
And what program would i use in xubuntu-desktop to change the volume keys to control "master mono"?

---

### Post by sudodus on 2012-12-31
> **Luigi2012SM64DS said:**
> And what program would i use in xubuntu-desktop to change the volume keys to control "master mono"?
Try (when logged into a Xubuntu session) from the menu:

***Program -- Multimedia -- Volume Control for PulseAudio***

It works for me.

If still no luck, I suggest that you start a new thread with a good descriptive title to attract those Ubuntu Forum members, who are good at tweaking audio.

---

### Post by Luigi2012SM64DS on 2012-12-31
I get connection to pulseaudio failed. But ok i'll make a new thread.

---

### Post by sudodus on 2012-12-31
Good luck with the new thread :-)

---

