---
title: "Messed up my resolution in Xubuntu 13.10"
date: 2013-12-03
forum: General Help
---

### Post by I.Bun.Tu on 2013-12-03
I am running Xubunu 13.10 on a Dell Inspiron 1501. I am not sure exactly what caused the issue because my laptop was on for a day or two before I restarted, but I think the only adjustment I made to the system was running

```
xfce4-panel -r
```

in the process of trying to fix my sound indicator, but restarting just fixed it; however when I restarted my resolution set to 1024x768.

I also edited /etc/default/grub to add 'nomodeset' to the > GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" line but I've done that before without issue.

I am not sure what the original resolution was but everything is stretched now (so the proper resolution has a wider pixel format, probably 16x9 I think) and the only other resolution option under Hardware > Display in the Settings Manager is 800x600. 

I would like to avoid reinstalling Xubuntu in order to get my original resolution back. I am using the opensource drivers and have never had any experience reinstalling them (if that's what required in this case). I was thinking maybe deleting/reseting a configuration file, followed by a restart might fix the issue? But I'm not sure which file.

```
marla@dell:~$ lspci | grep VGA
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS482/RS485 [Radeon Xpress 1100/1150]
```

Please let me know if I can provide any more information. Help is appreciated. Thanks.

---

### Post by pbrane on 2013-12-03
It sounds like the only display affecting action you took was adding 'nomodeset' to your grub file. You should remove that and run update-grub again, reboot and see if that fixes it.

You could try renaming your /etc/X11/org.conf file too. Unless you have some special entries in that conf file.

---

### Post by I.Bun.Tu on 2013-12-03
Thanks, removing 'nomodeset' got my resolution back to 1280x800. I hadn't realized that 'nomodeset' was a display affecting action. I used that as suggested here: [http://askubuntu.com/questions/361547/ubuntu-freezes-crash-after-wake-when-upgraded-to-13-10](http://askubuntu.com/questions/361547/ubuntu-freezes-crash-after-wake-when-upgraded-to-13-10)

in order to fix an issue with not being able to wake my laptop after closing the lid. Adding 'nomodeset' fixed the issue, but obviously it screws with my resolution. I should correct myself by saying that I've added the option without issue to Ubuntu installations before but this is my first time really using Xubuntu.

In terms of fixing my waking from suspend issue and maintaining my resolution, do the other options listed in the Ask Ubuntu solution have a possibility of fixing the suspend issue without messing up my resolution (I had asumed that if 'nomodeset' did the trick that the others would only apply to other systems), or should I stick 'nomodeset' back in and try to manually set the resolution to 1280x800 in a configuration file somewhere? Thanks again btw.

Edit: I noticed someone in the Ask Ubuntu post fixed everything by installing proprietary drivers, but that is not an option for me because of the GPU.

---

