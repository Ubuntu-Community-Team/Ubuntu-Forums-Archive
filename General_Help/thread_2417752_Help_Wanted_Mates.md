---
title: "Help Wanted Mates"
date: 2019-04-26
forum: General Help
---

### Post by dlrp on 2019-04-26
Prototype Project
DLRP - 2019

Hardware: Raspberry Pi 3
OS: Ubuntu Mate 16.04, RetroPie V4.4
Languages: Python, Java
Temporary: Berryboot

OPERATING SYSTEMS
- Ubuntu Mate 16: Currently striping down the OS to the bare minimum I need. An alternative I've chosen over starting from scratch, (A server or mini.iso), then building up instead. Version 2 will be done using this method, but for the time being I need to learn more about the main components of Ubuntu, and the new kernel recently released in UM 19. I've been using my favorite command for cleaning; &#8220;sudo apt-get purge --auto-remove ProgramName*&#8221;. This method is fine on a small scale where I'm familiar with what I'm purging, but doesn't help me remove large packages and dormant software. Synaptic is also a good tool to use, but it's limitations are still my ignorance. A comprehensive guide on the steps to take to strip down a distribution to its &#8220;barebones&#8221; or my essentials would be greatly appreciated.

- RetroPie V4.4: More testing is required before community support is necessary.

- OpenELEC: Analyzing code and components to determine if integration, into an admittedly crowded system, is even necessary. (The thought or idea is that there would be a specially designed OS to handle the three general tasks of; Gaming, Audio/Video, & Administration)

HARDWARE ISSUES
- Power: Will consistently show lightning bolt symbol in top right-hand corner of the screen, indicating it doesn't have enough power and/or USBs are demanding more than the unit can constantly produce.

- Boot: Looking for solution to avoid having to keep third party bootloader installed, (Berryboot), in-order to have an OS run from a USB.

GENERAL QUESTIONS
1) Is there an easy method for overriding or forcing components to update? Either one-by-one or in bulk. I realize that some aren't updated because there could be compatibility issues with the newest version of the software, but I'm not a typical user so problems caused will be documented and repaired. 

2) Is there a comprehensive guide to programming a Python project start to finish? Maybe a template? I can only conceptualize it to a certain point before it becomes redundant. In other words I need to know where to draw my lines.

3) For hosting a small website, (single domain), is there open-source python tools or examples to aid? Have no experience with website creation or hosting so would need to be a beginner's guide.

4) Packaging the stipped down UB OS once Version 1 is completed - then it can easily be installed on other Raspberry Pi units, as well as extracting the necessary components to build a version that can run on an early 2000&#8217;s (former XP) computer - which will act like a headless server with only text output.

---

### Post by TheFu on 2019-04-27
If you need a minimal OS, skip all the Ubuntus.
There are Linux OSes with X/Windows that fit in 16MB.
If you need a server, I've seen 400MB versions.

Depending on your needs, a r-pi might not be the best choice of machine.  Check out Atomic-Pi - this is an Intel Atom-based device for $34 and is faster than many chromebooks.  If you are stuck on ARM, the Odroid-N2 or Rock64Pro also provide real GigE and real USB3 ports.  For deployment (i.e. sales), I would avoid r-pi.  It doesn't have solid audio and can't support h.265 video and certainly doesn't support 4K video, which is standard at this point.  

Becoming a solid python webapp developer will take 6-12 months, assuming you already know the language.  The number of domains doesn't matter. 1 or 500, it is the same.  I'm a perl/ruby/C++ guy and admin, so cannot help with python.

As for controlling which packages are updated or not, APT has methods for that which are easily scripted or you could use any of the devops tools. Ansible has the lightest footprint on the client machines.  Ansible is written in python, if that helps, though as an ansible user, you don't need to know python.

No way, no how, would I attempt to run Java on a r-pi box.  No.  Just ... no.

---

