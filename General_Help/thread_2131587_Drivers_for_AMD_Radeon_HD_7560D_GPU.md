---
title: "Drivers for AMD Radeon HD 7560D GPU"
date: 2013-04-02
forum: General Help
---

### Post by RedYellowBlueBlast on 2013-04-02
Hi there, everyone.

While I am new to the forums, I am certainly not new to Ubuntu.

I hope this thread has made it to the appropriate sub forum. If not, please move this post for me mods/admins! :)

Anyways, Iv'e been really avid the Linux environment in these last couple years. And I'd really like to get some of my games to work properly on Ubuntu. However, it hasn't come very easy so far for me. I have a AMD A8-5600K APU in my machine, which has a integrated AMD Radeon HD 7560D GPU. Its plenty powerful to run most of my favorite games, such as Team Fortress 2, as it plays super smoothly under the Windows/Direct X environment.

However, as most of us as aware, the FGLRX driver in the Ubuntu 12.10 repositories does not work properly. So I went online and started looking for tutorials on how to install the latest PPA driver directly from AMD themselves, which is currently 13.1.

I was looking at this site in particular: [http://www.upubuntu.com/2013/01/amd-catalyst-display-driver-131-adds.html](http://www.upubuntu.com/2013/01/amd-catalyst-display-driver-131-adds.html)

I ran the commands given here and restarted my machine. The machines boots normally and doesn't seem to have any of the problems that the driver in the official Ubuntu repository does. (xserver issues.) But I noticed that at the bottom right corner of my screen, there is a testing purposes only" watermark. I thought this was odd and checked which version of the driver was actually installed on the machine through the terminal, and the terminal had reported to me that I was actually running the 12.10 driver. This is highly confusing to me. Why would a PPA, that I have found from multiple sources, report that it loads the 13.1 driver and then install the 12.10 driver?

I wouldn't even be all that concerned about this issue if 13.1 didn't have all the bug fixes which are important for running 3D applications. Can someone fill me in on this? Surly I'm missing something obvious here. Thanks for any help!

---

### Post by cristo-father on 2013-04-02
Best resource to install/uninstall any of the AMD graphics drivers(fglrx, OS,etc), is [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

I would search what is the most recommended driver for ur particular graphics card and from there use the installation guide on the site.

PPAs should be a last resort, the manual way is always better in my experience.

---

