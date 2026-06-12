---
title: "Device permissions for camera import wizard"
date: 2007-01-17
forum: General Help
---

### Post by PirateHead on 2007-01-17
When I plug my camera into my computer using a USB connector, it launches a GUI window to import my pictures, which is great. Unfortunately, the GUI window can only access the device if I configure it to gksudo before launching the GUI; and if I do that, then it imports the pictures as root and I have to chown them. How do I automatically make the device readable by my user before launching the GUI?

---

### Post by SoggyCornflake on 2007-01-17
> **PirateHead said:**
> WHow do I automatically make the device readable by my user before launching the GUI?
You could start by bringing up the "Users and Groups" program and verify a setting.

Click on the user you want to have access to the usb camera, and click on the "User Priviledges" tab and verify that "Access external storage devices automatically" is checked.

I'm not sure that would fix the problem, but it's easy to confirm and change if it isn't checked.

---

### Post by PirateHead on 2007-01-17
That box is checked. I have never had trouble automatically accessing USB drives, CD/DVDs, or any other removable media. I only have permissions trouble with the camera. Thanks for the suggestion, shame the obvious answer didn't work. =D

---

### Post by SoggyCornflake on 2007-01-17
> **PirateHead said:**
> That box is checked. I have never had trouble automatically accessing USB drives, CD/DVDs, or any other removable media. I only have permissions trouble with the camera. Thanks for the suggestion, shame the obvious answer didn't work. =D
<Blind shot>Do you suppose that the kernel needs to load a specific module to access the camera? You could see if that's the case by opening a terminal window and typing ```
lsmod
``` After installing the camera repeat the command and see if there's a new module listed.  Assuming there is, then find it and check its permissions.</Blind Shot>

---

### Post by PirateHead on 2007-01-17
I don't know whether a new device is becoming available. I'm having trouble getting lsmod to output to a text file so that I can do diff on them. I tried doing
lsmod | nano
and
lsmod | gedit
and neither of them output anything to the editors! Interestingly enough, doing lsmod | less outputs the text to less just find. Eyeballing the outputs does not make any new device pop out at me.

When I use gksudo to force access to the camera device, it seems to be pointing not to something in /dev, but to something like /org/Hal/usb_device_somelongnum_someothernum

---

### Post by PirateHead on 2007-01-18
Using the Ubuntu Device Manager, I noticed that the kernel is correctly loading whatever modules it needs to and immediately recognizes the device. The device itself is /dev/bus/usb/003/003 or similar. The device is owned by root and is not accessable to the auto-camera-import wizard that pops up to import my photos. The only way I can figure out to let the wizard do its thing is to run it as root, and that is an obviously suboptimal solution. Can anyone who knows more about Linux and Ubuntu in general help me find a better way? With my limited knoweldge, no elegant solution comes to mind.

---

### Post by PirateHead on 2007-03-12
For the benefit of anybody who finds this thread, I resolved the problem. Here's the IRC discussion from #ubuntu that helped me get things working:

<nekr0z>	go to console, plug the camera in and do "lsusb", then look if your camera is detected.
<PirateHead>	lsusb reports my camera and my three empty ports
<nekr0z>	You'll see two hexadecimal numbers separated with ":" aside of your camera, that's camera's ID
<PirateHead>	yup, I see it
<nekr0z>	Now look in /etc/udev/rules.d/45-libgphoto2.rules for a line that contains both those hex numbers.
<nekr0z>	There actually must be 2 lines in that file for each camera.
<PirateHead>	very nice, let me take a look at that
<PirateHead>	still there? it appears that there is no entry for my camera, but I'm not sure
<PirateHead>	is the hexidecimal combo idVendor:idNumber?
<nekr0z>	Yes, exactly. Well, you have to add it manually. Just make 2 lines looking the same as others, only with your camera's numbers.
<PirateHead>	why 2 lines?
<PirateHead>	it seems that all the other cameras have only 1 line.
<nekr0z>	Then restart udev (sudo /etc/init.d/udev restart) and replug the camera.
<nekr0z>	They have 2 lines each on my system, but if one is enough on yours, you can try it this way.
<PirateHead>	on your system, is it one line right after another?
<nekr0z>	Yes, it is. Report in if the solution works, because there's one more bug on this, and I'll guide you through that fix as well.
<PirateHead>	worked perfectly.
<nekr0z>	Then you got my congratulations! Just be aware, there is one more issue on this, and it can emerge on your system after some update.
<nekr0z>	I filed a bug on launchpad, [https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/91250](https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/91250) -- you may check it out to be prepared.
<nekr0z>	The solution is also there.

---

