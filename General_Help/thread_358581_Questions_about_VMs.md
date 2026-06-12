---
title: "Questions about VMs"
date: 2007-02-11
forum: General Help
---

### Post by Zeikcied on 2007-02-11
I've been thinking about using a virtual machine as a gaming alternative to Wine/Cedega.  And, I have some questions.  As most of my questions are more general than gaming related, I figured I'd put them here.

I'm running Kubuntu (Edgy).  I have an AMD Athlon 64 3200+ (2.2 Ghz), and I looked at the Community Documentation here on the Ubuntu website.  One thing I found was a shell command to see if any virtualization is supported by the CPU.  It was basically a grep command looking at /proc/cpuinfo, and it didn't get any results.  I'm fairly certain that the shell commands aren't specific to KDE or GNOME, so barring any BIOS settings that may enable it, is it safe to assume that my CPU doesn't support any of the newer virtualization stuff?  I'm a bit clueless as far as this kind of thing goes.

Also, I still have a WinXP install on the computer.  It came pre-installed with this machine, which is a Compaq.  As such, it doesn't come with install/recovery discs.  Rather it has a recovery partition.  Is it possible in any way, shape, or form to get a WinXP VM image from an existing installation?  Or do I have to create the install discs?  On a side note, I do have WinXP install/recovery discs from a previous Compaq that died last year.  Could those possibly work?

And, what kind of performance would be possible?  I know it depends if the VM has to virtualize the hardware or not, and I don't think I'll get native speeds, but what kind of slowdown could I expect?

I've never dealt with a VM before, and while the various HowTos are informative, I can't exactly find answers to all my questions.

---

### Post by racmar on 2007-02-11
Your main problem is going to be graphics.  You see, most VM's ( vmware ) uses a very basic 2d graphics driver.  Thus any 3d game will suffer tremendously.  That being said, I use a VM all the time, but I only play games /w a console these days ( please don't disrespect my choices ).  However, I do sometimes program /w windows and use IE to check my web pages for completeness using nothing but a vmware on my ubuntu laptop. 

You can download a free version of vmware-server from their web page.  Install it, then use the vmware-server-console to interact /w it.

Yes, you *can* use an existing partition /w vmware, but it is not supported or recommended.  Also, I use Acronis True-image ( $50 ) to clone partitions and save them on either DVD's or Network Attached Storage ( NAS ) devices.  You can however, freely download a linux rescue cd and use a program called dd or a norton ghost like program called g4l ( ghost for linux ).

To install windows in a vm is very easy, and you have multiple ways of doing it.  I have successfully imaged a copy of XP using Acronis True Image and then booted the rescue disk in a VM to restore the backup image.  You can boot from a retail XP disc, and that will also work.  Be careful with the OEM ( restore ) discs, because sometimes they check for certain BIOS flags before they will install ( not 100% sure about this ).

Hope this helps

---

