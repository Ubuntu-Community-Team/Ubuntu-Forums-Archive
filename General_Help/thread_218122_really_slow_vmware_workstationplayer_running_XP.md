---
title: "really slow vmware workstation/player running XP"
date: 2006-07-18
forum: General Help
---

### Post by RikoW on 2006-07-18
Hi there,

I recently installed vmware workstation and player and created a virtual machine for XP. My ubuntu in running on a laptop with 512 MB of ram and >1 GB of swap. The XP virtual has 372 MB (close enough) of ram.

However, the machine is harly usable because it is running extremly slow. I don't expect speed wonders of course, but to wait minutes until the control panels come up is not really acceptable.

It also slows the host machine down quiet a bit.

From the system monitors on the host, it seems like it's mostly HD access.

Does anybody know about buttons to push to speed up the virtual a bit?

Thanks,

         Riko

---

### Post by bigken on 2006-07-18
have installed vmware tools ;)

---

### Post by RikoW on 2006-07-18
me, too! Slow nevertheless ... but more comfortable :)

---

### Post by andy_cowman on 2006-07-18
Mine works brilliantly, I bought some extra RAM so XP and Ubuntu both have 512mb each. What CPUs do you use? If you have a modern intel try using the latest 686 kernel. I swtiched to it and it increased speed no end. ALso if you havent done it already turn off all the junk in XP like the graphical effects etc.

Good luck with it!

---

### Post by RikoW on 2006-07-18
> **andy_cowman said:**
> Mine works brilliantly, I bought some extra RAM so XP and Ubuntu both have 512mb each. 


I don't think RAM is really a problem, because (at least from the system monitors) it seems, the available memory is not even fully used. But of course, more RAM can never hurt :) I'll see what our group admin has in his drawers :)

It's seems like the network setup was at least one of the problems. After fixing that and giving the virtual the proper MAC adress as required by our network admins, it works somewhat faster, but still it takes ages to start-up or resume.

> **andy_cowman said:**
> What CPUs do you use? If you have a modern intel try using the latest 686 kernel. I swtiched to it and it increased speed no end.

I'm already running the 686 version of the current Ubuntu kernel

> **andy_cowman said:**
> ALso if you havent done it already turn off all the junk in XP like the graphical effects etc.


Uhh, what exactly do you mean?

I still have the suspicion, that the disk might be the bottle neck (too slow?). But that is not so easy to fix ....

Cheers,

          Riko

---

### Post by andy_cowman on 2006-07-18
XP has lots of silly toys on it that slow it down massively when its the only thing using the CPU! If i remember they are... 

system restore (not much using in a VMPlayer I decided). 

Set the memory options for performance not appearance. Right click my computer, properties, advanced, perforamnce settings button. The click best performance. It turns off a load of useless affects that you never notice anyway. 

Set the theme to Windows Classic so it looks like windows 2000, then go to the Appearance tab and click effects and turn all that junk off. 

You can also adjust the virtual memory settings, a quick google should tell you the best way to adjust it depending on the memory you have. 

To be honest RAM shouldnt make that much difference but what you are describing is the same as the problems I had when I first got VMplayer working. Giving it owns RAM really helped. The disk could also be a bottleneck. How have you set it up? I gave mine its own partition with plenty of space. Its EXT3 but then the VM files with the FAT32 partition work inside it. 

I know run Photoshop CS2 very easily through it, its a bit quicker than it was when XP was native on the machine. I also got the printing working from XP through the Virtual Machine to the CUPS server and for some reason I am really quite proud of myself!!

Andy

---

### Post by RikoW on 2006-07-18
Thanks, Andy!

going to the classic theme and turning all the unnecessary garbage off helped already a great deal.

Will try to get more memory also, maybe it will give another improvement on the performance.

Cheers,
            Riko

---

### Post by ephoenix on 2006-07-18
I found in the vmware knowledge base that there's some problem with linux RTC .

[http://www.vmware.com/support/kb/enduser/std_adp.php?p_sid=Ju1ulQci&p_lva=&p_faqid=892&p_created=1038952030&p_sp=cF9zcmNoPTEmcF9ncmlkc29ydD0mcF9yb3dfY250PTMmcF9zZWFyY2hfdGV4dD1ydGMmcF9zZWFyY2hfdHlwZT03JnBfcHJvZF9sdmwxPX5hbnl_JnBfcHJvZF9sdmwyPX5hbnl_JnBfc29ydF9ieT1kZmx0JnBfcGFnZT0x&p_li=](http://www.vmware.com/support/kb/enduser/std_adp.php?p_sid=Ju1ulQci&p_lva=&p_faqid=892&p_created=1038952030&p_sp=cF9zcmNoPTEmcF9ncmlkc29ydD0mcF9yb3dfY250PTMmcF9zZWFyY2hfdGV4dD1ydGMmcF9zZWFyY2hfdHlwZT03JnBfcHJvZF9sdmwxPX5hbnl_JnBfcHJvZF9sdmwyPX5hbnl_JnBfc29ydF9ieT1kZmx0JnBfcGFnZT0x&p_li=)

---

### Post by RikoW on 2006-07-18
Read that, but it claims it's for 2.4 kernels only but does not apply to 2.6 kernels.
Anyway, the /dev/rtc timer is present, read and writable for me and I only run one virtual machine.

It's still annoyingly slow, even after gettign rid of all the junk as Andy suggested. Haven't upgraded the memory yet, but I would be really surprised of an upgrade from 384 MB to 512 MB for the virtual machine gives a performance jump of several factors.

Cheers,
            Riko

---

### Post by andy_cowman on 2006-07-18
Hey
Ok you have other options, i have been thinking about why i made certain decisions on how to configure my system. I switched to XUbuntu because things were slower on normal ubuntu. It may be that running the 2 OSes with one CPU is simply to much. Reducing the overall load was my conclusion so I went for speed on my linux system. What system do you have?

Other options are using a different version of windows (ME, 2000), how about codeweavers crossover office or free wine?

Andy

---

### Post by RikoW on 2006-07-19
Hi again,

I'm running Ubuntu Gnome and the whole set-up is so fast, that I never had the feeling I have to get a 'thinner' desktop to reduce the load.

Unfortunately, I'm sort of 'stuck' with XP. I want/need to run the windows operation system which is the standard in the organization I'm working for. That I can follow my liking for Linux and Ubuntu in particular is due to the 'generosity' (if you want to call it like that) of my employer. In 90% of the cases, there is no need for XP because I manage just fine in Ubuntu also in exchanging documents (thanks to OOo) and meetings (evo)with XP users.
However, sometimes you just have to have Windows, for example for MS Project. 

I tried wine, but it's no good for my purposes. Haven't checked crossover yet.

I can hardly believe that you should not be able to run 2 OSes with a 1.6 GHz Pentium4 even with 'only' 512 MB RAM!! Still waiting for the 1 GB upgrade and will report back. :)

