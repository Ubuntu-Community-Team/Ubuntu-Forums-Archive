---
title: "Question about WINE"
date: 2017-08-06
forum: General Help
---

### Post by warmango on 2017-08-06
Okay so here is the deal, i have a dualboot of windows10 and ubuntu17. i have wine on the ubuntu and was curious if i could direct where it gets its files from its VirtualDrive to the windows partition? that way i can load my programs esayer


also, could i run the windows partion in a virtual machine?

---

### Post by vocx on 2017-08-06
> **warmango said:**
> Okay so here is the deal, i have a dualboot of windows10 and ubuntu17. i have wine on the ubuntu and was curious if i could direct where it gets its files from its VirtualDrive to the windows partition? that way i can load my programs esayer

also, could i run the windows partion in a virtual machine?
I don't think you can direct the Wine program to look for the Windows files in the other partition. I mean, you can set up symbolic links, and that may be a way of doing it somehow, but I don't think it would work ideally.

I think what you can do is copy the structure of some programs from your Windows partition to the Wine folder in Ubuntu, which is normally located in "/home/user/.wine/drive_c"
This is, install a program in Windows, and copy the files to the Linux partition. Of course, this would duplicate the installation; you'd have one copy in Windows and another one in Linux.

I think Wine needs to emulate other parts of the Windows environment such as the registry, so using this method, copying the file structure, may not always result in a workable program under Wine. Remember that Wine is a compatibility layer providing certain emulation of Windows, but it probably won't be able to run complicated programs that require the entire Windows environment.

The second question about running the Windows partition in a Virtual machine is a no. You cannot do that. A virtual machine is an entirely fake environment, so connecting to a real installed Windows partition like that would be quite the feat. I am certain somebody with more knowledge than me can prove me wrong, but I'd say for the general user, this is not possible.

I think it would be possible to take a Windows installation, then convert it to a single image file, "windows.img", and then emulate that image. So, you would see the same environment in your virtual machine. However, any further changes would be done on the virtual image, and not on the original partition.

Truth is that if you really need Windows programs, you should use Windows to run them, or look for free-software alternatives so you can transition away from Windows.

Using a virtual machine would be your best solution, I think. You can install it in Ubuntu, with a virtual Windows in it. Or, if you use Windows more, you can do the opposite. Install a virtual Ubuntu in your Windows environment.

---

### Post by leunam12 on 2017-08-07
About the first question: I don't see why not, first you have to make sure that hibernation is disabled in windows, you will not be able to mount the drive in Read-write mode if it's hibernated. The second thing that you have to do is make sure that the program that you want to run in WINE actually installs and runs without problems, check the winehq website, any;thing that is not gold or platinum is going to have problems. If you can meet those two requirements, then all you have to do is run winecfg and map one of the drives to point to your windows partition.

---

### Post by Bucky Ball on 2017-08-07
It is a different question than the one you're asking here, but yes, you can run Windows as a virtual machine. Running Windows as a virtual machine would avoid the need to use WINE. 

If you have further questions about virtualisation, you should probably edit the question from here and start a new thread in 'Virtualisation'. Gets confusing asking two questions in one thread and avoided around here. ;)

---

