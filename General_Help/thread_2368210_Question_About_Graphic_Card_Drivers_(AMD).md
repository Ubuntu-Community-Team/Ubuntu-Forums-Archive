---
title: "Question About Graphic Card Drivers (AMD)"
date: 2017-08-08
forum: General Help
---

### Post by vilixz2 on 2017-08-08
Basically im ive been trying out a few games on steam with Ubuntu and im noticed im unable to run a few games due to outdated opengl or other errors. Now im running a AMD R9 280 graphics card and im using the Radeon graphics driver, so my question is if i downloaded the AMD 15.12 propriety drivers and installed them considering they are old i believe, would i benifit more from it or should i stick with Radeon drivers? many thanks

---

### Post by mastablasta on 2017-08-08
> **vilixz2 said:**
> Basically im ive been trying out a few games on steam with Ubuntu and im noticed im unable to run a few games due to outdated opengl or other errors. Now im running a AMD R9 280 graphics card and im using the Radeon graphics driver, so my question is if i downloaded the AMD 15.12 propriety drivers and installed them considering they are old i believe, would i benifit more from it or should i stick with Radeon drivers? many thanks

which ubuntu version? on 16.04 and higher you should install & use AMDGPU (or rather use latest kernel - maybe even 17.04).

on 14.04 you can install catalyst (not sure if it supports the chip) but you need to be using 14.04, not for example 14.04.2

---

### Post by vilixz2 on 2017-08-08
well im using the latest and the drivers on amd website goes up to ubuntu 15 so its a fair bit out but im guessing installing that would be a bad idea

---

### Post by mastablasta on 2017-08-08
read about it more here: [https://help.ubuntu.com/community/AMDGPU-Driver](https://help.ubuntu.com/community/AMDGPU-Driver)

and i think that with that card you can use amdgpu pro: [http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx](http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx)

---

