---
title: "How can I install windows with Linux?"
date: 2006-12-31
forum: General Help
---

### Post by thenetduck on 2006-12-31
Hi, 
  I have had Ubuntu Linux installed on my machine for while now and love it to death, but I would like to play some games that just don't work very well being emulated with wine. Is there anyway to somehow dual boot windows with my linux machine without erasing all of my data on my linux machine? Also I want GRUB to pick it up properly. Thank you, 
  The Net Duck

---

### Post by Hendrixski on 2006-12-31
I hear that this is problematic, because the default behavior for Windows is to format the drive.  Though I think that there is a way to set it not to do that.  Also, if you can avoid the default partitioner, avoid it. Use a third party tool... like Qparted.

The option that many people use is VMWare.  This is a virtualization program, meaning you can run two operating systems at once through it.  It's easy to use once you get over the learning curve.  Download it for free at VMWare.com (it's free as in free beer, not as in "free speech" which is what we're all about... If you want a free virtualizer you can use Xen), and then install windows into a new Virtual Machine.  There is a performance hit from doing this, so I don't know if it's good for games. But it's perfect for business!

I hope that helps a little.

---

### Post by aysiu on 2006-12-31
Once you install Windows, the boot loader will be overwritten, and you won't be able to boot into Ubuntu any more.

You can use the "rescue an installation" option off the Alternate CD to reinstall Grub to the MBR, and then your dual boot will work again.

---

### Post by Hendrixski on 2006-12-31
Aysiu, is there perhaps a project that focuses on a way of installing Windows without it messing up GRUB?  I mean, I imagine that it can't be too hard to install an ISO image into a partition using a liveCD, perhaps even with BartPE??

This would be helpful to all of us who dual boot, and have to put up with the short half-life of Windows in a production environment (we re-image about every 6 months on average at my office).

---

### Post by thenetduck on 2006-12-31
> **aysiu said:**
> Once you install Windows, the boot loader will be overwritten, and you won't be able to boot into Ubuntu any more.

You can use the "rescue an installation" option off the Alternate CD to reinstall Grub to the MBR, and then your dual boot will work again.

All my data will still be on my Ubuntu drive still? Also, I am going to back up my information on my Ubuntu partition, is there a recommended backup program? Thanks,
 The Net Duck

---

### Post by meng on 2006-12-31
Yes you will not lose your Ubuntu data (unless you do something quite insanely stupid, and it would have to be an error of commission, not omission).

---

### Post by thenetduck on 2006-12-31
Ok so I used Gparted Live CD to resize my 80gb hard drive to a 50 gb on the Ubuntu partition and 20gb on the Windows partition with around 3 gigs for swap. My ubuntu OS still works fine, but when I put the windows cd in, it goes into the blue screen as normal,  then goes into a black screen then nothing happens. I'm not sure what this is, but when I resized my hard drive, I set the parition that the Windows was going to be on as "Unformatted". Could that be the reason? I am a little confused on why windows won't install normally. Maybe I resized in the wrong direction? Any input would be usful for me thanks,
 The Net Duck

---

### Post by Ziggy72 on 2006-12-31
Why don't you follow Hendrixski's suggestion of installing VMWare server and then installing Windows? I don't play games and so I don't know how games will perform on that kind of Windows installation but every other Windows program I've used with VMWare server as a Ubuntu guest works beautifully with no apparent loss of performance. Just don't overload the installation with programs you don't need. VMWare server plus Windows also has the advantage that you don't need to dual boot to access the Windows installation.

You will find all the information you need to install VMWare server and setup Windows at
[http://www.ubuntuforums.org/showthread.php?t=296668](http://www.ubuntuforums.org/showthread.php?t=296668)

If performance isn't satisfactory, you can always remove VMWare and suss out carefully how to dual boot. Dual booting is used by heaps of Ubuntu users (including me at present). The only thing I really would suggest is that before you embark on dual booting you should save your MBR just in case something goes wrong and you need to recover. I hope this helps...

---

### Post by walkerl on 2007-01-01
No, one mentioned this, but I would suggest, getting an additional harddrive and installing Windows on it. Once you install the drive, change the boot order in your BIOS, making the new drive boot first, then install Windows, after installing Windows, but your Linux drive back to one and your Windows drive to 2 in the boot order. After doing this, make a few changes to grub, and that's it.

---

### Post by glabouni on 2007-01-12
if you're thinking about playing 3D games under a vmware machine, you can forget it, performance are really terrible. at least on my personal I have achieved nothing but slideshows and crashes. 

I thought about using xen to get a native run, but from what I've read there is no 3D acceleration under windows in a xen installation on a virtualization enabled cpu. I have yet to try by myself though.

dual boot has the advantage to allow you to play 3D games but forces to reboot into windows each time you wanna play, and reboot into ubuntu each time you're finished playing.

here's a guide to dual boot:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

here's a guide to use xen on ubuntu:
[https://help.ubuntu.com/community/XenVirtualMachine](https://help.ubuntu.com/community/XenVirtualMachine)

---

