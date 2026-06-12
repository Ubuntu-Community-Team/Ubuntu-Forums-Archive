---
title: "Linux (Ubuntu and non) will not boot with new monitor!"
date: 2007-01-24
forum: General Help
---

### Post by Donshyoku on 2007-01-24
First off, I will dispel the common cultprits. Yes, my montior works, yes my video card works, and yes I have my CMOS options set with the DVD drive as the first boot option. 

The problem here is not so much as getting the disc to boot as it is to get it to finish booting. PCLinuxOS, Ubuntu, and SLAX live CDs don't boot. The graphical portions start to display (in Ubuntu and PCLOS) but they freeze partially booted. This has been happening since Christmas when I got my new monitor. Could the display be the culprit?

I am not sure about that last comment, because some distros give me a picture. Fedora Core 6 will load into anaconda fine, but freezes before the menu options appear. The Live CDs listed about show me video as they boot but freeze when entering the desktop.

It is not a common problem for the system as I can boot and fully install Windows XP and Windows Vista. Why aren't these Linuxes (old and new) not booting correctly?

Thanks in advance!

---

### Post by dcstar on 2007-01-25
> **Donshyoku said:**
> First off, I will dispel the common cultprits. Yes, my montior works, yes my video card works, and yes I have my CMOS options set with the DVD drive as the first boot option. 

The problem here is not so much as getting the disc to boot as it is to get it to finish booting. PCLinuxOS, Ubuntu, and SLAX live CDs don't boot. The graphical portions start to display (in Ubuntu and PCLOS) but they freeze partially booted. This has been happening since Christmas when I got my new monitor. Could the display be the culprit?

I am not sure about that last comment, because some distros give me a picture. Fedora Core 6 will load into anaconda fine, but freezes before the menu options appear. The Live CDs listed about show me video as they boot but freeze when entering the desktop.

It is not a common problem for the system as I can boot and fully install Windows XP and Windows Vista. Why aren't these Linuxes (old and new) not booting correctly?

Thanks in advance!

Does your definition of "freeze" mean no display, or a display and an unresponsive system?

If it means no display, then most likely the various linuxes are setting and incorrect monitor refresh rate, possibly because they are incorrectly detecting your video card/monitor.

You may want to plug in a different monitor (or maybe no monitor?).

---

### Post by meng on 2007-01-25
LCD monitor? Perhaps it's a refresh rate issue, i.e. system is trying to refresh at >60 Hz.
Press ctrl-alt-f1 when you come to the "blank screen" Then log in to a console
then
sudo dpkg-reconfigure xserver-xorg

---

### Post by Donshyoku on 2007-01-25
Sorry, I don't think I explained it clearly enough.  My fault...

I don't ever get no video.  With Fedora for example, anaconda loads the background and a portion of the image at the top but it is gargled like a messed up satellite feed (if you have satellite, you know how much that sucks... but onto more pertinant things).  With Ubuntu (Dapper and Edgy) it loads the OS, but the screen "freezes" when it is loading the splash screen.  The splash screen is garbled with red, purple, yellow, and green lines running through and messing up the image.  However, the system stops there... it doesn't load the desktop and doesn't load any more of the image... it just sits there half-way through the splash into Gnome.

However, I have "fixed" the issue, but am not really happy with it.  When I use my integrated Intel GMA900 (using the i810 driver), the system boots fine and works fine.  But the resolution is at 1280x1024 and the picture is really pixellated (probably due to using VGA on this monitor that is intended only for DVI).  I get this same image problem in Windows XP.  But it works.  As soon as I throw my PCI-Express card in (like I had it before when I posted this thread), the picture and system freezes just as I described above.  The card works fine in Windows and I really don't want to have to resort to using my integrated on a $140 video card.  Is there a better solution?

Should I boot and install with my Intel card and then throw in the Nvidia?  Can I install the Nvidia driver prior to placing in the card (say with my Intel... throw in the card afterwards and hope it is set up properly?).  Thanks for the quick replies, I hope to hear more soon.

---

### Post by dcstar on 2007-01-25
> **Donshyoku said:**
> 
........
 As soon as I throw my PCI-Express card in (like I had it before when I posted this thread), the picture and system freezes just as I described above.  The card works fine in Windows and I really don't want to have to resort to using my integrated on a $140 video card.  Is there a better solution?

Should I boot and install with my Intel card and then throw in the Nvidia?  Can I install the Nvidia driver prior to placing in the card (say with my Intel... throw in the card afterwards and hope it is set up properly?).  Thanks for the quick replies, I hope to hear more soon.

I think Linux has a problem with systems with multiple video cards, I tried installing Ubuntu on one yesterday where I had an additional card but no way to disable the built-in card.

It worked fine under Windows XP, but Ubuntu kept selecting the wrong card on install and I had to run dpkg-configure xserver-xorg and manually select the correct video card (using the PCI info I got from Windows properties).

---

### Post by loserboy on 2007-01-26
wait, i'm confused, I thought you said you couldnt get it to do anything with your new monitor, but it sounds to me like video card troubles.

what video card do you have?
i'm guessing a 7 series, if so it sounds like the same problem i had.
there was a bug with the edgy livecd and I dunno if they fixed it or not, but I couldnt get past the livecd splash, it would looked all garbled, i found out that both boot options did the same, it tried to detect your card as "nv" instead of the safe settings.

[https://wiki.ubuntu.com/EdgyKnownIssues](https://wiki.ubuntu.com/EdgyKnownIssues)

look at the 1st one in the list and tell me if it works for you, if not then i dont know what i'm talkin about and i'll shutup

---

