---
title: "Force VESA driver in Ubuntu 18.10 from Grub"
date: 2019-02-20
forum: General Help
---

### Post by Jason_Hunter on 2019-02-20
[COLOR=#242729][FONT=Arial]When editing the entry in Grub boot screen, what kernel parameter can I give linux to force it to only use the VESA driver for both bootup and Xorg[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Can this be forced from grub boot for both the OS startup and for Xorg?[/FONT][/COLOR]

---

### Post by oldfred on 2019-02-20
Does nomodeset work?

I have this in my notes, but now very old.
       insert "nomodeset" as a boot kernel switch to be able to boot VESA 
    
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

If you need specific gfxmode:
       
 From a grub command line (from grub menu) to see available settings pressing <c> & escape to get back to menu:
vbeinfo 

 Details on settings in /etc/default/grub
 info -f grub -n 'Simple configuration'
> `GRUB_GFXMODE'

  Set the resolution used on the `gfxterm' graphical terminal.  Note
 that you can only use modes which your graphics card supports via
 VESA BIOS Extensions (VBE), so for example native LCD panel
 resolutions may not be available.  The default is `auto', which
 tries to select a preferred resolution.  *Note gfxmode::. 
  

       Use command line editor grub's on set gfxmode=640x480
and just remove the # as that makes that line a comment and change to what vbeinfo output was.
sudoedit /etc/default/grub
# then 
sudo update-grub

---

