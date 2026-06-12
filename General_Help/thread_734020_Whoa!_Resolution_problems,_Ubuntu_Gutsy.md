---
title: "Whoa! Resolution problems, Ubuntu Gutsy"
date: 2008-03-24
forum: General Help
---

### Post by Cptnrodent on 2008-03-24
Ok, so this seems a bit weird to me. 
I'm running Ubuntu Gutsy on my desktop, equipped with a nVidia 8800 gtx and Samsung SyncMaster 206bw, native res of 1680x1200.  I'm using the latest nVidia restricted drivers.  I'm also using the Compiz desktop effects package.  
When I went to bed last night, everything was perfect...Ubuntu humming along with all the above components in great form, at the native resolution.  When I rebooted my machine this morning, the resolution had been arbitrarily set to 1440x900, and options greater than that resolution were nowhere to be found in the drop down list.  I tried changing the default monitor to the Samsung 206bw, then selecting 1680x1200.  That didn't do anything.  No effects, nada.  
So...besides a clean install of Ubuntu/graphics drivers, anything that might help?

Thanks

---

### Post by Therion on 2008-03-24
It sounds like you just need to edit your menu.lst file...
```
sudo gedit /boot/grub/menu.lst
```
Just tab through, accepting the default settings, until you come to the section that allows you to adjust your monitor settings.  I suggest you select three resolutions, bearing in mind the HIGHEST RESOLUTION you choose in that menu will be your new default.  Save, Overwrite, Exit... You should be good to go.

---

