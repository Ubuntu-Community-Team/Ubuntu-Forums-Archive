---
title: "AMD GPU driver issues. (?)"
date: 2017-11-21
forum: General Help
---

### Post by johnstefnds on 2017-11-21
So here is the deal I am currently running a system which uses a nvidia GPU (GTX 650 ti) I decided to upgrade to an AMD RX 580 8GB

It will arrive next friday what concerns me is that after starting a preliminary googling on what should be the best method to delete nvidia drivers and install AMD drivers I found out (or at least currently from what I have seen from my google searches) that AMD has serious issues with drivers for linux or atleast ubuntu... 

I thought that Nvidia was the "bad guy" in the linux driver world yet it seems AMD has not released any good proprietary driver for linux ... I see posts like these for example [https://askubuntu.com/questions/815591/ubuntu-14-04-5-16-04-16-10-and-amd-graphics#815592](https://askubuntu.com/questions/815591/ubuntu-14-04-5-16-04-16-10-and-amd-graphics#815592) saying that they dont even support the card "officially" on 16.10...

And I am running ubuntu 17.10 :S 

I also see different driver names like Amdgpu-pro and Mesa etc...

Could a** linux amd gaming connoisseur** advise me on what driver to use (also by the way how to purge my nvidia drivers from the system) and if I will face any serious perfomance bottleneck while gaming and how to avoid it if possible? 

Will the linux drivers for my AMD graphics card suck??? (compared to the windows drivers) 

Should I return the card and buy a nvidia one? 

I thank you in advance for your time and effort :)

---

### Post by QIII on 2017-11-21
AMD has an excellent open source driver as well as a proprietary overlay that you can add.  Your problem will likely be whether or not the Linux kernel is ready for that GPU to run with the driver.

You may have to use the (excellent) open source Radeon driver for a time until the driver/kernel combination is worked out.

Sometimes it is best with Linux to avoid the very newest hardware.  OEMs have to spend the same resources to update drivers that are used by only 2% of their customer base as for the entirety of the rest; and the kernel developers have to make sure the kernel cooperates. 

It is rare that the very most cutting edge hardware will work without complaint.  The 580X is a perfect example.  Unfortunately, your research may have been too late.  You might want to avoid opening the packaging and do a lot more research to decide if you would like to return the item.

No need to necessarily change to Nvidia.  I am using an AMD 380X right now with AMDGPU and AMDGPU-Pro on top of it.  But I'm going to continue to use 16.04 until the issues with Wayland in 18.04 are sorted out.  That is likely to affect both Nvidia and AMD.

---

### Post by johnstefnds on 2017-11-21
> **QIII said:**
> AMD has an excellent open source driver as well as a proprietary overlay that you can add.  Your problem will likely be whether or not the Linux kernel is ready for that GPU to run with the driver.

You may have to use the (excellent) open source Radeon driver for a time until the driver/kernel combination is worked out.

Sometimes it is best with Linux to avoid the very newest hardware.  OEMs have to spend the same resources to update drivers that are used by only 2% of their customer base as for the entirety of the rest; and the kernel developers have to make sure the kernel cooperates. 

It is rare that the very most cutting edge hardware will work without complaint.  The 580X is a perfect example.  Unfortunately, your research may have been too late.  You might want to avoid opening the packaging and do a lot more research to decide if you would like to return the item.

No need to necessarily change to Nvidia.  I am using an AMD 380X right now with AMDGPU and AMDGPU-Pro on top of it.  But I'm going to continue to use 16.04 until the issues with Wayland in 18.04 are sorted out.  That is likely to affect both Nvidia and AMD.

Thanks for your response.. but what do you mean by driver overlay? what does an overlay do? 

my kernel is 4.13.0.17 is this bad news or good news? 

I am not interested in just buying a compatible card I already have my GTX 650 ti which is perfectly compatible and runs fairly late drivers (387.22) and plays games in vulkan or openGL and whatnot... 

but I want more FPS in late games which my card plays flawlessly (driver wise and in terms of stability and graphics quality) but in low FPS... 

Obviously I dont expect the FPS rate to be identical to windows but the more the better so I need a new graphics card to do that job and if its not going to be the rX 580 it has to be the GTX 1060 which on windows is a little behind the RX 580 but it needs the same drivers (387.22) to run fine on ubuntu.

And generally I see an major driver update coming from nvidia every 3 or so months a few months ago it could not support vulkan but with the late drivers it now can etc...

