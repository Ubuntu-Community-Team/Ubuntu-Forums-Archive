---
title: "ubuntu wont start after envy install"
date: 2007-05-06
forum: General Help
---

### Post by StephanEriksen on 2007-05-06
After I installed envy (i do not know if it was the right verson), my pc wont start (my ubuntu disk). I get some error messages saying that xServer cant be started plus some other things. I believe it has something to do with the nVidia driver.

When my PC fails to start ubuntu it starts, whats it called.. the dos-like-thing where i can type commands. If anyone could help me with this problem i would be great full! 

Thanks in advance

(I also have another problem, how can i get ubuntu to run in 1080p resolution?)

---

### Post by StephanEriksen on 2007-05-06
Doesnt anyone know how to fix this problem?

---

### Post by sammao on 2007-05-07
cd into 

/etc/X11/

sudo nano xorg.conf

Im not sure but here you suld change the nvidia to nv some thing lite use driver "nvidia" change to "nv"

Then download the latest envy and install again. When you have installed envy. 
type in the terminal

sudo envy

to install it.

Search for 1080p click ubuntu = 1080p ? something

---

### Post by StephanEriksen on 2007-05-11
I finally got ubuntu to work again. Now I only need to find out how i can change the screen res. Ubuntu wont let me set it to any higher than 1280x720. I need either 1920x1080 or 1440x900. If someone could help me with this it would be great! I have indeed searched the forums for info, I found something, but I didnt manage to fix the problem.

---

### Post by rax_m on 2007-05-11
I believe that if your correct video drivers are installed the resolution should be set correctly (but I'm no expert ;)

I have used envy to install my drivers and it works well. Though the first time I tried to install the "Envy nvidia" driver over the one I already had installed. In this case my Xserver also failed to start.
But luckily envy has a text based mode where you can uninstall and reinstall stuff from. So maybe give it a go again.. 

Rax

---

### Post by StephanEriksen on 2007-05-12
The same thing happened to me. I have now installed the nVidia driver several times, but the resolution problem is still there. My video card (geforce 7800GS) detects my screen as a 1280x720 screen, and not a 1080p screen. When i try any other screen the same thing happens. Do anyone know of any terminal commands i can use to fix the problem? I think i need to manually set the native resolution of my screen in ubuntu.

thanks for any and all help!

---

