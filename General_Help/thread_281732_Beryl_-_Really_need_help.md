---
title: "Beryl - Really need help"
date: 2006-10-21
forum: General Help
---

### Post by s_h_a_d_o_w_s on 2006-10-21
I have tried to get beryl running for about two weeks now and i have failed countless times. Here are my specs (i'm 13 but here's what i know) :)

-dapper
-ati
-amd sempron 2300+ (if it matters)

Not sure if you need any more info. I have tried many guides and every time I get the ubsod (ubuntu blue screen of death) because apparetly X broke. I ahve reinstalled 7 times. I follow every instruction to the dot but X breaks eah time. I installed the ati driver and glxinfo shows direct rendering is working. I add repos, apt-get update, etc. Why is this so hard? I just want bouncy windows, and a 3d cube. Does anyone have similar specs and was succesfull in getting beryl running? If so which guide should i try? 

Thanks

EDIT: This will be a fresh install, nothing changed.

---

### Post by s_h_a_d_o_w_s on 2006-10-21
I login to beryl/xg session and after 10 seconds a message appeears saying its  takin too long. Is there a way to give it more time?

---

### Post by klato on 2006-10-23
> **s_h_a_d_o_w_s said:**
> I login to beryl/xg session and after 10 seconds a message appeears saying its  takin too long. Is there a way to give it more time?

I also get this message when trying to login to an xgl session.

---

### Post by wolf202 on 2006-10-23
you need to be very exact with ati hardware use this tutorial to install the ati drivers

[http://www.wikitut.org/index.php?title=How_to_Install_ATI_Graphics_Card_Drivers_under_Linux](http://www.wikitut.org/index.php?title=How_to_Install_ATI_Graphics_Card_Drivers_under_Linux)

and then follow this beryl/XGL tutorial and it will work.

[http://www.wikitut.org/index.php?title=How_to_Install_XGL/Beryl_on_GNOME_with_ATI_Hardware](http://www.wikitut.org/index.php?title=How_to_Install_XGL/Beryl_on_GNOME_with_ATI_Hardware)

good luck.

-wolf

---

### Post by thieves.honor on 2006-10-23
Here is what I have used to get both the ATI driver installed and Beryl to work.  I'm running a Dell Inspiron with a X300 card and have Dapper installed.

Use method 2 here [Link]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")

Here is how I installed XGL/Beryl [Link]("http://wiki.cchtml.com/index.php/XGL-Ubuntu")

---

### Post by Tobster on 2006-10-23
I know it hard but it might be worth just waiting until Thursday when the amazing Ubuntu is updated to 6.10  because I been told XGL (that what your trying to install) comes with the new Ubuntu release.

I dont really know about the hardware side.  However if your computer is quite new say under 4 years old it should not be a problem.

Hardware (the inside of your computer) really does not go out of date - I mean it really takes years and years so even if it older then 4 years it still prob will be o.k

Im having sleepless night too and im 29! just cant wait until Thursday :)

---

### Post by Tobster on 2006-10-23
I just like to add for a 13 year old you sound really smart, really clever :)

---

### Post by s_h_a_d_o_w_s on 2006-10-25
Thanks, i tried wolf202 first link but i tried method 1and now X broke. In the output it says it using xorg.conf then it sayd no screeens found. What part ofthat first method messed with my xorg? How can i restore it? Plz i had all my files. I'll try other way on my second hard drive if i ca get this fixed. appreciate the help.

---

### Post by s_h_a_d_o_w_s on 2006-10-25
NVM Guys i just rmved xorg.conf and replaced it with xorg.conf.origianl and renamed it to xorg.conf and it booted in! Now i'll try the second method wolf02.

---

### Post by CarpKing on 2006-10-25
BTW- I do not believe Edgy (6.10) will come with XGL.  It will, however, have AIGLX (a different way to use Beryl, depending on your hardware and drivers) integrated into X.org.

---

### Post by s_h_a_d_o_w_s on 2006-10-25
But will this ease the installatoin of beryl withmy ati?

---

