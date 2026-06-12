---
title: "Need a little help configuring my desktop theme"
date: 2008-07-06
forum: General Help
---

### Post by Scrplayr06 on 2008-07-06
Hello all,

I am a noob running Ubuntu 8.04 and am trying to setup my theme.  I have almost everything configured except two things.

1.  How can I make my active windows slightly transparent and my passive windows even more transparent?  I have been using the "Advanced Desktop Effects Settings" and have been unsucessful, except to get my menus slightly transparent.

2.  Also, how can I get my cube to zoom out like I see in the pictures?
    Like this: [http://img201.imageshack.us/img201/9329/mydesktopeo5.jpg](http://img201.imageshack.us/img201/9329/mydesktopeo5.jpg)

Thanks in Advance!!

---

### Post by Watchtow3r on 2008-07-06
make the cube zoom out is under advanced desktop settings--> Rotate Cube--> zoom

---

### Post by Scrplayr06 on 2008-07-06
Ok thanks Watchtow3r that worked perfectly.

---

### Post by isaacj87 on 2008-07-06
> **Scrplayr06 said:**
> 
1.  How can I make my active windows slightly transparent and my passive windows even more transparent?  I have been using the "Advanced Desktop Effects Settings" and have been unsucessful, except to get my menus slightly transparent.

You can achieve this by using the Trailfocus plugin. Go back into "Advanced Desktop Effects Settings" a.k.a CCSM and go to the "Trailfocus" plugin. From there, you can set custom opacity, saturation, and brightness levels for active and passive windows.

Hope that's helpful. :)

---

### Post by sayakb on 2008-07-06
You may also have a sphere instead of a cube.
[ATTACH]76669[/ATTACH]
Goto System->Administration->Software Sources
Click **Third party software** tab and add this: deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) hardy main
Then close the window and press **Reload** when prompted to. You shall be notified by update manager that there is an update for compiz. Install the update and reboot your computer. 
Then goto Advanced desktop effects settings and you will have a **Cube reflection and deformation** plugin there.

---

