---
title: "IDE Master/Slave difficulty"
date: 2007-06-08
forum: General Help
---

### Post by Moro-dashi on 2007-06-08
Hello all.

The past two days I've been working on an old computer of questionable stability and I just finally got Linux to run on it. I am running Xubuntu 7.02, installed from the alternate text-only CD burnt as an ISO image. As far as I can tell, these are my system specifications:

300MHz Intel Celeron Processor
512 MB of RAM
40x CD-ROM drive
Nvidia MX 4000 PCI graphics card
two IDE hard drives, one 40GB and one 120GB
I also have an unidentifiable PCI 10/100 network card

I have used both of these drives numerous times to attempt to install various Linux distros on other computers, so in the installation I chose to format the Master (the 40 gig) hard drive and install Linux on that. I did not choose to partition/format the 120 gig hard drive.

Upon booting up the computer, I discovered that Xubuntu ran quite nicely, but on my desktop (logged in as user, not root) there were at least five oddly sized "volumes" in addition to the standard "File System" one. I found this strange because they didn't add up; for example, there were two sets of volumes that looked like they used to be swap files based on their size, and two larger ones, and in addition to that there was one volume labeled simply, "120G Volume". If I tried to open any of these I received an error saying something like cannot mount volume or unable to mount volume.

Assuming these were old or damaged partitions, I formatted them with the Linux fdisk utility (I don't remember exactly what I typed in the terminal to do it though) and most of the drives went away. However, I still have the 120G volume (I reformatted so there was just one giant partition, primary only) and it still won't be accessed because of the "cannot mount" thing.

Can anyone help me out? Do I need to make logical drives out of it?

Thanks

---

