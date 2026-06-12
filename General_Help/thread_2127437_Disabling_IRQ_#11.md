---
title: "Disabling IRQ #11"
date: 2013-03-20
forum: General Help
---

### Post by GMachine_24 on 2013-03-20
I have been running 10.04 LTS on some older hardware - for a long time everything was fine but now whenever I boot the computer I get an error message that begins with a string of numbers, which changes with every boot but here is one example and followed by "Disabling IRQ #11" (without the quotes) so it looks like this:

[          6.075322] Disabling IRQ #11


Booting takes close to forever and after logging in - if I get that far - pretty much any task is verrrrrrrry slowwwwwwwwwwww.

I've searched online and in the forums - various guesses about this having to do with something in the kernel (going back many many versions of Ubuntu and other *nix OSes) and perhaps a USB device; really, I have no clue. I was using a USB keyboard and switched back to a PS-2 and sometime in there started getting the error message. Switched back to the USB keyboard and I still get the error message. Turned the BIOS support for USB off and booted - still got the error message. Turned it back on, still got the error message.

To be clear, there are no USB devices plugged into this computer at present. Am thinking about resetting the BIOS (via the MB jumper) but kind of didn't want to do that - only as a last resort. Because, at this point, I don't think it's going to change anything.

Found one post that said enabling "ACPI APIC Support" in BIOS made this error message disappear for one Ubuntu user; another said this didn't matter. And etc. No real answer.

Almost took a hammer to the hard drive today. Still seems to be a good idea.

---

### Post by dino99 on 2013-03-20
can you tell if that system got a fresh install recently, or if its a rolled dist-upgrade since 10.04, and now wich version it is ?
then i suppose your logs can greatly help to narrow down that issue, mainly /var/log/dmesg & .xsession-errors

as you said, the first thing to check is the bios settings (maybe need also to check for a bios upgrade), then you might also check the hdd settings (master/slave/...)
and clean the system as much you can: clean/autoclean/autoremove/gtkorphan/bleachbit

[https://help.ubuntu.com/community/DebuggingIRQProblems](https://help.ubuntu.com/community/DebuggingIRQProblems)

---

### Post by GMachine_24 on 2013-03-20
Hi. Thanks for your reply. It was just a full install of 10.04LTS - no version upgrade or anything.

I think I 'fixed' the problem: I found another setting in the BIOS for USB enabling/disabling and I changed that to disabled. That seemed to fix the "Disabling IRQ #11" problem. This all might have resulted from my attempt to boot the computer from a USB flash drive - and I don't think that's 'allowed' on this computer. I also thought about a BIOS update - but kind of wanted to leave that as a last resort.

Now, however, I get constant error messages re: secondary drives that I've installed to hold my music (this computer has served as a music server). The drives won't mount - I ran a file check and that seemed to fix some problems - but the drives still won't mount. So I took one to another computer with an external USB drive - one of those that you can swap hard drives. And, of course, the drive works fine.

I know I'm not putting up error messages and code so I don't expect/want any help. Just following up. At this point I might just throw everything onto a much-newer system because the one I have been using is about 13 years old - and enough is enough.

I'm going to mark this threat as *solved* even though I still have problems - but the IRQ problem is fixed.

Thanks again.

---

