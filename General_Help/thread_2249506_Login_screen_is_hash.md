---
title: "Login screen is hash"
date: 2014-10-22
forum: General Help
---

### Post by bubblefish on 2014-10-22
I upgraded to Ubuntu 14.04 several months ago. The upgrade went well, except right from the get-go, when I start up, I get a screen that says Kubuntu, whereas I have always been running Ubuntu, and computer info shows Trusty Tahr 14.04. After that, I get a log-in screen that is very mixed up. There is something like half letters in the middle of the screen, which must be my username, because when I hit "enter" and type my password, I see a series of circles with wedges cut out, and then the regular home page boots up beautifully. I can continue to work with this if I have to, but it bothers me that the startup pages are crappy. I'm wondering if downloading an image of Ubuntu 14.04 and re-installing would be my only option. Would that trash all my files and programs? I could save all my documents and pictures on a DVD, but I'd rather find out how to fix it.

---

### Post by DogMatix on 2014-10-22
Do you have the Kubuntu desktop installed too?

---

### Post by bubblefish on 2014-10-22
> **DogMatix said:**
> Do you have the Kubuntu desktop installed too?

I don't know. I have some K programs, like K Mymoney installed. I must have the K desktop. I never knowingly opted for Kubuntu as my OS.

---

### Post by bubblefish on 2014-10-22
Actually, I use the Unity by default

---

### Post by DogMatix on 2014-10-22
Is there an option to use a Kubuntu session at login?

You might try reinstalling lightdm.

---

### Post by bubblefish on 2014-10-22
[QUOTE=DogMatix;13149566]Is there an option to use a Kubuntu session at login?

You might try reinstalling lightdm.[/Q

 In Grub I have the option of starting Ubuntu or Mint. When I choose Ubuntu, it loads a screen saying "Kubuntu" then the hashed up log-in screen. I'll try lightdm.

---

### Post by bubblefish on 2014-10-22
That didn't do it. I might add, when I click "log out" under the system menu, I get a very nice (monochrome) log-in screen, which has "Ubuntu" at the bottom.

---

### Post by bubblefish on 2014-10-23
Found this in Synaptic, under "Grub gfxpayload blacklist: The 'set gfxpayload=keep' facility in GRUB provides smooth graphical
handover to the Linux kernel.  Unfortunately, this does not work on all
systems, resulting in a black or corrupt display.  This package provides a
blacklist of PCI IDs which fail."
I'm wondering if a re-install would trash my files in home?

---

