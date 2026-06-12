---
title: "Laptop brightness key NVIDIA all work on 20.04"
date: 2020-04-15
forum: General Help
---

### Post by WildSioux on 2020-04-15
Hello, I was unsure where to post this.  I have been using linux since about 2008.  Never really stuck with one for very long as I was learning and testing.  Jumped from Ubuntu, LinuxMint, fedora, opensuse, Manjaro, and a few others.  Always came back to Ubuntu or LinuxMint.  Found them to be the most user friendly.  Our desktop computer is currently on LinuxMint (ubuntu 18.04) I think with Cinnamon desktop.  

I'm writing this from my 15 year old Sony Vaio VPCCW26FX Intel® Core&#8482; i5 CPU M 520 @ 2.40GHz × 4, 4GB ram, with integrated GeForce GT 330M/PCIe/SSE2. (Sorry didn't know how to insert a picture of my system info.  I haven't used this laptop for at least 3 years.  Haven't needed to since I have a tablet, phone and the desktop if I needed something that big.

I have had this ongoing issue of the FN+F5, F6 brightness keys.  No matter what distro I installed the brightness keys typically wouldn't work. More often than not I just would not install the NVIDIA driver and use the nouveu since that worked.  A few times I even used it on full bright for the short time I needed it.

This past week I actually needed to use this laptop for Zoom meetings.  Tried a few distros mainly Ubuntu 19.04, 19.10 and linuxmint based on a release within the last year or so and a few others. each one, the brightness FN keys didn't work with Nvidia.  Sad to see that things were stiil the same with it not working in same way or another including the base install without a driver.  That is kind of a minimum that the brightness functions work.

I finally downloaded the Ubuntu rolling release focal Ubuntu Focal Fossa (development branch) from distrowatch.  Installed the Nvidia drivers and ran in to it freezing on boot.  Found that with the autologin enabled and Nvidia drivers was causing this issue.  [https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1845801]("https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1845801") Edited the grub and deleted "splash" from GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"  autologin now works!  

So why does 20.04 work smoothly with NVIDIA.  When over the past 15 years they failed in some way with brightness keys not working?  I'm not complaining just curious what finally changed to make it work.

I'm happy that this is working even though it is a development rolling release.  With Nvidia things are really smooth and it runs cooler not having to use as much CPU.  

Thanks and keep up the good work!  There is a reason why I have come back to Ubuntu!

---

