---
title: "Urgent help needed - Possibly hardware?"
date: 2007-11-18
forum: General Help
---

### Post by tipsqueal on 2007-11-18
My computer has been acting really funny the past few days. First, my computer has been taking way too long to boot up, much longer than normal. At the Ubuntu loading screen it takes about 2-3 minutes to fully boot up the operating system and take me to the login screen. Secondly my computer restarted itself (I think it was a restart not a gnome failure) about 3 times yesterday. I can't say for sure if it was a full restart because every time it happened I was in another room, but I'm currently assuming it was a full restart. 

Now within the past 15 minutes pidgin failed to work. I exited out pidgin, and tried restarting the program but it wouldnt start up, it just started eating up all of my processor usage (42-98%). I decided I was going to restart my computer to see if that would solve the problem and it did not. I even tried just hitting control-alt-backspace to restart gnome but when I would log back in pidgin would still be running and taking up a lot of my processor usage.

On a possibly related note: I have another hard drive in the system that is currently running Windows XP Pro, I use this to play games like Team Fortress, Counterstrike Source, etc. I booted into it to play some TF2 the other day and it restarted then brought me to a screen saying "sorry it didnt load correctly last time, choose how you want to start your operating system" and I chose "Start Windows Normally" and then it worked.

Also, I recently added my Windows Hard Drive to my Grub menu (before I just went into the BIOS and changed the boot order). Other than that I haven't made any system changes.

Does anyone know what the possible problem could be? Any help would be greatly appreciated.

Thanks,
Tipsqueal

[EDIT] I just swapped out both sticks of RAM and neither seem to change the performance. I then restored my original grub boot menu, and unplugged my Windows hard drive and it did not change performance at all. I also tried using a different Ethernet port and re-installing pidgin, but once again nothing has changed. Any help would still be greatly appreciated.
[EDIT#2] I booted the computer with verbose mode, found out there were multiple errors with my USB ports, so I removed my USB Bluetooth adapter and rebooted, and it booted lightning fast. The only problem I have left now is my Pidgin still doesn't work.
[EDIT#3] I ran pidgin as root and it worked, so that led me me to believe there was a problem with one of the files in my home folder so I deleted the ".purple" folder in my home directory and BAM! pidgin works. I still have no idea why this problem occurred in the first place though, so if anyone has any insight please do share.

---

