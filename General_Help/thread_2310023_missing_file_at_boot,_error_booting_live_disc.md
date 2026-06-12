---
title: "missing file at boot, error booting live disc"
date: 2016-01-15
forum: General Help
---

### Post by gandhi2 on 2016-01-15
hi all

i'm having issues with one of my computers.....

during the boot process.... its says "missing terminal.mod file" then...

goes to "grub rescue>"

sooo i did some research online... and found the you might be able to fix the problem with a LIVE CD....BUT

when i load the live cd i get this message "bootloader /ca: not found".... i've tried 2 disc and i'm not sure where to go next!?

any help would be appreciated

thank you

Gandhi

---

### Post by gandhi2 on 2016-01-22
anyone know anything??? someone must of had issues installing on a new system??? please help?? thank you

---

### Post by Seanan on 2016-01-22
Was this error during or right after installation?

---

### Post by gandhi2 on 2016-01-22
the live CD didn't even boot.... the error appears while the cd is loading... i've tried 2 cds and the same error appears

---

### Post by Nuno_Abreu on 2016-01-22
Do you use EFI? If so, try to disable "**EFI Secure Boot**" or something similar on the BIOS and try again.

Tell me the results.

---

### Post by gandhi2 on 2016-01-22
i don't think the computer is recent enough to have that......its an old xp machine.... can't even boot from usb

---

### Post by Nuno_Abreu on 2016-01-22
I see.
If you're booting from a CD/DVD drive, I understand the problem - my experience in burning Linux distros in CDs have always been bad. Have you ever heard of Plop? You could burn this to any CD-ROM and then try to make a bootable flash drive and boot from there. Here's the website:
[https://www.plop.at/en/ploplinux/index.html](https://www.plop.at/en/ploplinux/index.html)

---

### Post by gandhi2 on 2016-01-22
sorry to sound stupid....but i'm sure exactly what i'm download.... could you please point me in the right direction as there seems to be alot of options on the Plop site...am i suppose to download the ISO here [https://www.plop.at/en/ploplinux/downloads/live.html](https://www.plop.at/en/ploplinux/downloads/live.html) .....and what happens from there... i boot that disc first and enable usb boot??.... then boot from usb (i've done that before :) )

thank you soooooo much for your help!!!!

---

### Post by Nuno_Abreu on 2016-01-23
No, it's okay that you ask - and you do it well.
Actually, you better download the zip file right on the website:
[https://www.plop.at/en/bootmanager/download.html](https://www.plop.at/en/bootmanager/download.html)


Then, burn the ISO file inside it (there are others tools, but you only need this one and a burning tool) and choose to boot from USB (there is an option for it).

If you still have doubts don't hesitate.

---

