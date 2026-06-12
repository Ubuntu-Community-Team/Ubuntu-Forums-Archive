---
title: "SD Card problem - wont format, stuck in read only mode"
date: 2012-10-20
forum: General Help
---

### Post by faraz_k86 on 2012-10-20
Hi,

So i plugged my old 16GB microsd card into the card reader and plugged it in.

The icon for it shows up but when I click on it the computer freezes, and it just constantly tries to read the disk. When I unplug the card reader, computer unfreezes and I can use it.

So I thought it must be a partition problem or something so I'll format it with GParted.

I load up GParted and select the memory card, it has a small exclamation mark next to it, indicating some problem. When I selected delete partition and applied it gave me an error, going into details gave me many lines of error saying "disk is in read only mode"

please help me fix this. I dont even want the data back, I just want it to be usable again


Thank you

---

### Post by efflandt on 2012-10-20
What does dmesg say about the microSD card when you insert it (any errors)?

Is the microSD plugged directly into the card reader or in an SD adapter?  In one case I forget if the lock switch on the adapter was loose or slot too tight, but every time I tried to insert the adapter into the SD slot, the lock switch would flip making it read only.

Fortunately I have a different USB card reader that has a microSD slot.

---

### Post by faraz_k86 on 2012-10-21
> **efflandt said:**
> What does dmesg say about the microSD card when you insert it (any errors)?

Is the microSD plugged directly into the card reader or in an SD adapter?  In one case I forget if the lock switch on the adapter was loose or slot too tight, but every time I tried to insert the adapter into the SD slot, the lock switch would flip making it read only.

Fortunately I have a different USB card reader that has a microSD slot.

dmsg?

Im using a card reader that directly takes the microSD, I dont have to put it into an adapter first so that removes the possibility of sd card being locked by switch.

I tried it in Windows as well, the drive for the card reader shows up as I:\ in My Computer but when I click it, it takes forever to load and freezes the computer. When I remove the card reader it returns to normal operation.

Is there any way to salvage this card?

Thanks

---

### Post by varunendra on 2012-10-21
> **faraz_k86 said:**
> dmsg?It is a command that you have to run in the terminal (shortcut to bring up terminal is 'Ctrl+Alt+T'). It gives a very long list of kernel messages that were logged since you booted. You are interested in only the last few messages that were logged when you plugged in the card reader. To limit the output to only last 10 lines you can 'pipe' it to 'tail' command :
```
dmesg | tail
```
It should return the last 10 messages including when the card was detected, and error messages if any.

However, looks like the card is dying, and if the data on it is important, you should try to create an 'image' of it using 'testdisk' (**sudo apt-get install testdisk** command in terminal to install it, then **sudo testdisk** to run it).

But if the data isn't important and you only want to make it reusable, then I don't know anything better than gparted (& I don't know much!). Perhaps look for some 'low-level format' utility in either windows or linux.

---

