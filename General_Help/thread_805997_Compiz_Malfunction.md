---
title: "Compiz Malfunction?"
date: 2008-05-24
forum: General Help
---

### Post by kevo214 on 2008-05-24
I'm running Hardy Heron here and I had to install the restricted video drivers as I'm using an NVIDIA GeForce 7950 Go GTX. When I clicked the use restricted drivers I didn't get the little panel in the System > Administration tab for restricted drivers; however my computer updated and the graphics card now works. I was able to get the graphics working and enable the advanced effects. However now I don't see the compiz panel so I can edit the settings.

I went to the terminal and put in
> compiz
and then it returned
> Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0297 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1920x1200) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.


so what now?

---

### Post by Forlong on 2008-05-24
> /usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
This is not an error but a warning you can safely ignore.
> GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
That's because of a [bug]("https://bugs.launchpad.net/bugs/209207") in Hardy.
Run ```
gconftool-2 -s -t string /apps/compiz/plugins/scale/allscreens/options/initiate_edge Disabled
``` in a terminal to fix it.

---

### Post by kevo214 on 2008-05-24
Thanks a bunch, your other posts also help me realize that I had to install the settings manager 
> 
sudo apt-get install compizconfig-settings-manager

and also enable the universe software repository.

---

