---
title: "Newbie's question about ATI driver"
date: 2007-06-03
forum: General Help
---

### Post by jingdejun on 2007-06-03
I know there are lots of threads about this topic, but it is difficult to extract a clear summary for a newbie like me. 

I am using ATI Radeon 9600XT, installed Ubuntu Feisty. I followed [this great post]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon") to install Beryl. Everything went smoothly. However, I found problem in using 3D hardware acceleration (I am doing some 3D CAD and computer simulation and need OpenGL).

Now, I am confused and don't know where to go next. After read some online linux post, I have several questions:

(1) To enable OpenGL, do I have to stick with fglrx driver instead of 'radeon' driver?

(2) After I finish a fresh installation of Ubuntu Feisty, looks like direct redering is enabled. However, I still have 'X error' when I install some softwares. So, what on earth the status of the fglrx driver's usability after a fresh install of Ubuntu Feisty? 

(3) How to check Xorg status or video card status? Generally what kind of commands should be used?

 I am new to linux, so sorry for such simple questions.

---

### Post by AD-RS1600i on 2007-06-03
Hi,

I don't profess to be an expert so please take what I say with a pinch of salt.

I never managed to get my ATi Radeon to work on Edgy, but I did on Feisty Fawn.

I believe fglrx driver is not used this time around, I certainly didn't on mine, it is purely the Beryl driver which runs AIGLX. So I wouldn't attempt to input your old method for setting you graphics up under Edgy..

I found this guide which was ace and worked really well with my setup, I advise following it, and if you can get it to give you the wobbly windows and cube effect using the Beryl driver you are likely to have cracked your problem (deselect those options first from System>Preference>Desktop Effects).

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29)

Hope this helps

---

