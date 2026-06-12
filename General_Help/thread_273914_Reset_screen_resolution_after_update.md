---
title: "Reset screen resolution after update"
date: 2006-10-09
forum: General Help
---

### Post by steve_waters on 2006-10-09
Hi

I ran an update at some stage last week, have been out of the office since then, rebooted today and my resolution has been reset to 600x480 and 60hz. 

Is there an automated tool to ensure Ubuntu picks up all my hardware correctly again, I don't want to edit xorg.conf by hand.

Thanks for your advice in advance

p.s. no I have not installed any new graphics cards or monitors, or anything actually.

---

### Post by steve_waters on 2006-10-09
I have tried this command:

sudo dpkg-reconfigure -phigh xserver-xorg

It said I should get the same screen I got during setup but I got very little, i drop out to a command line and then it automatically goes back to the graphical login screen.

Thanks
Steve

---

### Post by sKuarecircle on 2006-10-09
I am having exactly the same problem.Ran th eupdate today and after boot up my resolution is stuck at 640x480. Any help would be greatly appreciated.

---

### Post by sKuarecircle on 2006-10-09
Ok this makes no sense but it works now. I have my resoltion sback at 1152x864 and I have more options.

I ran

sudo dpkg-reconfigure xerver-xorg

That will open a sort of screen display that allows you to set hardware settings. i did it but cocked up my monitor settings.There is an option to set which resolutions you would like to allow your monitor to display and i unchecked 640x840.The thought behind this was that if it wasn't there in the firstplace and the others were ticked it would have to display my other resolution settings. Alas on boot up Ubuntu promptly and very clearly indicated to me that it wasn't happy with this set up and was not going to boot into my GUI. It booted straight into a terminal. (kinda looks like dos, no graphical interfaces at all) Luckily i wrote down the above code that I mentioned.This time though I changed nothing since it auto detects everything i just flew through everything accepting the settings that Ubuntu had given me...........rebooted and now everything is fine.

Not the most effective way of getting the job done but there you go. Like i say If it ain't broke fix it till it is

---

### Post by steve_waters on 2006-10-11
Ok got mine back as well.

The issue appears to be with the auto detection of my monitor. Perhaps there was an X update and it tried to do an auto monitor detection.

The -phigh paramters are to get dpkg-reconfigure, to do an automated detection of all hardware etc etc.....

I dropped the -phigh and went through the screens manually but it kept falling over at the monitor auto detection, so skipped the auto part of that and was able to finish the reconfiguration and all is well in Ubuntu land again.............

---

