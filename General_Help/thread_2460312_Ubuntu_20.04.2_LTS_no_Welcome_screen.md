---
title: "Ubuntu 20.04.2 LTS no Welcome screen"
date: 2021-04-07
forum: General Help
---

### Post by lumaja2 on 2021-04-07
Download the above Ubuntu and certified on booting from USB ISO there is no Welcome screen.
 How to fix these
 Thank you

---

### Post by Rex Bouwense on 2021-04-08
Have you checked the hash of the download?
Have you changed the boot order in the BIOS/UEFI so the USB flash drive is first to boot?
What happens when you try to boot?  In other words what if anything does your computer boot to?

---

### Post by ActionParsnip on 2021-04-08
What do you see instead of the "welcome screen"?

---

### Post by lumaja2 on 2021-04-09
Have checked the hash it was OK
 Changed the boot order to USB flas drive and it booted from this drive.
 Booting from ISO USB is normal with Ubuntu sign on the bottom then the screen
 opens with the cat sign on the middle ant black To Bar with date and the normal
 icons on the right after afew seconds the screen goes blank and Ubuntu sign on the
 bottom comes up and stays like that until switch off the computer.
 The working  HDD that i intend to install the new Ubuntu as Ubuntu older version 16.04 LTS
 as these come to end these month I wanted to install the latest version

---

### Post by CatKiller on 2021-04-09
> **lumaja2 said:**
> the screen
 opens with the cat sign on the middle ant black To Bar with date and the normal
 icons on the right after afew seconds the screen goes blank and Ubuntu sign on the
 bottom comes up and stays like that until switch off the computer.
*Technically* you could log in again (I *think* the username is "ubuntu" and the password is blank) but then you'd experience exactly the same symptom.

So from your description, your graphical session is crashing. Then, when the session restarts, you end up back on the login screen, since that's the first thing that happens when a session starts. So you're looking at things like graphics drivers as the cause of your problem.

There was a thread recently where their computer didn't with with the default X session for some reason, but *did* work with a Wayland session (which will be the default in 21.04, and future versions if the test goes well), so you could try Wayland (which you can select from the login screen) to see if it helps. 

You could also try one of the other flavours to see if it's a Gnome-specific issue. 

Otherwise, it's providing details of your graphics hardware and looking through your logs to see where the problem lies.

---

### Post by lumaja on 2021-04-14
This details are made from Ubuntu 16.04 my working Ubuntu.

luis@luis-H81M-DS2:~$ lspci -v | grep VGA -A 1
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06) (prog-if 00 [VGA controller])
    Subsystem: ASRock Incorporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
luis@luis-H81M-DS2:~$

---

### Post by Dennis N on 2021-04-14
> **lumaja2 said:**
> Download the above Ubuntu and certified on booting from USB ISO there is no Welcome screen.
 How to fix these
 Thank you
In Ubuntu MATE 20.04 the welcome application is only available as a snap package.
It would not be present on the ISO. When you do the actual install to your computer it probably will get pulled in, since I see it on mine in the snap list, and I don't recall installing it.
You can manually install it if necessary:
```
snap install ubuntu-mate-welcome --classic
```

---

