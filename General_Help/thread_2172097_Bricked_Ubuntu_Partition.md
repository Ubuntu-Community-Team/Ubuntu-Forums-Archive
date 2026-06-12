---
title: "Bricked Ubuntu Partition"
date: 2013-09-03
forum: General Help
---

### Post by leond2 on 2013-09-03
Dear All,

It's been a while, I was last on here in 2007 (forgotten/lost/denied old username...just remove the 2!) when I'd first started experimenting with Ubuntu, I've recently come back to the OS when I was given an old Thinkpad R61 which was set up as Win 7/Ubuntu dual boot system.

It was working beautifully and Ubuntu was a lot smoother on this machine than Win 7...I was happy.

I'm currently working as part of an R&D team and as such I've been trying to get a Thermoteknix Miricle 307 thermal imaging camera to work under Linux in the hope I could run it from Raspberry Pi and send it up in the air.  Some dude from Nasa sent one to the moon and wrote the Linux install guide, however, I was having trouble, mainly with (from what I can tell) the communication between the device and the UVCvideo driver which apparently supports this hardware.

In my blind fumbling around and attempt to get things to play nicely, I believe, that in the process of installing V4L media package I've inadvertently wiped all of the old drivers and relocated them to my desktop enviro in Ubuntu...which now boots but with zero interface. I've booted in safe mode and loaded into terminal under root, attempting to remove the folder and files via terminal but I'm getting a denied access read access only.

Is there anyway I can recover from this?!!!

Cheers,

Leon

---

### Post by grahammechanical on 2013-09-03
Are you sure that you have identified the fault correctly? Please explain what you mean by "zero interface." Do you get a log in screen? Do you get a desktop but without Unity? What version of Ubuntu are you using? We get issues like this one when there is a kernel update and/or a proprietary video driver is buggy.

If you can get to a working desktop you can open Additional Drivers and experiment with the video drivers listed there. From the Grub boot menu we can select Recovery Mode>Resume and that may load to a working desktop using an open source video driver.

Regards.

---

### Post by leond2 on 2013-09-03
Thanks for coming back to me.

I'm running 12.04 LTS (if the latter acronym is correct).

OK, I get the boot loader, whereby I can choose either normal, safe or boot to an earlier version.  Of these three only safe boot works, whereby I can access the system via root.  If I try to boot as normal, via the safe graphical mode (from the menu in safe boot) or into a previous version I then get cast into a realm of black screens and nothing else, no mouse, no cursor, nada (no GUI, no terminal).  Just before this happened, and after I'd fiddled around adding the V4L media package, whenever I tried to restart the computer, it essentially just logged me out and took me to the login window without shutting down, I then shutdown from the command line and then this happened, I believe, I was up to date on the software side of things.

Before I'd messed about with V4L and tried to re-install the UVC driver, I was getting FATAL: responses when running sudo modprobe uvcvideo (or uvc) which indicated to me that along the way I'd moved/removed/killed it in some way, hence my trying to re-install.

I can't get into a working desktop, like I say, I can get into root via safe boot, but I have noticed a couple of times that I'm only getting read only access from here.

Cheers,

Leon

---

### Post by leond2 on 2013-09-16
This can be closed.  I've done a clean install...couldn't fix it.

---

