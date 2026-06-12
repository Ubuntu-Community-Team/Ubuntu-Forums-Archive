---
title: "Returning to Ubuntu after 5 years, getting crashes every hour."
date: 2016-08-14
forum: General Help
---

### Post by irreleventuser on 2016-08-14
So I installed 16.04.1 and have had crashes when playing stardew valley in steam, other games, firefox with youtube. Seems to be anything with video or gifs. 

I don't know what I've done wrong or if this is a known bug but every day in the past week or 2 I've had Ubuntu, I've had multiple crashes every day. I value my privacy from Windows 10 and all the crap along with it but it was at least stable. 

Any help would be appreciated.

---

### Post by oldfred on 2016-08-14
What video chip/card?
What brand/model system?
UEFI (newer system only)? or BIOS install (even on newer system)?

If AMD chip it may be an issue.
       [http://www.omgubuntu.co.uk/2016/03/ubuntu-drops-amd-catalyst-fglrx-driver-16-04](http://www.omgubuntu.co.uk/2016/03/ubuntu-drops-amd-catalyst-fglrx-driver-16-04)
[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx)
16.04 Release notes
When upgrading to Ubuntu 16.04 from a previous release, both the fglrx driver and the xorg.conf will be removed, so that the system is set to use either the amdgpu driver or the radeon driver (depending on the available hardware). 
With 15.10 Release notes
AMD's fglrx driver does not work with the current kernel
The fglrx driver is now deprecated in 16.04, use radeon and amdgpu

---

### Post by irreleventuser on 2016-08-14
*Awesome!* So, I would be better off doing a clean install of 15.10 if I want it to be more stable, or buy an nVidia card.. this whomps. I do have an AMD card, R7 265. I think I went with UEFI since I did a clean install and it sounded better. AMD FX 8320. 

Thank you for the answer though.

> The open-source Radeon drivers for AMD/ATI hardware are far from being a 1:1 replacement.
 AMD has a new Catalyst driver due for release this summer, but even  this effort, based on AMDGPU,  is unlikely to support the same breadth  of hardware that fglrx already does.



Does anyone know where I could find the software referenced here? I'll look myself and edit this if I find it.

---

### Post by oldfred on 2016-08-14
Many with AMD are installing 14.04 as that still supports the fglrx proprietary driver. And it is a long term support. 
Unless newer hardware where the drivers in 14.04 will not support the rest of the system that may be the better choice. 
It will install in UEFI mode also. How you boot install media is then how it installs.

I like to have more than one / (root) partition that is smaller, but data in another partition so I have the same data in all installs. Then I can test if changes still work with a full install while still having main working install.

I have 14.04 still installed on SSD, but have not booted it much since installing 16.04 to SSD. The 14.04 will probably not get overwritten until 18.04 is out as next LTS. And I then have 16.10 on HDD to see if any major changes or changes that make a difference in my configuration.

---

