---
title: "How to find what is causing the long booting time using bootchart"
date: 2012-11-18
forum: General Help
---

### Post by ghostrecon on 2012-11-18
Hey This is my bootchart [http://screencloud.net/v/Btva](http://screencloud.net/v/Btva) . The thing is am not an expert. I need someone who is really expert in this to tell me whcih apps or services that are causing the delay and how can I improve the booting time  disabling them 

thanks 

P.S am using UBuntu 12.10. Specs are:

amd A6 Quad core processor

---

### Post by NikTh on 2012-11-18
Well , fist of all I'm not an expert but I tended to experiment allot with such "tricks" in past. 

There is a reason where the startup applications are hidden. You can make your system unbootable or unusable very easy if you disable the wrong application. 

Is really the 1 min and 10 secs a long boot time ? 
For me , no is not. Except if you use an SSD .

A suggestion could be to try some things fist in VirtualBox. See here about VB=> [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)
then when you are sure about what you are doing , you can apply to your actual installation. 

PS: Recently I broke my system with such experiments, and is not the first time :p 
but this system (I have) is for such things , experiments.

---

### Post by ghostrecon on 2012-11-18
Thanks NikTh. Actually that's a really good suggestion. I am downloading virtual box now :)

and I said the same thing. 1:10 is good. But when I tried asking here : 

[[REDDIT]("http://www.reddit.com/r/Ubuntu/comments/13cobp/ubuntu_does_not_boot_in_10_sec/")] the majority of the laptops/PCs are booting in less than 15 sec O_o. But some of them said they have an SSD.

---

### Post by oldfred on 2012-11-18
It looks like i686? So that is 32 bit version? But that really should not matter.

I never understood boot chart, but review dmesg logs and look for any entry with error, repeated tries and then either timeout or later success. or just long times between entries. 

My rotating drives usually were about 40 seconds. Even though my SSD says 10 sec, BIOS takes about 10 sec & grub another 5 so it is between 20 & 25 sec total. 

I also find mounting NTFS partitions slows boot time a lot. And if you have issues with NTFS flags set - like needs chkdsk or hibernated that can slow boot.

---

### Post by ghostrecon on 2012-11-18
yea 32bit.

Ok. I disabled dropbox and now booting time is 45 secs with grub menu being disabled and autologin enabled.

I tried hibernation instead of normal shutdown and the hibernation made my boot time around 25~30 secs. :-/

---

