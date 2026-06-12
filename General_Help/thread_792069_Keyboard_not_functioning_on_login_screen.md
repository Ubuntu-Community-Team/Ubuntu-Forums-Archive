---
title: "Keyboard not functioning on login screen"
date: 2008-05-12
forum: General Help
---

### Post by purnama on 2008-05-12
Hallo,

I'm using Hardy Heron for about 2 weeks now, i tried to solve the problem by looking and searching on the internet, but the result didnt help me to resolve the problem.

im using an english version of Hardy heron with german keyboard. the keyboard functioning properly. but SOMETIMES i can't use my keyboard at the login screen.

i use ubuntu together with windows, so i have a grub loader where i can choose whether i use ubuntu or windows. my keyboard still functioning from the start to grub loader, but as i'm in login screen, it not functioning anymore.

i tried 4 different german keyboards, usb and ps/2 keyboards, but the result was still the same. i read a thread about disabling the   usb legacy support in bios, but that didnt help either.
if i disable the usb legacy support, then i cant use the usb keyboard to choose ubuntu at grub loader (i make windows as default os). using ps/2 keyboard with usb legacy support disabled is not solving the problem.

as i said this problem appear SOMETIMES. but if it do appear, i cant do anything, i could restart my pc or go to safe mode and hoping that the problem would solved itself. sometimes when i restart my pc twice than its gone, but sometimes i restarted it xx times, and its still there, and i don't find any thread that help me further in resolving this problem.

please help thank you

---

### Post by TheBuzzer on 2008-05-16
> **purnama said:**
> Hallo,

I'm using Hardy Heron for about 2 weeks now, i tried to solve the problem by looking and searching on the internet, but the result didnt help me to resolve the problem.

im using an english version of Hardy heron with german keyboard. the keyboard functioning properly. but SOMETIMES i can't use my keyboard at the login screen.

i use ubuntu together with windows, so i have a grub loader where i can choose whether i use ubuntu or windows. my keyboard still functioning from the start to grub loader, but as i'm in login screen, it not functioning anymore.

i tried 4 different german keyboards, usb and ps/2 keyboards, but the result was still the same. i read a thread about disabling the   usb legacy support in bios, but that didnt help either.
if i disable the usb legacy support, then i cant use the usb keyboard to choose ubuntu at grub loader (i make windows as default os). using ps/2 keyboard with usb legacy support disabled is not solving the problem.

as i said this problem appear SOMETIMES. but if it do appear, i cant do anything, i could restart my pc or go to safe mode and hoping that the problem would solved itself. sometimes when i restart my pc twice than its gone, but sometimes i restarted it xx times, and its still there, and i don't find any thread that help me further in resolving this problem.

please help thank you

Hi!

I got the same problem, I was unable to enter my username and the CAPS chars worked.

You should boot in recovery and go in /etc/X11/ directory to edit the file xorg.conf and go to the language line in Input Device Section and put the language you want. Try "uk" or "us" if you have qwerty keyboard.

Section "InputDevice"
        Option          "XkbLayout"     "uk"


Marc

---

