---
title: "I've done it again..."
date: 2007-01-09
forum: General Help
---

### Post by TheNetStrider on 2007-01-09
Well, It's just my luck... Everytime I seem to come right I "break" it... ](*,) 
OK, here's what I've done:
I was busy downloading and installing "Build-Essential" with the "sudo apt-get" command.
I saw the word "completed" but little did I know that it was only complete with the download and not yet with the installation. Just as it began installing (too late to realize), I've already punched the Ctrl+Alt+Bksp keys and FKD-up the whole thing.
Now I can't into Ubuntu.
It gives me an error telling me that if I wasn't logged on for more than 10seconds and see this screen, that I should reboot and fix the problem in "FailSafe" mode.
Could someone please help me fix this. I've downloaded so many stuff already for this installation, that I feel it would be a waste of Bandwidth to Re-Install it.
I have to add that I am a COMPLETE noobe, so I would appreciate a fairly detailed "fig-guide" :rolleyes: 
Thank you!

---

### Post by maniacmusician on 2007-01-09
There's a couple of ways you can do this; Recovery mode, and a Fail-safe session. To access the fail-safe session, do the following:

At the GDM login screen, click on the "options" button on the bottom left (if you're using the default theme) and click on the Select Session option. From there you can select Fail-Safe Gnome and Fail-Safe Terminal. 

To access recovery mode, you have to reboot your computer. When it says "Loading GRUB menu" (it's only for a couple of seconds), you have to press Esc. From the menu that shows up, select the one that has "recovery mode" in parentheses.

Either way, you should reach a Terminal in the end. The command you're looking for to fix this is: > sudo dpkg --configure -a . Now that's just from memory, but I'm 90% sure that will work for you.

Hope it works out.

---

