---
title: "Kernel null pointer dereference"
date: 2008-04-08
forum: General Help
---

### Post by wh33t on 2008-04-08
K, first off. I think my laptop may be broken. But I can't pinpoint what is broken about it. Read my whole post please before responding with anything.

So this laptop used to be a windows XP machine. It worked fine. One day I turn it on and I notice the touchpad and keyboard are responsive... I hold the power button for a few seconds to turn it off and it doesn't work. So I pull the plug and it's battery. Turn it back on, and same thing... So I'm thinking Windows is doing something screwy, who knows right? My girlfriend is a computer noob so there is telling what she may have done, although she claims nothing.

I format the drive and begin the reinstall of Windows, and the touchpad continues to become unresponsive randomly through out the install, I hook up an external mouse and the same thing happens. Weird thing is though, it doesn't appear to be a system freeze becaues I can still see the silly windows animations happening, there just doesn't appear to be any way to communicate to the machine.

So I'm like bah! Windows is borked, bring on the linux. And similar things happen. I have tried many different distro's the latest being Fluxbuntu. It managed to install, but it won't launch any programs. Logging in with the shell spits me out the error message

```
BUG Unable to handle kernel NULL pointer dereference at virtual address 000000001
```

Any ideas what is wrong with my laptop? I presume this is what is causing what ever problem it is, and it seems to happen randomly at any given time. Sometimes I can boot to the distro, others it just hangs during boot. HELP PLZ!

---

### Post by danwood76 on 2008-04-08
Try running the memory test available from the grub boot menu.
run it for a few hours to be sure.

Faulty memory can cause all sorts of issues like you are describing, though normally it will just crash your system entirely.

---

### Post by wh33t on 2008-04-08
Omg, I hope it's just the MEMORY! Will go do that now! thank you!

---

### Post by wh33t on 2008-04-08
Ok the memtest was taking too long (although I am now running it again and will let it finish), so I swapped each memory chip out in turn and tried to do something and I got the same error message. So either both memory chips are messed up or the motherboard is.

Any other suggestions or explanations? I also tried to do a software reset in my bios (load set up defaults) which didn't help. Also removed the harddrive and tried to load a live cd, same problem.

Any help would be great! I'm about ready to smash the thing into pieces!

---

