---
title: "Acer Aspire VN7-591G very regularly slows down until freezing"
date: 2015-01-29
forum: General Help
---

### Post by ePierre on 2015-01-29
Hi everyone,

I'm trying to troubleshoot an issue that's driving me crazy on my laptop using Ubuntu 14.10.

My laptop is an Acer Aspire VN7-591G with 8 GB of RAM, an i5 CPU, a 1TB HDD and a nVidia/intel Optimus GPU that sucks all of my battery in less than 1 hour even when I'm just editing a file in vim.

From time to time, my laptop slows down to the point where the mouse cursor gets laggier and laggier and finally the whole screen freezes. I cannot access the TTY (Ctrl+Alt+F2 for instance), or when I can, it takes forever.

I thought it was related to the Web browsers I use, because usually, this happens when I access a JavaScript-intensive website like Google Maps or Google+. However, some times I don't have any problems accessing them. Some other times the same issue happens just by opening a terminal (Ctrl+Alt+T).

I'm using Firefox to my work-related tasks and I tried the following for news/social network browsing:

[LIST]
[*] Chromium
[*] Opera
[*] Midori
[*] QupZilla
[/LIST]


Everytime I ran into the same issue at some point.

When I can reach the TTY, I try to check htop and iotop. It looks like my CPU are not used intesively, and for the disk access, I'm not sure because it fluctuates a lot (and usually, by the time iotop is finally launched, the situation gets better).

I checked the disk integrity using the "Disks" utility and my hard drive looks OK.

I don't know what/where to investigate in order to solve my problem. I'm getting tired to have to reboot my laptop once an hour because of these freezes, though&#8230;

Thanks in advance for you help!

---

### Post by ajgreeny on 2015-01-29
What drivers are you using for the **nvidia optimus** system? That is most likely the power-hog in your laptop?

I suspect you need to investigate **bumblebee**, which is getting better but still has some way to get before it equals the windows equivalent.

I have no experience of any nvidia cards so I speak only as a result of reading much about this problem.

---

### Post by ePierre on 2015-01-29
According to the "Additional Drivers" panel, I am not using any proprietary drivers and there are not any proprietary drivers available for my laptop.

lspci gives me the following info on the graphic cards available:

[FONT=Courier New]00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
01:00.0 3D controller: NVIDIA Corporation GM107M [GeForce GTX 860M] (rev a2)[/FONT]

lshw -c video gives me the following output:

[FONT=Courier New]  *-display UNCLAIMED     
       description: 3D controller
       product: GM107M [GeForce GTX 860M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:d0000000-d0ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:4000(size=128) memory:b2000000-b207ffff
  *-display
       description: VGA compatible controller
       product: 4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:48 memory:d1000000-d13fffff memory:c0000000-cfffffff ioport:5000(size=64)[/FONT]


So basically it's as if the nVidia card was not using any driver… I really don't understand what's going on here! Any idea?

---

### Post by ajgreeny on 2015-01-30
Not really, I'm afraid as I have never used nvidia, and certainly not an optimus system.

However a quick search suggests you may need the xorg-edgers repository which has a driver for that nvidia card.
See [http://askubuntu.com/questions/526668/how-do-i-use-nvidia-gtx-860m-with-14-04](http://askubuntu.com/questions/526668/how-do-i-use-nvidia-gtx-860m-with-14-04) for some more info or do a search with the term **GTX 860M driver** using my custom search site [Ubu-Search]("https://www.google.co.uk/cse/publicurl?cx=003847201077524938900:ukjniuf1wao")

---

### Post by ePierre on 2015-02-02
Thanks for your answer!

I installed the NVIDIA drivers through xorg-edgers repository and am now using v340.x of their drivers. I turned off the NVIDIA card and am only using the Intel GPU (as I explain in the askubuntu post you linked to), but I'm afraid this has little impact on the lack of stability of my computer, because less than an hour after the update, my computer froze while displaying a blog post on Opera... :(

---

### Post by ePierre on 2015-02-06
It looks like the problem comes from an intensive use of the hard drive. Basically, when I load a JavaScript-intensive web page or a big picture in a Web browser tab (no matter what web browser), I can hear the hard drive working a lot. The more I wait, the more my laptop slows down (cursor moves less and less) until it's completely frozen and I have to force-stop it.

When I check with [FONT=Courier New]iotop[/FONT], I can see a lot of process write on the the hard drive including [FONT=Courier New]apport[/FONT] (the bug report tool written in Python). Could it be that apport it overzealous and goes crazy gathering logs and preparing a bug report?

The strange thing is that I have 8GB of RAM and even in those critical situations, only 2-3 GB is used (when I check with [FONT=Courier New]htop[/FONT]).

I really don't know what's going on with my installation but I know this is pretty bad because if I keep froce-stopping the computer like that, the hard drive will just die...

---

### Post by ePierre on 2015-02-10
I used the sysstat tools iostat and it shows me during these "crisis" the iowait goes up to 99%. In those cases, the mouse cursor can hardly and I cannot do anything. Sometimes I still have time to switch to a tty and launch a "sudo killall opera" but most of the time it's already too late and I have to force-reboot...

---

