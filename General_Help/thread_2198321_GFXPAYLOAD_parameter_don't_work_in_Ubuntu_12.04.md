---
title: "GFXPAYLOAD parameter don't work in Ubuntu 12.04"
date: 2014-01-08
forum: General Help
---

### Post by Libertario on 2014-01-08
Hi there,

I have a virtual machine in VMware Fusion with Ubuntu 12.04 and I would like to fix the resolution to AxY parameters.

I set the parameters in /etc/default/grub to:

[LIST]
[*]GRUB_GFXMODE=1280x720
[*]GRUB_PAYLOAD_LINUX=keep
[/LIST]

Then I executed the command "sudo update-grub" and ends successfully.

The GRUB menu resizes correctly but the OS don't keep the resolution.

The parameter has other name?

Thanks,
Bruno.

---

### Post by stinkeye on 2014-01-08
I believe the command is..
```
GRUB_**GFX**PAYLOAD_LINUX=keep
```
and doesn't it just maintain the same resolution for the plymouth splash?

---

### Post by Libertario on 2014-01-08
Yes, the parameter is "GRUB_GFXPAYLOAD_LINUX". I misspelled it. Sorry.

The splash screen get the new resolution successfully but it doesn't keep for the OS.

Thanks.

---

### Post by stinkeye on 2014-01-08
Grub won't set your resolution once booted.
You need to look for solutions for vmware...
eg [http://askubuntu.com/questions/334456/cannot-change-resolution-on-ubuntu-13-04-desktop-with-vmware-tools](http://askubuntu.com/questions/334456/cannot-change-resolution-on-ubuntu-13-04-desktop-with-vmware-tools)

---

### Post by Libertario on 2014-01-08
The GRUB manual says:

"If this variable is set, it controls the video mode in which the Linux kernel starts up, replacing the &#8216;vga=&#8217; boot option"

I though that this should be enough...

It worked in Debian 7 without X.

Thanks.

---

### Post by stinkeye on 2014-01-08
> **Libertario said:**
> The GRUB manual says:

"If this variable is set, it controls the video mode in which the Linux kernel starts up, replacing the &#8216;vga=&#8217; boot option"

I though that this should be enough...

It worked in Debian 7 without X.

Thanks.
Doesn't set the X environment resolution though.
And then your adding virtualization to the mix.

---

