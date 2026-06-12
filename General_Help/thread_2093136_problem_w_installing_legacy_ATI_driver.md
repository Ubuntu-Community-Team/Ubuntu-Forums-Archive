---
title: "problem w/ installing legacy ATI driver?"
date: 2012-12-10
forum: General Help
---

### Post by lightsaberlesbian on 2012-12-10
I have an ATI Radeon x1300 pro.  I tried to install the legacy driver but received this error in terminal (link to driver here: [http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English):](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English):)
> 
Created directory fglrx-install.5AceB2
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:3.2.0-34-generic-pae; make sure that the version is being
correctly set by --iscurrentdistro

Does anyone know what's going on?

The only thing I can think of is that I installed a 32 bit version of 12.04 Ubuntu

---

### Post by Bucky Ball on 2012-12-10
Possible. Is this a fresh install? If so, have you gotten updates and checked in 'Additional Drivers'? You shouldn't need to manually install anything unless you have a specific reason.

I use Xubuntu so not sure but does Ubuntu still have 'System Monitor'? I think that will tell you if you have 32bit or 64.

PS: You have marked this thread as 'solved' ... is it? If so, could you let us know what went on? It may help another user down the track. If not, could you mark it as unsolved to increase your chances of getting help? ;)

---

### Post by lightsaberlesbian on 2012-12-10
this isn't a fresh install. i checked additional drivers and didn't see anything. i just find that when I go to the Activities menu from Gnome shell the animation is really stupidly slow.  I thought installing the proprietary driver might help things.  Not really sure if that's the case.

---

### Post by lightsaberlesbian on 2012-12-10
accidental reply

---

### Post by Cheesemill on 2012-12-10
That driver won't work with 12.04, it's too old.

You are already using radeon (the open-source driver) which is the only option available for Ubuntu with your card.

---

### Post by Mark Phelps on 2012-12-10
AMD dropped Linux driver support for that card years ago -- when they relegated it to Legacy status.  The latest Ubuntu version that will work with that driver is 8.10.  More recent Ubuntu versions use upgraded versions of the X-Server that will not work with that driver.  There are no newer AMD Linux drivers that will work, either.

---

### Post by coldraven on 2012-12-10
> **Mark Phelps said:**
> AMD dropped Linux driver support for that card years ago -- when they relegated it to Legacy status.  The latest Ubuntu version that will work with that driver is 8.10.  More recent Ubuntu versions use upgraded versions of the X-Server that will not work with that driver.  There are no newer AMD Linux drivers that will work, either.
  Mark is correct. My laptop has the X1250 card, the last distribution that worked reasonably well was 10.10 and the framerate was too slow for gaming but worked with the compiz cube etc.
Now I cannot run 12.04 with Unity so I'm using Kubuntu 12.04 with the 3D effects switched off .

---

