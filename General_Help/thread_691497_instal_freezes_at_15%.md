---
title: "instal freezes at 15%"
date: 2008-02-08
forum: General Help
---

### Post by lollebol on 2008-02-08
Hello, ive just bought a new laptop and wanted to try-out wubi on this computer... so i downloaded wubi 8.04 rev398 from the website and installed it.

I have selected ubuntu with a dutch language (cause im dutch myself). Downloading the iso went well and after that i had to reboot. 

When I selected linux-ubuntu in the bootmenu a window came up with installation which freezed at checking filesystem (in dutch) at 15% and i had to reboot my lapt Vista also freezed at startup.

The laptop which i tried to install wubi on is a HP Pavilion TX2000 with Vista Home Premium with a dualcore 2,2 processor, 2GB ram and 250GB HDD.

Is it possible to fix this?

Thanks in Advance

---

### Post by ago on 2008-02-09
Can you pres ctrl + alt+ f2 to get to a console?
If so look at the log using 

cat /var/log/syslog

---

### Post by lollebol on 2008-02-09
Ive rebooted my laptop again and started ubuntu-linux again...
Ubuntu loaded to his interface, and i think thats weird because the setup was incomplete. The interface had an English language while i selected Dutch and there was an install icon on the desktop.

I opened the install program and i saw a new window with 'Choose Regional settings' where i selected Amsterdam.. but when i pressed the 'continue' button it gave the error 'Partman crashed with exit code 10' and the window disapeared .

:edit:
When opening Vista again I went to the Control Panel, uninstal program and Wubi was not in the list,  but was available in the bootloader :confused:

Is there a solution to this problem?

with kind regards,

O. van Egmond

---

### Post by ago on 2008-02-10
> **lollebol said:**
> 
Ubuntu loaded to his interface, and i think thats weird because the setup was incomplete. The interface had an English language while i selected Dutch and there was an install icon on the desktop.
Hmm that's the live CD envirnoment. Not sure how you got there, either the live CD was in the tray, or the automatic installation failed and launched the live CD desktop, or the boot menu is wrong.

> When opening Vista again I went to the Control Panel, uninstal program and Wubi was not in the list,  but was available in the bootloader :confused:
If you do not have an ubuntu folder, you can use EasyBCD to remove the entry.
Wubi should remove itself from the bootloader, and that works on my vista machine.

You may want to retry with a later version and see if you can replicate the above issues. 
I cannot replicate what you say above, if I can replicate, there are good chances I can also fix it.

---

