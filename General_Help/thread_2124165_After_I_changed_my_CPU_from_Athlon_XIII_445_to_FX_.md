---
title: "After I changed my CPU from Athlon XIII 445 to FX 8120 Ubuntu won't start."
date: 2013-03-10
forum: General Help
---

### Post by JamesUbnt on 2013-03-10
Hi. Good day. 

I'm using Ubuntu 12.04 LTS 32 bits in my desktop computer with the following characteristics:

[LIST]
[*]AMD FX 8120 (new processor) Athlon XIII 455 (old one).
[*]**Motherboard GA-880GMA-USB3 which includes an onboard Radeon HD 4250. It also has been updated to the latest BIOS version(F3) and does support the FX CPU. ([http://www.gigabyte.com/products/product-page.aspx?pid=3817#ov](http://www.gigabyte.com/products/product-page.aspx?pid=3817#ov))**
[*]Partitioned with both Linux 12.04 and Windows 7 as OSs.
[*]16 GB RAM DDR3 Kingston
[*]More than half of my OS partitions is empty, also.
[/LIST]

Today I bought a CPU to upgrade my computer. After I installed it, Windows loaded fine. I worked for a while with it in Photoshop and Illustrator and then rebooted. 


[LIST=1]
[*]Ubuntu didn't start. All I saw was a bleeping cursor in the left corner of the screen for more than 10 minutes. Completely unusual.
[*]I restarted again in recovery mode. I saw strange conduct going on. I took pictures.
[/LIST]
[IMG]http://postimage.org/image/7qadb3wgd/[/IMG][IMG]http://postimage.org/image/7qadb3wgd/[/IMG][IMG]http://s14.postimage.org/bzf3d9zpt/DSC1031.jpg[/IMG]

After showing this, it would freeze for, like 10 minutes. Then, I'd see this:
[IMG]http://postimage.org/image/crmcq7tal/[/IMG]
[IMG]http://s14.postimage.org/i319axfdd/DSC1033.jpg[/IMG]

And it stays there forever. 

[B]I have already tried:

[/B]
[LIST]
[*]**Booting from the Ubuntu CD. (Both 12.04x32 and 12.10x64). Same thing happens and I just see a bleeping cursor in the corner after a short time.**
[*]**Searching the Internet for a similar error. Nothing. :(**
[*]**Loading both Optimal Defaults and Fail-Safe Defaults in BIOS.**
[*]**Booting from Knoppix or Slitaz Live CDs. Same thing. It gets stuck after a short while. But I get to see a little more of what's going on. Here are some pics I took while Slitaz was trying to start:**
[/LIST]
[IMG]http://s14.postimage.org/udpmh9c0h/DSC1030.jpg[/IMG][IMG]http://s14.postimage.org/yfbb0ntox/DSC1034.jpg[/IMG]


And here, it gets definetely stuck: 



 Please, help me recover my Ubuntu! I both work and study and I use it much more than Windows for my important stuff. What do you think is going on? As I said, Windows works just fine. It also detects all eight cores in the Performance tab in Task Manager.

---

### Post by dcstar on 2013-03-10
Go onto your BIOS and do a reset to fail-safe defaults and then try again.

---

### Post by JamesUbnt on 2013-03-10
Thanks, dcstar. I've already tried loading both Fail-Safe Defaults and Optimal Defaults from BIOS. Is that what you mean by resetting to Fail-Safe Defaults?

---

### Post by sanderj on 2013-03-10
I would try this:

Boot 13.04 daily from DVD/USB and see if it works
Boot 12.10 from CD/DVD/USB and hit F6 to change boot options. See [https://help.ubuntu.com/community/BootOptions#Changing_the_CD.27s_Default_Boot_Options](https://help.ubuntu.com/community/BootOptions#Changing_the_CD.27s_Default_Boot_Options)

---

### Post by JamesUbnt on 2013-03-13
[SIZE=2]Thanks for your answers. 

I have solved my problem. Here is what I did--and what was going on--for others who might have similar problems.. 

sanderj, you put me in the right track! Thanks. Heres iwhat I did in the end:

1. I disabled [COLOR=#000000][FONT=Verdana]AMD C1E Support in BIOS
2. I installed a more recent BIOS (F4e) from Gigabyte. (Which is labeled as a Beta, so that's why I didn't install  it before.) 

I searched around the internet and other people are having similar problems with Linux, Gigabyte motherboards and FX chips. They were solving the issue this way. As I said, I didn't download the most recent BIOS from Gigabyte before since it was labelled as a beta, but seems that's what works better to solve this issue. It also seemed to me that Gigabyte doesn't care about Linux users for some of the comments I read. 

Thank you all of you. [/FONT][/COLOR][/SIZE]

---

