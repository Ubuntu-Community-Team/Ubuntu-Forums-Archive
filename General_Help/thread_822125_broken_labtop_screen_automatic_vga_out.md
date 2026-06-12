---
title: "broken labtop screen automatic vga out"
date: 2008-06-07
forum: General Help
---

### Post by toulvus on 2008-06-07
So i have a labtop but the screen is broken so when i coulkd just barley see one of the sides in windows i changed it to use the vga out and an external screen, worked well but now i want ubuntu i got a disk booted off it and nothing would appear on the external screen using the vga port. is there any way i can have the install disk go to the vga port and not the broken labtop screen and ubuntu also if i can manage to install it the labtop is a compaq v300z

EDIT: windows is installed right now and it works fine using the external moniter and i mean i need ubuntu to use the external display also not just the installer

---

### Post by toulvus on 2008-06-07
bump

---

### Post by SirPerigrin on 2008-06-08
You shouldn't be having any issues at all, i just installed on an HP laptop with similar situation (Busted screen and DVD-Drive) and i own a v3000z which also doesent have any problems using external by default when connected... have you tried telling BIOS to direct to the VGA? (Hint: Fn + F4)

---

### Post by toulvus on 2008-06-08
i cant get to the bios cuase like the bios are going through the labtop screen and its broken. Like i start up my computer and the compaq logo and stuff would all be going to the broken screen the first thing that i see on the external screen when i boot up is the windows login screen. If i got into the bios from the compaq startup screen would they go throgh the external moniter?

---

### Post by tom66 on 2008-06-08
On my Dell there is some text on the F keys. Mine has Fn + F8 for external video. Look for something like that on your laptop.

---

### Post by toulvus on 2008-06-08
mashing fn+f4 repedately during startup worked now im looking around the live cd thanks guys

---

### Post by tom66 on 2008-06-08
No problem, enjoy.

---

### Post by toulvus on 2008-06-08
ok this is bad the livecd worked through the external moniter then i installed and mashing fn+f4 doesnt do anything. so its going through the laptop screen but thats broken so i see nothing so now the computer is useless unless maybe the live cd worked with fn+f4 so i could get into that anc change xorg.conf?? please i need help that computer waas expensive and i dont want a 1000 dollar paperweight

---

### Post by tom66 on 2008-06-08
So you were able to get the VGA working through the setup, but it won't work after booting. 

If so, make sure the cable is plugged in from boot. Is it possible to use another computer to access the computer over the network, e.g. VNC viewer? Connect to your computer from another computer through the network using Remote Desktop Viewer. Then you can set up multiple monitors, etc.

---

### Post by toulvus on 2008-06-08
can you set that up without seeing anything?


eidt: i forgot its not connected to the internet


edit (again): i can boot into the live cd so i can see the contents of my hard drive and ther has to be a way to change settings with just the hard drive

---

### Post by the8thstar on 2008-06-08
Hey **Toulvus**, I don't want to lecture you or anything, but could you please make an effort on punctuating your sentences correctly? Your posts are VERY hard to read.

Thanks man.

---

### Post by toulvus on 2008-06-08
Oh, sorry. Anyway according to sites you have to press fn f4 when grub appears, but that doesnt work. I can still access the hard drive through the live cd so i can edit any files there. Someone please help this is really starting to piss me off.

---

### Post by toulvus on 2008-06-08
C'mon guys this is URGENT. I'm a DJ and i need the computer for an event TOMMOROW. Someone please help!

---

### Post by the8thstar on 2008-06-08
Have you tried the following: 

1. Plugging the monitor cable into the VGA port of your laptop
2. Reboot Ubuntu
3. Don't touch the Fn+F4

... what happens then? Black screen?

I know that on my config (see below) the VGA port will work natively and Ubuntu will display on BOTH monitors after the login screen. Tell me about your config a bit.

---

### Post by toulvus on 2008-06-08
just a blank screen. i have a compag v3000z and a 1024x768 monitor

---

### Post by toulvus on 2008-06-08
Well, I had to cancel on the event tommorow my boss said it was the last straw, I was laid off. And guess what? rents due on thursday Am i gonna have enough money to pay? no. So thats itbecause of ubuntu i was laid off and my landlady has a three strikes your out policy and i used two last year and ive been pretty good since then but now im not so im getting evicted. so thats it homeless and jobless because of ubuntu thanks just thanks

---

### Post by the8thstar on 2008-06-13
Sorry we couldn't help, but I think you're being dishonest. In your  first post you said your screen was broken. If you wanted your computer to work normally, you coould have done the following:

1. bought a new computer
2. brought yours for repair
3. gone to an Internet cafe (successful, cheap solution too!)
4. gone to your workplace (maybe there was at least one computer available)

Eventually your bad judgment is your own fault. You can't expect Ubuntu to help you resurrect a computer. If the hardware is broken, FIX it.

---

