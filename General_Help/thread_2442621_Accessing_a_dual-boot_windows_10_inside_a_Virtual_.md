---
title: "Accessing a dual-boot windows 10 inside a Virtual Machine (using QEMU)"
date: 2020-05-05
forum: General Help
---

### Post by dariush91 on 2020-05-05
I know it can be done, because I did it ...then I somehow messed it up when trying to get the GPU-passthrough setup.

I'll try and keep this concise:

1. Initially I had ubuntu 18.04 and windows 10 set-up in a dual-boot configuration. Each is installed on a separate SSD drive so that when I boot-up I only needed to choose the drive and the relevant operating system would boot.
2. I then attempted to access my windows 10 with using QEMU in ubuntu by loading the image from dev/disk/by-id/NAMEOFSSDWITHWINDOWS when creating the VM. It worked. The simplicity makes me so happy.
3. So now I try to set-up a GPU-Passthrough, somehow I could not get VFIO to take control of the GPU and in the end I messed up enough with it so that ubuntu wouldn't log me in. So I figured I would start from scratch and hearing that ubuntu 20.04 was out I might as well upgrade - maybe things will work smoother with a shiny new OS.
4. However, with the new installation, the steps I took in no.2 no longer work! When I try to access windows 10 through the VM I am greeted by grub2 :frown: 
5. I notice also, that at the boot screen of my UEFI BIOS where I choose the operating system, it has changed. Where I used to click my SSD, now I must choose 'ubuntu' or 'windows boot manager'. If I choose either of my SSDs to boot from I am greeted by the same GRUB2 screen.

I feel strongly that point 5 is connected to why point 2 no longer works. _If only I could put the boot loading sequence back to how it was _I think QEMU would recognize windows like it used to, but I have no idea how. Even reformatting and reinstalling both SSDs separately while the other is unplugged hasn't changed it back.

I only switched to ubuntu a couple weeks ago so I'm am an amateur here, and my mind is so full of acronyms I think I might go crazy.
 
Maybe someone could shine a light on any solutions, or anything obvious that I've missed?

edit: hold on. I just realized that grub will load my usb windows disk automatically. It seems to be installing where I want it to. Finger crossed x

---

### Post by yancek on 2020-05-05
> . Initially I had ubuntu 18.04 and windows 10 set-up in a dual-boot  configuration. Each is installed on a separate SSD drive so that when I  boot-up I only needed to choose the drive and the relevant operating  system would boot. 

If they were both installed in the same mode (either both Legacy or both UEFI) you should have been able to boot both from the Grub menu.  If you want them separate, you can do it from the BIOS as you apparently were.  The link below gives a pretty detailed explanation of dual booting windows 10 and Ubuntu UEFI and the information there should be helpful so I would suggest first reading through it.  The page at the link below is the official Ubuntu documentation.  You might have mixed a Legacy with an EFI install with 20.04.  If you don't resolve this, go to the second link below and get boot repair using the 2nd option explained on the page using the Ubuntu 20.04 install media.  Make sure you only select the Create BootInfo Summary option and do not try any repairs.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by HermanAB on 2020-05-06
Note that normally, Windows 10 doesn't shut down completely, it suspends.  So if you reboot into Linux and access the suspended Windows filesystem, you can corrupt it.

---

### Post by dariush91 on 2020-05-06
Thank you for the advice. I got it working &#128513; 
I got the boot order allright, but as @yancek suggested, that didn't seem to be the problem.
By using SeaBIOS instead of UEFI in the VM I could boot. That way the graphics card was also recognized, however not functioning (with error 43). I had to physically swap the graphics card for ubuntu to accept it. For some reason it doesn't like me passing through a graphics card in the primary slot. 

I'll be sure to always shut windows down properly too!

---

