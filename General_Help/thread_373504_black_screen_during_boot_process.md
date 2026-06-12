---
title: "black screen during boot process"
date: 2007-03-01
forum: General Help
---

### Post by ffxr on 2007-03-01
hi.. i have a minor issue i would like to sort out..

during the boot sequence..  everything goes normally except after the section where it says loading linux kernel, the screen goes disconcertingly black for around 10secs, & then it i get presented with my login screen as normal.. to summarise:

POST -> grub -> loading linux kernel -> BLACK SCREEN for 10secs -> login screen...

also a similar thing happens during the shutdown process, ie the screen goes blank for a few seconds, then it shuts down normally..


i am setting up an AMD64 xubuntu machine at the moment; With my 32bit xubuntu machine, on different hardware.. a little mouse with a wheel around him appears during these 2 'black screen' moments...


my question, what exactly is happening at this point during the boot/shutdown process & does anyone have any idea how to get back the normal screens..?


my new machine's hardware includes a pentium D 820 & NVIDIA 7100gfx.

thanks.

---

### Post by energiya on 2007-03-01
1) Can you use the tty screens? (Alt+Ctrl+F1,2,x)
2) Open the system logs and search for the word "error" or "err" or just look at a boot secvence to see what is wrong.
If you can use the ttys, my gues is that it has something to do with the bootsplash.

---

### Post by ffxr on 2007-03-01
oh i found this:

PCI BIOS BUG: MCFG area at e0000000 is not E820 reserved
PCI Not USing MMConfig
PCI Cannot allocate resources region 9 of bridge 0000:00:06.0
PCI Cannot allocate resources region 9 of bridge 0000:00:07.0



any idea what this means..? no doubt this is my problem...

---

### Post by NBrepresent on 2007-04-08
I have this exact issue. It doesn't really bother me, but I'd still like to know what's going on/fix it.

---

### Post by yves on 2007-04-10
How about trying to add this with your boot parameters : vga=791.
I had this issue and that fixed it. It has to do with the splashscreen that uses a resolution that your video card doesn't support if I remember right !

---

