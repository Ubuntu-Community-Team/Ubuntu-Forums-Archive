---
title: "Graphics Driver Unknown!"
date: 2013-04-08
forum: General Help
---

### Post by Ashfaqur Rahman on 2013-04-08
In the " About This Computer Section "
About computer graphics its saying
" Driver Unknown "
" Experience Standard "

Is that mean that my computer cant find graphics card?
I have Around 1400MB on board AGP.
What can i do now?

---

### Post by cortman on 2013-04-08
You can select "Additional Drivers" in the Dash, and install a driver if it suggests it.

---

### Post by Ashfaqur Rahman on 2013-04-08
Cant find anything named " Additional Drivers " in the Dash!

---

### Post by cortman on 2013-04-08
Then try searching for Jockey.

---

### Post by bogan on 2013-04-08
Hi!,
If using 12.10, Right-Click on the Desktop>'Change desktop Background'>'All Settings>System>Software Sources>Additional Drivers Tab.

Before 12.10, Open System Settings,select Additional Drivers.

Chao!, **bogan**.

---

### Post by Frogs Hair on 2013-04-08
Just like previous versios the propietary driver uses its own setting and will appear as unknown in details.

---

### Post by gifford on 2013-04-08
As Frogs Hair indicated, even with proprietary drivers, the driver will appear as unknown and the experience standard. This is normal.

---

### Post by Ashfaqur Rahman on 2013-04-08
Cant find anything named jockey! @cortman

In the Additional Driver Tab Found Nothing! @bogan

Then how can I be sure that I have my Graphics Driver? @Frogs Hair

---

### Post by QIII on 2013-04-08
Hello!

Which version of Ubuntu are you using and what is the OEM/Model of the card?

Thanks.

---

### Post by kuifje09 on 2013-04-08
May this help a bit ...

cat /etc/*rel*           for ubuntu version
lspci | grep -i vga    for the vga video card

---

### Post by Ashfaqur Rahman on 2013-04-08
I am using Ubuntu 12.10 .Actually I don't know my video card model @QIII

Cant understand your code! @ kuifje09

---

### Post by QIII on 2013-04-08
Paste the following in the terminal and post back the results.

```
lspci | grep -i vga
```

Thanks.  We need to know the OEM and model of your GPU to help much more.

---

### Post by kuifje09 on 2013-04-08
And for the release of ubuntu```
cat /etc/*rele* 
```

---

### Post by Ashfaqur Rahman on 2013-04-08
Typing the code it replied "00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)" @QIII

Thanks understood! @**[COLOR=#000000]kuifje09[/COLOR]**

---

### Post by kuifje09 on 2013-04-08
Thats a intel core machine with buid-in graphics.  HD400/2500  
I am not sure if it is in the repos, but at the intel site you can find drivers if needed:

[URL="https://01.org/linuxgraphics/downloads"]https://01.org/linuxgraphics/downloads 
[/URL]
Check with your os-release !

( I have no experience with installing intel drivers )

---

### Post by Mark Phelps on 2013-04-08
> **Ashfaqur Rahman said:**
> Cant find anything named jockey! @cortman

In the Additional Driver Tab Found Nothing! @bogan

Then how can I be sure that I have my Graphics Driver? @Frogs Hair
If you're seeing a desktop, not a command line text screen -- then the graphics drivers are installed and working -- and there is nothing else to be done.

---

### Post by kuifje09 on 2013-04-08
Nothing to be done ... depends on if he is satisfied with the resolution.
Also I think intel is rather good supported.
On my Dell D440 I had nothing special to do.
(VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device)

---

