---
title: "Low screen resolution"
date: 2008-04-27
forum: General Help
---

### Post by celticninja on 2008-04-27
Well I recently switched over to Xubuntu, and after I installed the drivers for my graphics card, my screen resolution went down, and when i go to change it in the options the only choices are *default* and *320X240*. I know it isn't the graphics card bc any other Linux distro lets me change the resolution and it acts fine. So what I am asking is, What do i have to change so that I can a higher resolution? Because  this low resolution is somewhat annoying.

---

### Post by oldsoundguy on 2008-04-27
you most likely have the generic drivers and need to install the specific drivers for your video setup.  Not knowing WHAT that is, very hard to garner a response.

---

### Post by celticninja on 2008-04-27
Oh yea, well its a nVidia 6100, and well i did use generic drivers. The first time i installed the drivers i used Envy, and it did the same thing. I am also using the 8.04 64bit version, with a AMD Athlon 64 4000+

---

### Post by lovecrime on 2008-04-27
Applications >other >Screens and Graphics

then choose your monitor model 
this should solve the problem

if you can't find Screens and Graphics
edit menus by right click on menu bar and add it

---

### Post by danwood76 on 2008-04-27
assuming envy installed the driver correctly run this from the terminal:
```

sudo nvidia-settings

```

this will bring up the nvidia config panel where you should be able to sort it out.

---

### Post by Reg Editor on 2008-04-27
After a lot of effort I was finally able to get more resolution options by using this guide

[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by celticninja on 2008-04-27
Well, i have it fixed. While i had the drivers installed before with Envy, and with the low resolution, i uninstalled the drivers and when i reinstalled them, it gave me the option to choose the drivers.

So basically reinstalling the drivers did it :), but thanks anyway everyone!

---

