---
title: "Enabling hibernation in Gnome"
date: 2015-08-17
forum: General Help
---

### Post by Robbyx on 2015-08-17
Having followed the advice in various messages  I have hibernation working via the command line, but not via logout. No button to hibernate on exit  appears  there.

Would the reason be the total mem is greater than the swap even though the amount used is much less?
```

robins@robins-desktop:~$ free
               total       used     free     shared    buffers   cached
Mem:      15253092    2641924   12611168       3268      95876    1586508
-/+ buffers/cache:     959540   14293552
Swap:      8499196          0    8499196
robins@robins-desktop:~$ 
```

---

### Post by jim_deadlock on 2015-08-17
When you click the logout icon and you get the dropdown dialog, press your Alt key and the power logo will change to a pause logo, not sure if it's suspend or hibernate though.

---

### Post by Robbyx on 2015-08-17
> **jim_deadlock said:**
> When you click the logout icon and you get the dropdown dialog, press your Alt key and the power logo will change to a pause logo, not sure if it's suspend or hibernate though.

I thought that was marvelous. Tested it and the computer restarted with no loss. Then i realised that I could not access the internet. I found the network connection was off and I switched it on. No difference: still did not work. I could not close the machine down and tried to do it via the terminal, but there were problems droping into the terminal via one of the Alt Ctrl -F2 to F6. I had to turn off the machine and do a soft boot. 

What do you think is the cause of all that?

---

### Post by jim_deadlock on 2015-08-17
I think it's normal for the network to go off during suspend, not sure why it didn't come back on though. I usually do ctrl-alt-F1 to get tty, then ctrl-alt-F7 to get the desktop back.

---

### Post by oldfred on 2015-08-18
Have you timed boot vs. reload from hibernation.

I always found full Ubuntu boot was so fast that hibernation saved little if any time.

My new system with SSD, I had to change UEFI fast boot to a 3 second delay so I could get into UEFI, set grub to a 3 sec delay so I could get into grub menu if needed. 
Today new kernel came down. It took about 6 sec to shutdown, the 6 sec for UEFI & grub and about 6 sec to boot from grub to working system or less than 20 sec total to reboot.

---

### Post by Robbyx on 2015-08-18
I agree with you. Booting is now very fast with SSD and a modern MB. I wanted to hibernate because I had started to use the workspace option. I had a load of different programs and files in each workspace. I did not want to reboot and not be sure to recover them from memory and notes. 

Hibernate for me is a mess. Not only is the network permantly out of action until I hard reboot, but I can not send a command from the terminal to reboot if I had previously tried to hibernate. The modem manager is failing to shut down on exit. 

Incidentally, how do you get the grub options? I want to run fsck on my root and home partitions.   I have tried shift and it does not cause the grub options to appear. 

I am using an AMD64 version of UbuntuGnome.

---

### Post by oldfred on 2015-08-18
Shift should work if you have BIOS, but you usually have to hold it until grub menu appears.

With my new UEFI, I have to use escape, but it does not always seem to work. Or  sometimes one press works, other times multiple presses are required. Something about where in UEFI, grub loading that escape is pressed & then remembered.

---

