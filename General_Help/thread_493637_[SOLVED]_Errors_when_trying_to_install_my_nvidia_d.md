---
title: "[SOLVED] Errors when trying to install my nvidia driver:"
date: 2007-07-05
forum: General Help
---

### Post by jawinterton on 2007-07-05
I'm getting the following errors while trying to install my nvidia driver:

ERROR: Unable to create '/usr/lib/nvidia/libGL.so.1.2.xlibmesa' for copying (no such file or directory)

ERROR: Unable to restore file '/usr/lib/nvidia/libGL.so.1.2.xlibmesa'

ERROR: Unable to create '/modules/2.6.20-16-generic/volatile/nvidia.ko' (no such file or directory)

What should I do about these errors?? I think that if I can get these errors to go away then I will be able to correctly install the driver and be on way to starting gnome in ubuntu again.  It hasn't worked for over a month and I'm frustrated with the slow response from the nvnews forum.  Any help would be greatly appreciated.

---

### Post by DagMan on 2007-07-06
Depending upon how you are isntalling, the installer may spit things out as errors instead of warnings and still build the driver.  When I use the driver from the NVIDIA site to install there's some messages that I safely ignore however I can't remember specifiaclly what they were, just that the driver module was built successfully.

Try this though
```
sudo mkdir /usr/lib/nvidia/
```and possibly you will also need
```
sudo mkdir /lib/modules/2.6.20-16-generic/volatile/
```Maybe that will help things along.


In the meantime, if that does not work, you can possibly get back into your GUI by typing in 
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
sudo nano /etc/X11/xorg.conf
```
and then finding the section refering to the nvidia card, mine looks like this:
[B] Section "Device"
    Identifier     "nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
    Driver         "nvidia"
EndSection[/B]

and changing the driver part to say nv instead of nvidia like this

[B] Section "Device"
    Identifier     "nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
    Driver         "nv"
EndSection[/B]

Our files will probably differ slightly in that section but don't worry about that.  Just change the one part from nvidia to nv, assuming it's what's keeping you out for now, and if that doesn't work or breaks something, restore the file
```
sudo cp /etc/X11/xorg.conf-backup /etc/X11/xorg.conf
```

---

