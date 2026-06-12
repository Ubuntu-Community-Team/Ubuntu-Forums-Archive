---
title: "GFX Drivers"
date: 2012-11-08
forum: General Help
---

### Post by Kirkkaf90 on 2012-11-08
Hi all,

I have just recently moved to Linux after using Windows for more than 15 years. After checking my system details it appears Ubuntu doesn't know what type of graphics card my machine has. 

After checking the AMD website here: [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English) it appears there is a Linux version of my drivers and software. I have downloaded the file but being new to Linux have no idea how to install it as it appears to be source code if I am not mistaken? 

Thank you for your assistance in advance. 

Kirk.

---

### Post by mabittenc on 2012-11-08
Hi Kirkkaf90,
  Could you post your video card model?


[]("http://ubuntuforums.org/member.php?u=1753456")

---

### Post by Kirkkaf90 on 2012-11-08
Sure its nothing special - ATI Radeon™ HD 5450. 

I just need to know how to install the drivers for it.

---

### Post by Kirkkaf90 on 2012-11-08
Anyone provide any instructions on how to install the driver located at the link above?

Thanks.

---

### Post by dannyboy79 on 2012-11-08
here's some thorough directions

[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

---

### Post by grahammechanical on 2012-11-08
> After checking my system details it appears Ubuntu doesn't know what type of graphics card my machine has.

This bug has been around for a while. I had that on my machine for about a year. Sometimes, when I use the open source driver I see information on the Details page about my video card. Sometimes not. Even then it always lists my experience as standard.

It means that the Details dialog is not fully working. It does not mean that you do not have the correct video driver installed.

When you installed Ubuntu did you tick the box to give permission to install third party software? If so, then Ubuntu installed the proprietary video driver for your hardware. If you did not tick that box then you are using the open source Nouveau video driver.

You can go to System Settings>Additional Drivers and activate a proprietary driver from there. I am assuming that you are using Ubuntu 12.04 as you do not say which version of Ubuntu you are using.

With Ubuntu you should not need to download files from the Nvidia site.

Regards.

---

### Post by Mark Phelps on 2012-11-08
Unless you really need hardware acceleration for 3D video game performance or fan management due to GPU overheating, you don't really NEED the AMD drivers.  

Also, if you're running UBuntu 12.10, then do NOT force the installation of the AMD drivers.  Folks are reporting LOTS of problems with these at present.

IF you're running Ubuntu 12.04, and you see a desktop, the Radeon drivers are already installed.  SO basically, you don't really need to do anything.

---

