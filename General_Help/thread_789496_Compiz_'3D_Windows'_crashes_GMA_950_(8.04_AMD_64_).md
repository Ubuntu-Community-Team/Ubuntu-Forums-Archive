---
title: "Compiz '3D Windows' crashes GMA 950 (8.04 AMD 64 )"
date: 2008-05-10
forum: General Help
---

### Post by homersapiens on 2008-05-10
On my Biostar Core 2 Duo system with Intel GMA 950 integrated graphics controller, if the Compiz '3D Windows' effect is enabled AND any application is running AND that application's window is showing on the desktop, then the system will crash and return to the login screen if I attempt to rotate the cube (via Control + Alt + mouse move). Other Compiz cube features seem to work okay (rotating without 3D Windows enabled, Cube Reflection, Cube Caps, etc.)

Anyone else seeing this problem with the GMA 950? Any suggestions/workarounds?

I'm running Ubuntu 8.04 LTS Alternate AMD 64.

---

### Post by SNW24Linux on 2008-05-15
I'm having the same problem with ubuntu 64 bit version with an intel 945G 256 MB. Everything works except for the 3D windows plugin.

Can somebody help us please? :confused:

---

### Post by riseringseeker on 2008-05-27
> **SNW24Linux said:**
> I'm having the same problem with ubuntu 64 bit version with an intel 945G 256 MB. Everything works except for the 3D windows plugin.

Can somebody help us please? :confused:

I have a System76 Darter Ultra that I am having a similar problem with.  Whenever I try to rotate the cube with a window open on the desktop it crashes before I can even see a cube.

I've played with this a bit, and I wonder, if you do NOT have any applications open, or all minimized, does the cube work for you?  It does here.  

I have added to a minimal bug report, perhaps you should as well.

[https://bugs.launchpad.net/ubuntu/+source/compiz-fusion-plugins-main/+bug/140497](https://bugs.launchpad.net/ubuntu/+source/compiz-fusion-plugins-main/+bug/140497)

No one will fix it if there aren't complaints/

---

### Post by willyboy666 on 2008-08-21
same here
 intel gma 950 +3d windows= crash

---

### Post by Ihaveaproblem on 2008-08-26
Same problem. Ubuntu 8.04 64bit on acer travelmate 4230 core 2 duo, Intel GMA 950 integrated graphics controller!
Compiz work fine. Cube option too. But if I select "3D Windows" option, ubuntu (I think server X) crashs and after few seconds linux go to the login graphic window like after boot strap!
Some idea?

---

### Post by beyondthegraves on 2008-09-23
I have the same problem -- if 3d windows is enabled, rotating the cube using mouse buttons causes 64 bit Ubuntu (Hardy) to crash, taking me back to the login screen. Using Intel Core2 Duo, Integrated Intel Graphics Media Accelerator 3100 on G33 chipset. If 3d windows isn't enabled, everything else seems to work fine.

---

### Post by ss2man44 on 2008-10-18
The bug happens to me, too. I'm using 64Bit Intrepid on a Dell XPS M1210 with the Intel integrated graphics.

---

### Post by houdodu on 2008-11-01
same. 64bit intrepid and integrated intel gfx. been this way for a while, was hoping it was magically fixed with the upgrade.

---

