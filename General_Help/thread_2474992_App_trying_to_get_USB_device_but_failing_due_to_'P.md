---
title: "App trying to get USB device but failing due to 'Premission deniad'"
date: 2022-05-13
forum: General Help
---

### Post by annonannon on 2022-05-13
Hi, this is my first time working with linux, so assume you are speaking to retarded monkey. I'm trying to develop a simple app that will to stuff when reciving DMX signal. I found a framework/application that does just the thing i need (OLA: [https://wiki.openlighting.org/index.php/Open_Lighting_Architecture](https://wiki.openlighting.org/index.php/Open_Lighting_Architecture)), but i have one problem. When running the OLA app and plug the device that it is supposed to work with to the USB port i get cryptic 'Premission deniad' error as shown in the following image. 

The device in question is: 
[https://wiki.openlighting.org/index.php/DMX_USB_Pro](https://wiki.openlighting.org/index.php/DMX_USB_Pro)


After reaching for help in the OLA community i was told that i probably need to add this udev rule: 
[https://wiki.openlighting.org/index.php/OLA_Device_Specific_Configuration#Linux.2C_FTDI](https://wiki.openlighting.org/index.php/OLA_Device_Specific_Configuration#Linux.2C_FTDI)


I did it with touch and nano commands, i dont know if i was supposed to do it like that. But after doing it nothing changed.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290440&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=290441&stc=1[/IMG]

---

### Post by yancek on 2022-05-13
The first line in the first image you posted shows you ran the command (can't actually read what it is?) as a normal user.  Try prefacing it with sudo to get root permissions.

I'm not familiar with the software but all the instances of software "disabled" is likely a problem.  Changing a udev rule will likely require sudo also.

---

### Post by annonannon on 2022-05-13
First line says "olad -l 3", its to fire up OLA deamon. The feature of this software is that it refuses to run as a root so i cant write sudo before it.

The instances of diabled are not a problem, those are plugins in the software that allow it to comunnicate with devices of the different producers. The last line is for USB Serial plugin that is supposed to work with Enttec device i have. 

Yes, i needed sudo with nano to write udev rule, otherwise it wouldn't let me write it. I'm not sure if the rule itself is correct, i copy&pasted it from the wiki and have no idea what it means.

---

### Post by annonannon on 2022-05-13
[COLOR=#000000][FONT=Verdana]i was able to narrow the problem.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]I went into /dev directory and changed ttyUSB0 file's permissions with chmod 777 command. After that the app and device started to work togather![/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]However, new problem is that after rebooting the PC and also after unpluging and pluging the device, the file is removed and created again with the same old permissions. How do i set up the system so each time i plug the usb device in it has sufficient permissions?[/FONT][/COLOR]

---

### Post by annonannon on 2022-05-13
i needed to add user to a dialout group with [FONT=Verdana, Arial, Helvetica, sans-serif][COLOR=#000000]"[/COLOR][/FONT][COLOR=#000000][FONT=Verdana]sudo usermod -a -G dialout username" command. The problem has been resolved.[/FONT][/COLOR]

---

### Post by GhX6GZMB on 2022-05-13
/dev contains devices. You know, hardware. Of course it will revert to the original settings.
"Everything in UNIX is a file". Burn this statement into everything you do.

Do not fiddle with permissions on directories and files, they are generally exactly as they should be.
Working with Users and Groups makes sense.

---

