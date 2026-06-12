---
title: "Nvidia GTX 760"
date: 2014-01-04
forum: General Help
---

### Post by Settori on 2014-01-04
Hello. I have a problem with my Ubuntu. During and after installation any linux have no view on the screen. The problem is when Ubuntu is running on Nvidia GTX760, but on integrated graphic card the view is ok. The newest Ubuntu 13.10 already has a view on graphic card, but the image is bad - cursor is duplicate and ubuntu show error window. I tryed to install drivers from nvidia webpage (ubuntu doesn't show any additional drivers), but every time installation was aborted or screen was black also on integrated card.
Thanks for help and sorry for my English ;)

[COLOR=#000000]GPU - Nvidia GTX 760[/COLOR]
[COLOR=#000000]CPU - Intel Core i5 4570[/COLOR]
[COLOR=#000000]MOBO - Gigabyte GA-H87-HD3[/COLOR]

---

### Post by egeezer on 2014-01-04
You might try installing one of the Nvidia drivers via the Ubuntu option: I believe in 13.10 it can be found in the settings under software and drivers (formerly Additional Drivers).

---

### Post by Settori on 2014-01-04
But there is no additional drivers.

---

### Post by grier-devon on 2014-01-04
You went to the > software & update > additional drivers tab? You should have open source drivers running by default but that is where you need to go to install the proprietary drivers. They should be in there otherwise I would then check your repo list and make sure you have everything checked.

---

### Post by Settori on 2014-01-04
I don't know why, but there is no additional drivers.

---

### Post by grier-devon on 2014-01-04
okay, a little weird, now when you download from nvidia I saw the files are ".run" files, how did you execute? You should have downloaded the correct driver for your series and it should be Linux 64. Then saying it downloaded to your downloads folder you should have....
```
cd ~/Downloads
chmod u+x filename
./filename

if error then

sudo ./filename
```

of course filename is where you type the complete name of the file as it appears in your download folder. If this works then great, though I would still try to find out why it is not showing under "software & update" since I believe it should since that is a supported card.

---

### Post by Settori on 2014-01-04
Yes i downloaded a proper driver from nvidia and installed with turned off lighdm, but after installation screen was black.
I was installing this drivers many times in many ways and tutorials, but after all screen was always black.

---

### Post by efflandt on 2014-01-04
You likely need **nomodeset** kernel boot parameter which is often needed for nvidia drivers and I figured was needed for the dual types of video (instead of default kernel mode setting). I am not even sure if 13.10 install would boot without it, but I may not have waited long enough for hardware discovery the first time I booted install iso on USB stick on a laptop with Intel HD 4600/Nvidia GTX 765M graphics. It is usually best to use Ubuntu packages for nvidia drivers to make sure that everything is coordinated and updated properly, but I forget if I used Software Center or Synaptic to do that (I used nvidia-experimental-310 which is currently a 319 version). Additional Drivers will not come up with anything while running the default Intel graphics.

If you install drivers using a script directly from nvidia might be on your own figuring out how to get everything to work, especially with bumblebee, the X server, and kernel updates.

I had to do some other things to get steam to find 32-bit libs in 64-bit Ubuntu 13.10, and some launch parameters to launch steam games using optirun for nvidia graphics (I just use Intel for steam itself).

---

### Post by Settori on 2014-01-04
Nomodeset doesn't help :(

---

### Post by Settori on 2014-01-05
Any ideas?

---

### Post by Settori on 2014-01-05
Hello! My Ubuntu doesnt show any image from DVI input from GPU, but from input in motherboard (i have integrated gpu in CPU).
MOBO: [COLOR=#006FFD][FONT=Arial]GA-H87-HD3[/FONT][/COLOR]

---

### Post by bapoumba on 2014-01-05
Threads merged.

---

