---
title: "how to use old laptop with closed lid (screen is broken)"
date: 2018-03-31
forum: General Help
---

### Post by matrooswolf on 2018-03-31
Hi,

I have an old laptop with a broken screen. I recently installed Ubuntu 17.10. I have attached a screen (vga) and a wireless keyboard and mouse and everything works fine. I have selected the vga screen as the primary screen, but I cannot turn of the broken screen, and when I close the lid, the vga screen goes dark. I suppose the laptop goes in suspend mode. But... I turned suspend off (in gnome-tweaks energy suspend when close lid).

I also read somewhere that you could turn off the screen completely, but I don't see a button to that effect in settings/screens. I can see both screens, choose the vga as my primary screen, but there is no option to disable the build in screen...

Anybody any suggestions how I could use the laptop with the lid closed?

---

### Post by TheFu on 2018-03-31
For many laptops, heat management requires the laptop lid to be open.  It gets really hot under there. 

In the /etc/systemd/login.conf file, there are controls for how the lid impacts the running system.  I think you'll always need it open, a little, to boot, but after that, you can close it.

As for turning off the display, any of the *randr tools should let you control it for X/Windows.  I haven't any clue for Wayland. Sorry.  **lxrandr**, arandr, are a few simple GUIs.

---

### Post by HermanAB on 2018-04-01
You could open the thing and cut the power wires to the display and lid switch. You could also repair it - there are shops in Singapore and Hong Kong that sell generic laptop parts.

---

### Post by TheFu on 2018-04-01
> **HermanAB said:**
> You could open the thing and cut the power wires to the display and lid switch. You could also repair it - there are shops in Singapore and Hong Kong that sell generic laptop parts.

Replacing a laptop screen is one of the easier things, assuming it is the screen and not the GPU at fault. Replaced the screen on an Acer for $29. Took about 15min because I was going really slow.  Someone who does it all the time could do it in 3 min.

---

### Post by matrooswolf on 2018-04-03
Hi TheFu,

Do you know which settings I should change in etc/systemd/login.conf? This is what I have.
```
[Login]
#NAutoVTs=6
#ReserveVT=6
#KillUserProcesses=no
#KillOnlyUsers=
#KillExcludeUsers=root
#InhibitDelayMaxSec=5
#HandlePowerKey=poweroff
#HandleSuspendKey=suspend
#HandleHibernateKey=hibernate
#HandleLidSwitch=suspend
#HandleLidSwitchDocked=ignore
#PowerKeyIgnoreInhibited=no
#SuspendKeyIgnoreInhibited=no
#HibernateKeyIgnoreInhibited=no
#LidSwitchIgnoreInhibited=yes
#HoldoffTimeoutSec=30s
#IdleAction=ignore
#IdleActionSec=30min
#RuntimeDirectorySize=10%
#RemoveIPC=yes
#InhibitorsMax=8192
#SessionsMax=8192
#UserTasksMax=33%
```

And thanks for the suggestion of replacing the screen. But the computer is an old computer from the US. I live in Belgium. In Belgium having someone look at the screen and saying 'I can't fix it' would already cost 50 euro, I think ;)

---

### Post by TheFu on 2018-04-03
ebay and amazon usually have the screens. Doesn't matter where in the world you are. 

YOU doing the replacement yourself would be 15 min. Tonnes of youtube how-to videos. Screens are all almost the same. 

**man logind.conf** as details about the settings in the logind.conf file.

---

### Post by HermanAB on 2018-04-03
I can attest to this as well.  I have repaired multiple laptop screens and backlights.  The main gotcha is that you have to go and buy a set of funny screwdrivers to disassemble the thing and get the part numbers before you can order the parts online, but getting the screen parts and installing them, is *not* a problem.  It just requires a bit of patience.

---

### Post by matrooswolf on 2018-05-02
Hi everybody,

I disassembled the screen and reassembled it, which was indeed easier then I thought, and lo! it works (for the moment), so I think it was only a bad connection.

I tried too look for a replacement screen, but couldn't find one (in Europe), as it is an old model (compaq presario c700), and I was wondering if you could replace a laptop screen with just any other screen, or if you had to have a specific one. Just a question...

---

### Post by HermanAB on 2018-05-02
You'll have to disassemble it, remove the screen to get the real manufacturer and model number printed on it, then search for that with Google.

---