Thanks again,

              Riko

---

### Post by RAOF on 2006-07-19
> **RikoW said:**
> ...
I can hardly believe that you should not be able to run 2 OSes with a 1.6 GHz Pentium4 even with 'only' 512 MB RAM!! Still waiting for the 1 GB upgrade and will report back. :)
...
512MB of ram shared between 2 OS gives you only about 256MB per OS.  Furthermore, if the virtual machine keeps its 378MB of ram all the time (which I believe it does), that leaves only 140MB of ram for Linux.  That's really not very much (even though you can still buy Dells that come with that amount of ram).  The fact that there's a lot of disc access suggests that you're hitting the swap quite a lot.  That's probably what's slowing the system down - nothing kills performance quite so much as needing to use the harddrive as extra RAM (it's about 3 orders of magnitude slower ;)).

In short, I don't think there's any reason for the quotation marks around "only" :)

---

### Post by philippe_carlo on 2006-07-19
Actually, I have it running on my 512MB laptop and the response is acceptable here. Of course, I'm just using a resolution of 1024x768. I gave the VM 256 MB of memory. It's slow at times, but usable. There must be something else that slowing you down.

---

### Post by andy_cowman on 2006-07-19
I am running 2.8ghz celeron chip with 1gb RAM with a Geforce 256mb card with XUbuntu and it all runs brilliantly. 

I think the RAM should definitly make a difference to it, I also wonder if 1.6ghz is fast enough to manage all those processes at once? I imagine it can do it just that it may be a lot for it but I have not tried it. 

If you still need Windows then VMs are definitly the way to go! Good luck with getting it all set up for it!

Andy

---

### Post by ephoenix on 2006-07-19
I am running 2.0Ghz Pentium M with 2 Gb RAM on a IBM Thinkpad T43. Ubuntu 6.06 is installed as a primary OS. I also tried to use VMWare Player to run WindowsXP but it's so slow that I can't work with it. I tought that the bug found on VMWare was that because if you go in the ".h" file specified in the bug, the #DEFINE is at 100HZ not 1000HZ like it's suppose to be in a 2.6 Kernel. I'm not interested and familiar to build a custom kernel. So for now I'm planning to re-installed my laptop with a dual-boot setup and I'll wait for a bug fix for that...

---

### Post by RikoW on 2006-07-19
Hi all,

first of all, thanks for the fruitful discussion. In fact, my problem was that I gave to much ram to the virtual machine. So in fact, what made the machine slow was the swapping on the Linux host.

I checked, how much ram is used by Ubuntu when not running any application. That left about 200 MB of teh 512 MB available unused. So, those 200 MB I assigned as ram to the virtual XP and everything in honky-dorey :)

I still waiting for an additional 512 MB from our group admin and that shoudl solve all my problems! hopefully :)

Thanks again for the suggestions and the discussion,

                 Riko

PS: Now I have the problem left of using a brideged network connection with the wireless .... see next thread :)

EDIT: Well, actually NAT might be enough for wireless access. So I guess for now no new thread :)

---

### Post by andy_cowman on 2006-07-19
I'm glad you are pretty much there with it, thats very interesting about the virtual memory. I am gonna check mine and see if I can get even more speed!!!  Knowing my current luck I will break everything!

Andy

---

### Post by gswoods on 2008-03-12
Just for the record: I am having the same problem. I do NOT have this problem running the same version of VMware Workstation under Fedora Core 6, but I do have the problem under Fedora 8, which is one reason I wanted to try Ubuntu on this laptop in the first place. It has to be a software problem, as the hardware is identical when running FC6.

The big difference, I think, is that in order to even get the kernel modules to build under F8 or Ubuntu Gutsy, I had to apply vmware-any-any-update115. On FC6, only update92 is required. What updates did you guys have to apply?

---

### Post by gswoods on 2008-03-12
My laptop has 2GB of memory. I tried upping the amount given to the virtual machine (from 768K to 1GB) and that helped just a little. Diddling with the Windows settings (turning off pointer shadow, using Classic theme) made no difference at all. Right now it is just agonizingly slow. Anything that requires use of the CPU runs at a snail's pace. A bridge game I have takes nearly 30 seconds to play a card, which on the same virtual machine is nearly instantaneous on FC6/update92.

It almost has to be something introduced in the update115, as I do not have the problem with FC6 using update92.

---

