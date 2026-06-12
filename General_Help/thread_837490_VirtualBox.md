---
title: "VirtualBox"
date: 2008-06-22
forum: General Help
---

### Post by Brunno Silva on 2008-06-22
I have an Ubuntu 8.04 installed in my laptop. Recently, I installed the SO Windows XP SP3 using VirtualBox, but it has three problems:

1. USB: The USB simply doesn't work. The Windows can't detect when i put a pen-drive, for example, in my laptop. BTW, is there other (local) way to share files between Ubuntu and Windows than by pen-drives?

2. Wireless: I can't connect via wireless with Windows, only via a wired connection.

3. Driver: From time to times, an error appears and then disappears. It states that the VirtualBox driver isn't installed.

Thanks for any help in these issues.

---

### Post by wolfen69 on 2008-06-22
> 1. USB: The USB simply doesn't work. The Windows can't detect when i put a pen-drive, for example, in my laptop. BTW, is there other (local) way to share files between Ubuntu and Windows than by pen-drives?
which version of virtualbox did you install? from the repos or the PUEL version from the virtualbox website? the [PUEL Version]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI") has USB support.
> 2. Wireless: I can't connect via wireless with Windows, only via a wired connection.windows uses whatever connection ubuntu is using. it is a shared connection.
> 3. Driver: From time to times, an error appears and then disappears. It states that the VirtualBox driver isn't installed. i would have to see the specific error message to help you.

---

### Post by TomDaBomb2u on 2008-06-24
I made the mistake of installing OSE yesterday instead of PUEL. I had everything set up fine before I realized that I had to get the PUEL version to have USB support. Now, I do not know how to uninstall OSE, and PUEL will not install at all. 

I downloaded virtualbox_1.6.2-31466_Ubuntu_hardy_i386.deb from the Sun website, right clicked it and selected "Open with GDebi Package Installer." I then clicked "Install Package." After I entered my password, it appears to begin installing, then I get "Failed to install package virtualbox_1.6.2-31466_Ubuntu_hardy_i386.deb"

Any ideas?
1.) Do I need to uninstall OSE?
2.) How do I get PUEL set up?

Thanks!

---

### Post by wolfen69 on 2008-06-24
yes, i would uninstall ose first. i just clicked the .deb file to install it. (puel)

---

### Post by TomDaBomb2u on 2008-06-24
Thanks wolfen. I had to uninstall OSE, then the PUEL package installed fine.

---

### Post by Brunno Silva on 2008-08-15
When I try to install the PUEL, the following error appears:

error processing /home/brunno/Desktop/virtualbox_(...)_i386.deb --install):
  trying to overwrite '/lib/modules/2.6.24-18-generic/misc/vboxdrv.ko', which is also in package virtualbox-ose-modules-2.6.24-18-generic
dpkg-deb: subprocess paste killes by signal (Brojen pipe)

Also, another doubt: I installed a Ubuntu 7.10 i386 in my AMD 64 laptop. Then, I upgraded to 8.04. When I try yo install the VB PUEL for AMD 64, it complains about a "wrong architeture". Is it normal?

---

