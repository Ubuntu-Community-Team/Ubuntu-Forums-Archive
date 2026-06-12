---
title: "problems setting up graphics drivers"
date: 2008-02-14
forum: General Help
---

### Post by fiddle_sticks on 2008-02-14
Hey i just installed ubuntu for the first time yesterday, ive got everything working just fine except my nvidia grafics driver.

everything works fine whilst running under the default nv driver but when i install the nvidia driver and restart my resolution is 800x600 and the driver is set to vesa. no matter what i do i can change the driver, i had to replace my backup of xorg.conf to get back to my nv driver setup.

linux picks up my card( 7900gt) without any hassle, but not my screen (samsung syncmaster 740bf)

i used envy to install the drivers.

any help would be appreciated, im new to linux so be nice.

---

### Post by danwood76 on 2008-02-14
You can install the Nvidia GFX drivers through the restricted drivers manager (System -> Administration -> Restricted Drivers Manager)
that will install the drivers correctly and setup your Xorg.

---

### Post by fiddle_sticks on 2008-02-14
no, ive already tried

when i log out and back in my driver has been set to vesa and i have to revert back to my old xorg.conf file.

---

### Post by danwood76 on 2008-02-14
Well if you need to setup your xorg you can do:
```

sudo nvidia-xconfig

```

That will set it up correctly.

---

### Post by fiddle_sticks on 2008-02-14
ok but i dont understand why i cant use the nvidia driver, at all, as soon as i select it and reboot it changes to vesa. i dont know what i should be setting up in xorg?

---

### Post by danwood76 on 2008-02-14
The xorg needs a few extra things like glx modules being loaded.
Try using the nvidia config script.

If the drivers still dont load I would have thought you havent installed the drivers correctly.

---

### Post by fiddle_sticks on 2008-02-14
ok when i try that i get this messsage and then nothing happens:

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

repeating the command does the same thing. im pretty sure i downloaded the driver correctly, and i used envy to do it initially so im stumped.

---

### Post by danwood76 on 2008-02-14
Did you reboot after?
The xorg conf file only loads when the xserver loads.

If it makes no difference I would look at installing the drivers manually from the nvidia site.

---

### Post by fiddle_sticks on 2008-02-14
I did reboot after, still nothing. busy downloading the driver from nvidia now. will see if that works.

---

### Post by fiddle_sticks on 2008-02-14
ok i installed the driver from the .run package without a problem, when i restart it just does what its always been doing. 

Just before the login screen i get a message saying:

"ubuntu is running in low graphics mode" 

it shows my monitor as plug and play and i am running of vesa driver. 

so am still in the same position as when i started...

---

### Post by fiddle_sticks on 2008-02-14
ok i managed to get the nv driver working properly, but i still cant ust the nvidia driver any ideas?

---

### Post by fiddle_sticks on 2008-02-15
ok its fixed, all it was was that my graphics card power wasnt pluged in properly....

---

