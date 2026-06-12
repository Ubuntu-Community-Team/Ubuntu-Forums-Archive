---
title: "Bluetooth keyboard not staying connected"
date: 2007-10-15
forum: General Help
---

### Post by aliencam on 2007-10-15
SUMMARY:  bluetooth keyboard does not work in gutsy when i "wake up" the display that was automatically turned off by moving the mouse.  this worked in feisty. 




FULL PROBLEM: 


I upgraded from Ubuntu Feisty to Gutsy.  I have the Logitech Bluetooth MX Desktop, which is a keyboard, mouse, and "media pad" (glorified numpad) 

The mouse and keyboard worked perfectly in Feisty, using the guide here: [https://help.ubuntu.com/community/BluetoothSetup?highlight=%28bluetooth%29]("https://help.ubuntu.com/community/BluetoothSetup?highlight=%28bluetooth%29")
to connect my bluetooth devices on startup.  they worked perfectly. 

Now, when the computer is idle for a long time ( I have it set to turn off the monitor after 40 minutes),   the keyboard does not work.  The mouse works, but that is probably because of the "on/off" switch on the mouse, when I leave the computer I turn off the mouse to charge it, and the keyboard stays on indefinitely.   when I come back, I turn on the mouse, wiggle it to "wake up" the monitor, and the mouse works perfectly but they keyboard does not.  

The keyboard will not "wake up" the computer, or do anything after I get the display back on with the mouse.  what I have to do is go into the terminal and, using the "on-screen keyboard" that I enabled just in case, type in ```
sudo hidd --search
```

that line re-searches for my keyboard and finds it.  my right-clicking on the bluetooth icon in the taskbar I cannot do a "search for bluetooth devices" or anything like that, and sometimes it ses the keyboard, but displays it as disconnected and when I click on it to connect it, it says it cannot find the device. 

while using the on-screen keyboard to type in "sudo hidd --search" is not impossible, because of my extremely long and complicated password, it takes me forever to type it in, and makes it a big pain...

---

### Post by Nadim on 2008-03-16
Ever find a solution for this, Aliencam?  I just finished setting up my Rocketfish bluetooth keyboard/mouse with Gutsy, and am having the exact same problem.  It seems that the "normal" mechanism for re-establishing communication on startup or wakeup isn't working...with the mouse, you can fix it by turning it off / on, but the keyboard doesn't have a power switch, and removing and re-inserting batteries every time you want to get a connection  is extremely annoying.

Surely there must be a better way...anyone know it?

---

### Post by thinkdez on 2008-03-17
I have a Logitech Bluetooth MX Desktop and it does have an on and off switch on the bottom of the keyboard.  Having turned this off and on does it not find the keyboard again?  I can't say that this will work for sure as I am having other issues with my keyboard in bluetooth mode.

---

### Post by aliencam on 2008-03-17
the logitech keyboard i have does not have an on/off switch, only the mouse does, and the way I could prevent it from "loosing" the mouse was to switch off the mouse every time before i walk away, then when i switch the mouse back on it would connect, but the keyboard would be gone. 

no i never found a solution to this, but i got a laptop since then so it's not an issue for me anymore... (lol i know that doesn't help anyone else)  sorry.

---

