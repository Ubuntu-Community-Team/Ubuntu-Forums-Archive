---
title: "Automounting a PSP under Kubuntu"
date: 2006-12-19
forum: General Help
---

### Post by Reapman on 2006-12-19
Ok I've been pulling my hair out trying to get this working just right, tried google and these forums with no luck... here's the details:

I'm running Kubuntu Edgy, and have recently bought a PSP.  I don't like the idea of it being detected as a generic "usb device" and using sdc1, so i setup a udev rule to have it point to /dev/psp whenever it's inserted.  This way Amarok properly knows where to transfer my music tracks to.

here's what I added to udev:
/etc/udev/rules.d/60-local.rules
BUS=="usb", SYSFS{manufacturer}=="Sony", SYSFS{product}=="PSP Type A", KERNEL=="sd?1", NAME="%k", SYMLINK="psp"

here's what I have in fstab:
/dev/psp        /media/psp        auto            noauto,rw,user                 0 0

now if I do a mount -a it will mount and work just fine.  However what I want for it to do is AUTOMOUNT like any other USB thumb drive... it used to do this, until i created that blasted udev rule.

Now I'm assuming by creating that rule whatever controls automount under KDE ignores it... so I guess my questions are...

1) How can I get it to automount?  I've tried a udev rule along the lines of: "RUN+="mount /dev/psp", ACTION=="add"" but it doesn't seem to do anything (and I am having trouble finding good udev documentation that covers this)
2) How does KDE automount... at least with this I could maybe get a good idea of where to look?

3) Finally last and definitly least... when I DO mount it by hand it puts the icon on the desktop (which I want) however it gives it an iPod icon ](*,)   How can I change that to be a PSP icon (I have the graphic, just don't know what to do with it)

Thanks for any help!

---

