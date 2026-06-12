---
title: "installed ubuntu updates, nvidia driver broken (again!)"
date: 2008-06-28
forum: General Help
---

### Post by shmoe010 on 2008-06-28
I had been away from this particular machine for about 2 months because of a trip, and when I came back and turned it on, I saw that I had about 150 updates to download, which being the anal-retentive user I am, I got right away. At this point, my nvidia settings were fine, and my resolution was a cozy 1280x1024.

Upon reboot, however, I got the famous "running in low-graphics mode" dialog and it suggested the Vesa driver, which as we all know, is horrible. I'm pretty new to linux, and i had a very similar problem before, but my college roommate was a compsci major and fixed my video settings for me (it took about an afternoon of fiddling with it) and now I can't get a hold of him. It's really hard to work in 640x480 with 16 colors. :(

I have envyng and had it install the nvidia driver to no avail. The I downloaded the nvidia driver from nvidia.com which is a *.run* file, and was not able to do anything with that (if someone could remind me of the coding that would be great!) Then I typed in a command that nvidia suggested to get something like nvidia-glx-new? but of course that failed too.

I am just really stuck, and if anyone has resolved a similar problem I would really appreciate the help. I've looked over the forums and searched and tried several different fixes to no avail. Here are my system specs:

Ubuntu 8.04 (latest update)
Opteron 165 @ 2.45 GHz
DFI LanParty NF4 SLI-DR
2x1GB G.Skill DDR SDRAM
eVGA 7800GTX PCI-E 256MB GDDR3
Seagate 320GB SATA 300

Thank you in advance for the help!

---

### Post by shmoe010 on 2008-06-28
bump

---

### Post by steveneddy on 2008-06-28
When you do get it figured out, if you run the nvidia driver in the repos, this won't happen again.


:-k

---

### Post by PmDematagoda on 2008-06-28
About the problem, how did you install the driver in the first place?

---

### Post by hextic on 2008-06-28
I am having this issue as well whenever the kernel or the nvidia driver updates.  If I install the kernel before reinstalling the Nvidia drivers, then it causes a problem.  I created a bug report, but after at least a month, it does not appear to have even been seen.  If interested, it is bug #240742.

---

### Post by relaxdane on 2008-06-29
Hello, as you can see, I am pretty new to ubuntu, but I also had some problems with my nvidia driver. I installed it with Envyng, and when i was finished rebooting, I too ran in low-graphics mode. However I solved this problem by typing (sorry, I do not know how to make the terminal box):

sudo dpkg --configure -a

in terminal. After reboot everything was fine. Hope this was helpful.

---

