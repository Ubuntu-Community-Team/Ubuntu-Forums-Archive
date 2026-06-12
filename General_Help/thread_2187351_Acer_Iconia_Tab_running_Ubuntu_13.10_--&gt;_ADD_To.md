---
title: "Acer Iconia Tab running Ubuntu 13.10 --&gt; ADD Touch GUI ???"
date: 2013-11-11
forum: General Help
---

### Post by jamesisin on 2013-11-11
I have an Acer Iconia Tab on which I have successfully installed Ubuntu 13.10 (desktop) and which works great/as-expected.  It has a sort of docking station with a keyboard (or I suppose I could attach a USB keyboard).  That's all fine.

However, if I try to use it like a tablet there are various annoyances and deficiencies.  (For example, navigation is awkward and I have to have a keyboard running all the time on-screen.)

I am hoping to add a repository which will allow me to install some of the GUI packages intended for the Touch version into this version.

Thoughts?

---

### Post by jamesisin on 2013-11-12
I chatted with a dev over at the Ubuntu Touch IRC channel.  I am informed that they aim to have the Touch functionality rolled into regular Ubuntu perhaps by 14.04.  (Currently there is no way to install those GUI elements into regular Ubuntu.)

---

### Post by jamesisin on 2013-11-15
I talked (via IRC) with someone over at Ubuntu Touch.  These packages ought to be available perhaps nearer to the release of 14.04.

---

### Post by Gouzi001 on 2014-03-02
Hi Jamesisin,
I had create USB stick with 13.1, cause it no contain .efi bootfiles, I had use it from oracle distribution /partition magic/.
After Grub appear i use:

menuentry "UBUNTU 13.1" {
linux /casper/vmlinuz.efi boot=casper
iso-scan/filename=/ubuntu-13.10-desktop-i386.iso noprompt
initrd /casper/initrd.lz
}


kernel loads sucesfully, - it wrote booting UBUNTU 13.1, than screen goes black and get stuck. Did u use some initrdEFI ?
Or what you amend in original .iso ?

Thank you

---

### Post by jamesisin on 2014-03-03
I think I just used my YUMI drive with a regular Ubuntu installer.  The tablet I have may just use BIOS though.  It came with Win7 installed.

Also, in case anyone is interested, I was able to get the onscreen keyboard to auto-appear by locating a setting in its preferences.

---

