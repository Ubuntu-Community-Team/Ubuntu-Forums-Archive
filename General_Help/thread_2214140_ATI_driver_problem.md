---
title: "ATI driver problem"
date: 2014-03-30
forum: General Help
---

### Post by stelescuraul on 2014-03-30
Hello everyone, 

I have a huge problem with my video card. My laptop ( HP g62-b98es) has 2 video cards (one integrated and one dedicated).

HD 4250 (integrated) and HD 5470 

I can't find the proper drivers anywhere. I have installed the default one from additional drivers but when i restarted my laptop everything was black (couldn't do anything) so i had to remove fglrx. 

Please help me with instructions on installing the damn drivers. I have tried with the instructions provided in this link : [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD) , did not work. 

Another problem that i have is that on youtube or vlc or any video player, the video is not playing smooth but is played in "frames". the sound is fine but the video is not. I guess is it related with the video driver but i remember that even when i had it installed it did not work and i remember doing some changes in compiz (if i`m not mistaken) and it still did not work. 

Also from time to time i don't have internet connection. I am still connected to the network but there is no internet access. Any solutions ? 

Please let me know what kind of information you want me to provide and I will. I`ve been "fighting" with these problems for a long time. 

Thank you

---

### Post by deadflowr on 2014-03-30
This happened here
[http://ubuntuforums.org/showthread.php?t=2212381](http://ubuntuforums.org/showthread.php?t=2212381)

My advice is to follow this advice in that thread and disable the 4000 card.

---

### Post by stelescuraul on 2014-03-30
I can't disable the video card from bios. 

I had the ati catalyst center installed i could change from one graphic card to another (that was great because when i used the laptop on battery i just switched to power mode using the onboard video card) but now i am fine only with the dedicated one. Any tips on how to disable the other one ? 

Apparently the problem is still not fixed in the other thread.

---

### Post by Mark Phelps on 2014-03-30
My understanding is the the drivers that AMD provides on their website are for dedicated video processors of a single model, not for a mixture of models like that in your system.  While they might work in Windows, the problem you're running into in Linux is that the HD 4xxx series drivers require an older X-server version than the HD 5xxx series drivers.  Without a way to disable one of the two in the BIOS, you won't be able to install drivers for the other -- and as that thread indicated, there appears to be no way to do that.

---

### Post by stelescuraul on 2014-03-31
So you are telling me that I can't optimize my Ubuntu so basically i can't use it ? I had the ati CCC installed and it worked fine but i had video playback problems but now i can't find the proper drivers to make it work. I don't remember where i got the ccc from but it worked for switchable graphics .

---

### Post by mastablasta on 2014-03-31
he is tellign oyu that AMD dropped support for 4xxx chips and moved it into legacy while they stills support 5xxx chips. now the problem is that 4xxx drivers do not work with newer xserver available in ubuntu while the 5xxx drivers will work. by disabling the 4xxx card you will get zhe 5xxx workign propperly using proprietary drivers.

another solution would also be to just use opensource driver but from a newer kernel (i.e. to upgrade the kernel or use 14.04). or perhaps to use a distribution that still uses the older xserver (maybe debian stable or centos?!)

---

### Post by Mark Phelps on 2014-03-31
> So you are telling me that I can't optimize my Ubuntu so basically i can't use it ? 

Well, yes and no.  If by "optimize" you mean configure it to use BOTH video cards, on a demand basis, as is done in Windows, then  yes -- you can't "optimize" it.

Whether you can actually "use it" depends on whether or not you can disable the HD 4xxx chip to then install drivers for the HD 5xxx.  And,as mastasblasta pointed out, whether or not the default Radeon drivers work.

These multi-video-chip machines pose serious problems for Linux due to the lack of specialized drivers for them.

---

