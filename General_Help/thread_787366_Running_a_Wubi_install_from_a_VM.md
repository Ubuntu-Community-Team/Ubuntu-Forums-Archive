---
title: "Running a Wubi install from a VM?"
date: 2008-05-08
forum: General Help
---

### Post by d0nk on 2008-05-08
Hi,

I'm preparing to reformat my laptop (currently dualboots windows xp and ubuntu).  I am considering getting rid of my ubuntu partition (15gb, of which I use maybe 5-6gb of, as everything is on my storage partition) and using Wubi.  

One question I have is whether or not I can easily boot my wubi install from a VM like qemu or Virtualbox within windows (for when I don't want to reboot, but need something in nix).

My thoughts are that I may need to make a minimal linux install in virtualbox and have it mount my wubi loopback file as /.  Is there an easier/better way, or is what I described the best/only way of doing this currently?

Thanks.

---

### Post by garyedwardjohnston on 2008-05-08
When you install Ubuntu from XP using Wubi, you need don't need virtualization software too.

Just download and install from XP.  Simple.

---

### Post by d0nk on 2008-05-08
I'm well aware of that. What I want to do is be able to boot ubuntu (installed via wubi) using a VM in addition to normally booting.

---

### Post by garyedwardjohnston on 2008-05-08
I really do not understand what you are trying to do.

You can run as many operating systems as you like, all at the same time too.  Simply install numerous virtual machines and run them all.

As far as booting, you can only boot into one operating system at computer startup.

You can also make a virtual machine one of the startup programs.  I am most familiar with Virtualbox so if you want help with Virtualbox let me know.

---

### Post by ago on 2008-05-09
> **d0nk said:**
> Hi,

I'm preparing to reformat my laptop (currently dualboots windows xp and ubuntu).  I am considering getting rid of my ubuntu partition (15gb, of which I use maybe 5-6gb of, as everything is on my storage partition) and using Wubi.
Hmm not sure it's a good idea. If you need space, resize your partition to say 5-8GB (the same space would be required by wubi anyway).

If you want to run ubuntu apps within Windows without dualbooting then use andLinux
There is no much point running Ubuntu in VM, if you have to use a VM use a VM Ubuntu installation.

---

### Post by leahcim_bulwark on 2008-05-09
This is for gentoo and windows, but the same idea applies. Is this more along the lines of what you are trying to do?

[http://gentoo-wiki.com/HOWTO_Configure_a_dual_boot_windows_linux_to_be_able_to_open_each_os_in_vmware](http://gentoo-wiki.com/HOWTO_Configure_a_dual_boot_windows_linux_to_be_able_to_open_each_os_in_vmware)

---

### Post by d0nk on 2008-05-09
> **leahcim_bulwark said:**
> This is for gentoo and windows, but the same idea applies. Is this more along the lines of what you are trying to do?

[http://gentoo-wiki.com/HOWTO_Configure_a_dual_boot_windows_linux_to_be_able_to_open_each_os_in_vmware](http://gentoo-wiki.com/HOWTO_Configure_a_dual_boot_windows_linux_to_be_able_to_open_each_os_in_vmware)

Thanks, that is exactly what I was talking about.  I'll try it out sometime this weekend/next week.  If it doesn't work out I'll just do a 5gb ubuntu partition as suggested by ago.

---

### Post by markjreed on 2009-10-21
> **garyedwardjohnston said:**
> I really do not understand what you are trying to do.

Windows box, Wubi install.

The OP wants to, while running Windows, launch the Ubuntu install inside a VM (e.g. VirtualBox). Using the same image that Wubi uses, without having to reboot.

I would like to do the same thing.  Is it doable?

---