The "taste" that I am getting (again without having first hand experience or proper research just from what I gather from a few quick google searches) is that AMD cards in general (for example I saw this video for the older RX 460 [https://www.youtube.com/watch?v=0L_85Xgd1Aw](https://www.youtube.com/watch?v=0L_85Xgd1Aw)) have quite a few issues.. and (to my standards at least) I consider them incompatible almost..

---

### Post by QIII on 2017-11-21
AMDGPU is an open source driver produced by AMD, where the Radeon driver is an open source driver produced by the Linux community.  AMDGPU-PRO is a proprietary "add on" to AMDGPU.

Much of the misinformation about AMD drivers is a carry over from before AMD bought ATI.  ATI didn't really care at all about the Linux community and their drivers were terrible.  AMD got that all going in the right direction.

But the Linux community demanded a good open source driver from AMD.  This became a "be careful what you wish for" situation.  AMD went all out and produced one.  But it only works with hardware after a certain point that could use the driver.  AMD is in the process of porting that back to some earlier models, but it will only go as far back as the first generation of GCN (Graphics Core Next) GPUs.  That means that most of the HD series will not be supported.

But AMD is a business.  As such, it has to make a profit.  The only way they could get AMDGPU out was to drop any further development of fglrx.  Unfortunately, that driver will not work any more because the Linux world has moved on.

As new models, such as yours, come on line, there is a delay between its appearance on the market and the appearance of support for it both from AMD and from the kernel developers.

The straight up fact is that when the road construction is done, AMD will have positioned itself to provide support far and away better for Linux than anyone else.  Even now, given a supported card, the support is superior.  Nvidia will no doubt answer and its support will get much better.  That will be great for Linux.

If you are using an Nvidia card and it suits your needs, keep using it!  Nvidia produces a great product and its drivers are very good.  I'm not an AMD evangelist.  I just like to have the facts straight.

---

### Post by johnstefnds on 2017-11-21
but will it play crysis? No joke literally :P

---

### Post by johnstefnds on 2017-11-22
just heads up according to this link [https://www.phoronix.com/scan.php?page=article&item=vega64-open-lead&num=1](https://www.phoronix.com/scan.php?page=article&item=vega64-open-lead&num=1) I should not use AMDGPU-PRO but MESA.. its on a vega card which is not polaris but I dont know the difference is significant... grrr I ordered the card mainly because I thought AMD would have an even better/stable support than nvidia in the linux world turns out I was terrible wrong the opposite is true :( but I cant just return the card its already on its way :(

---

### Post by QIII on 2017-11-22
I have to say again:  This is the necessary road work to make AMD's support superior.  There are bumps and detours right now.  There is no doubt at all that this is terribly unfortunate and users are frustrated.  I would have recommended against that particular product at the moment.

This isn't a matter of AMD failing to support Linux, but positively supporting Linux.  They just can't snap their fingers and make it so.

Nvidia's support is very good as well.  Both companies expend a lot of resources to satisfy a very small slice of the market.  From a business perspective, that's a bad choice.  But they are both committed to Linux.  Both are members of the Linux Foundation.

---

### Post by mastablasta on 2017-11-22
> **QIII said:**
>  From a business perspective, that's a bad choice.  But they are both committed to Linux. 

maybe not, since GPUs these days are not used only on desktops (where linux market share remains small). nVidia entered mobile market, AMD would like to follow. then there is bitcoin mining, various servers (minor super computers) that process CGI etc.

---

### Post by QIII on 2017-11-22
I was speaking specifically of the consumer market, actually.

The contracts in supercomputing amount to billions of dollars each.

---

### Post by johnstefnds on 2017-11-22
ok after finding this article which is exactly about RX 580 performance on ubuntu [https://www.phoronix.com/scan.php?page=article&item=rx580-pro-open&num=2](https://www.phoronix.com/scan.php?page=article&item=rx580-pro-open&num=2) I am perfectly convinced that AMDGPU-PRO is **not** the way to go MESA simply has significantly better performance in games which is what exactly I am looking for.

---

### Post by realdreams on 2018-04-09
> **QIII said:**
> AMDGPU is an open source driver produced by AMD, where the Radeon driver is an open source driver produced by the Linux community.  AMDGPU-PRO is a proprietary "add on" to AMDGPU.

Much of the misinformation about AMD drivers is a carry over from before AMD bought ATI.  ATI didn't really care at all about the Linux community and their drivers were terrible.  AMD got that all going in the right direction.

But the Linux community demanded a good open source driver from AMD.  This became a "be careful what you wish for" situation.  AMD went all out and produced one.  But it only works with hardware after a certain point that could use the driver.  AMD is in the process of porting that back to some earlier models, but it will only go as far back as the first generation of GCN (Graphics Core Next) GPUs.  That means that most of the HD series will not be supported.

But AMD is a business.  As such, it has to make a profit.  The only way they could get AMDGPU out was to drop any further development of fglrx.  Unfortunately, that driver will not work any more because the Linux world has moved on.

As new models, such as yours, come on line, there is a delay between its appearance on the market and the appearance of support for it both from AMD and from the kernel developers.

The straight up fact is that when the road construction is done, AMD will have positioned itself to provide support far and away better for Linux than anyone else.  Even now, given a supported card, the support is superior.  Nvidia will no doubt answer and its support will get much better.  That will be great for Linux.

If you are using an Nvidia card and it suits your needs, keep using it!  Nvidia produces a great product and its drivers are very good.  I'm not an AMD evangelist.  I just like to have the facts straight.

That sounds quite optimistic about AMD.
On 16.04 Nvidia binary/Intel driver works out of box most of the time (was a hit and miss on 14.04). From what I have read AMDGPU/AMDGPU-PRO is at best hit and miss currently, if the user can get it to work at all. I am talking about a workstation setup (multi monitor, HDMI/DP audio, some occasional youtube playback), not even gaming.

[https://www.phoronix.com/scan.php?page=news_item&px=AMDGPU-Audio-Still-Format-Woes](https://www.phoronix.com/scan.php?page=news_item&px=AMDGPU-Audio-Still-Format-Woes)

---

### Post by QIII on 2018-04-09
Your article mostly addresses a particular series of APUs, not the broader class of GPUs in general.  The broader issue is related to newer audio formats.  It is not terribly unusual for the "newest" stuff to lack immediate driver support in the Linux world.

This particular user has had no problems at all with AMDGPU-PRO running a GPU supported by it.  It is not difficult to "get it to work at all."

---

