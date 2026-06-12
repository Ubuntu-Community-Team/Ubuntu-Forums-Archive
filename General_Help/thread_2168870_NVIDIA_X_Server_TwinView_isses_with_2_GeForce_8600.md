---
title: "NVIDIA X Server TwinView isses with 2 GeForce 8600GT cards"
date: 2013-08-19
forum: General Help
---

### Post by pete-petenoto on 2013-08-19
Hi All,

Full disclosure, I am relatively new to Linux and loving the learning curve but I am undoubtedly capable of ignorant mistakes :-)

I have a rig I am building for my home office desktop.  The basics:
[LIST]
[*]Gigabyte MB 
[*]AMD 64bt processor 
[*]Ubuntu 12.04 64bit 
[*]two Nvidia GeForce 8600GT video cards using a SLI bridge 
[*]two 22" DVI input HP monitors 
[/LIST]

So here is my issue (it is driving me nuts) with X Server.

If I plug both monitors into GPU 0 X Server auto configures TwinView and all is grand, works like a charm, though both are running off of GPU 0.

If I plug one monitor into GPU 0 and one monitor into GPU 1, X Server enables the monitor on GPU 0, sees but keeps the monitor on GPU 1 disabled.  My presumption (we all know the saying about presumptions) is that all I would have to do is select the disabled monitor on GPU 1 and drop down the Configure pull down and select TwinView...problem is when the monitors are plugged in this way, the TwinView option is greyed out and can not be selected. 

What am I not understanding here?  Is there some sort of configuration I need to do elsewhere for Ubuntu to utilize both GPU's?  

Any help will be most appreciated, thanks in advance.

---

### Post by pete-petenoto on 2013-08-21
Pretty quite out there, can anyone help me on this?

---

