---
title: "Dell Latitude E5570 and Ubuntu linux"
date: 2016-06-11
forum: General Help
---

### Post by Paul_Patton on 2016-06-11
I am investigating buying a new laptop, and am interested in several machines. One is the Dell Latitude E5570.  I want to set it up as a dual boot with Windows 7 and Ubuntu Linux, with the goal of switching over to Ubuntu over time.  How compatible is this machine with Ubuntu?
[http://www.ubuntu.com/certification/hardware/201508-18813/](http://www.ubuntu.com/certification/hardware/201508-18813/)

Canonical lists it as "certified preinstall" but warns that standard images may not run at all.  However, the listing appears to be out of date, since it only lists Ubuntu 14.04 and not the more recent 16.04.  Is it likely to run OK?  Has anybody out there tried it?  How widespread is the problem of Ubuntu not working on machines that are sold with Windows?  Is it something to worry about a lot?  I have also been looking at the Lenovo Thinkpad E560, and at System 76 machines, on which I would run linux with Windows 7 as a virtual machine.  I have seen mixed reviews on System 76 machines.  The idea of a small company that specializes in making machines designed to run Linux seems good but I've seen mixed reviews on their machines, some love them, but many others complain of various technical problems.  I like that System 76 machines accommodate dual drives.  On problem is that I can't check out this machine locally before buying.

---

### Post by dpcole72 on 2016-07-08
I goofed in my previous post regarding model number.  I didn't drink enough coffee today...

Apparently there are issues with AMD drivers with Ubuntu 16.04 and, by default, 16.04 installs with the Intel package -- and not the open source version of AMD (nor is it seen in the device manager I installed)?  I'll get back to that in a moment.

To make sure I had the right laptop with right components for the purchase made, I reinstalled Win10 --   Device manager shows both AMD R7 370 and Intel 530 chips, "enabled" and working correctly.  The latest drivers downloaded from Dell enable switchable graphics.  So mine definitely has the higher end gear installed.

Supposedly, both internal and external GPUs are linked in a way that the AMD is activated dynamically under load.  Which is what I want since my VMWare session will be enabled for hefty graphics use, but for now Ubuntu only installed the Intel driver...

Either way, all that is better than the BIOS revealing *nothing *more than the Intel 530.  I will be reinstalling Ubuntu 16.04 Studio ASAP, also noting this revelation I stumbled on:

[http://news.softpedia.com/news/canonical-recommends-open-source-amdgpu-and-radeon-drivers-for-ubuntu-16-04-lts-501556.shtml](http://news.softpedia.com/news/canonical-recommends-open-source-amdgpu-and-radeon-drivers-for-ubuntu-16-04-lts-501556.shtml)

The article makes me pine for Ubuntu 16.04.1 LTS.  :)

I also updated the BIOS to the latest version (as of 7/8/16) on Dell's website.

Will keep looking at the system, finding the open source drivers, and moving forward.  Sounds like There's a fix in the works, which is super-cool.  Either way, I don't anticipate big problems - most of the installation has been slick and smooth, apart from this video driver scare.

---

### Post by mastablasta on 2016-07-09
> **dpcole72 said:**
>    Device manager shows both AMD R7 370 and Intel 530 chips, "enabled" and working correctly.

Supposedly, both internal and external GPUs are linked in a way that the AMD is activated dynamically under load.  Which is what I want since my VMWare session will be enabled for hefty graphics use, but for now Ubuntu only installed the Intel driver...

Either way, all that is better than the BIOS revealing *nothing *more than the Intel 530.  I will be reinstalling Ubuntu 16.04 Studio ASAP, also noting this revelation I stumbled on:

[http://news.softpedia.com/news/canonical-recommends-open-source-amdgpu-and-radeon-drivers-for-ubuntu-16-04-lts-501556.shtml](http://news.softpedia.com/news/canonical-recommends-open-source-amdgpu-and-radeon-drivers-for-ubuntu-16-04-lts-501556.shtml)

The article makes me pine for Ubuntu 16.04.1 LTS.  :)


i am not sure amdgpu will be made for your chip. it could be i am wrong. in any case you might be better of using 14.04 version which has the option of AMD fglrx drivers. they did support what you are after. however i am not sure the switching was automatical.

---

### Post by dpcole72 on 2016-07-21
> **mastablasta said:**
> i am not sure amdgpu will be made for your chip. it could be i am wrong. in any case you might be better of using 14.04 version which has the option of AMD fglrx drivers. they did support what you are after. however i am not sure the switching was automatical.

Nuts...  I'd hate to have to find 14.04, but if I have to...

I did run terminal commands to upgrade to 16.04.1, then I ran:

[FONT=Courier New][SIZE=2]lspci | grep "AMD"[/SIZE][/FONT]

and the result did find an AMD card, though it was reported as "Radeon 8670A/8670M/8750M [1002:6600] (rev FF)".  Whether that's doublespeak for "M7 370" or a preceding model, it found *something* anyway - for better or worse.

I also ran in the terminal "glxgears" and it popped up in a window with the blue, red, and green gears purring right along very smoothly (~300 frames in 5.0 seconds, 60.01fps).  Whether glxgears is using AMD or the Intel 530HD, I have yet to determine what hardware is the default...

[FONT=Courier New][SIZE=2]lshw -c video[/SIZE][/FONT]

Shows only the Intel HD530, but that's with glxgears not running and glxgears could have used either card I suppose?  I don't recall glxgears existing in 16.04.0, saying "command not found" from the command prompt...

I'll reinstall Vmware next and see if it allows 3D acceleration and what video card it recognizes...

Unsure of the AMD chipset version message found, I did more research:

[https://ubuntuforums.org/showthread.php?t=2331196](https://ubuntuforums.org/showthread.php?t=2331196)

I'll keep holding out and seeing if those open source alternatives mentioned do any good... otherwise I'll find and get v14.04 and update only the apps...

Thanks for your reply and info!

(Oh, information from the link below allows me to use 3D acceleration from the Intel GPU in VMWare...  didn't get the "hw acceleration disabled" error after putting in the parameter.  Until I downgrade to 14.04 for full AMD support or until 16.xx or newer supports the R7 370M again, that won't hurt to use...)

[http://askubuntu.com/questions/537787/enable-3d-hw-acceleration-on-vmware-workstation-10-on-ubuntu-14-04](http://askubuntu.com/questions/537787/enable-3d-hw-acceleration-on-vmware-workstation-10-on-ubuntu-14-04)

Looks like there may be an update to the AMD drivers, a Google search revealed the main page updated a couple of days ago:

[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

[http://support.amd.com/en-us/download/linux](http://support.amd.com/en-us/download/linux)


Will attempt to download and test later today (or using their command prompts)

---

### Post by chrysssl on 2016-10-17
Please tell me that it worked!..

---

