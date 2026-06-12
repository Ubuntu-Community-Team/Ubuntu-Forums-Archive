---
title: "[SOLVED] Might have to go back to Windows......"
date: 2008-06-25
forum: General Help
---

### Post by drjonze on 2008-06-25
I may have to end my great Linux experiment. I have enjoyed Ubuntu (8.04 64bit) and some of the features are just amazing

BUT....

My PC has crashed more in the last week than it ever has. My system keeps freezing up and there are lots and lots of posts from people with same problem and there are no solutions. I cannot keep hard booting twice a day.

I'm tired of having to reset all of my display settings every two days. I'm tired of the launcher icons on my panel being in a different position every time I reboot. My caps lock and num lock lights don't work. My computer will freeze if it goes into suspend/sleep - it will freeze when my screen saver comes on.

I'm not going to bash ubuntu because its working great for a lot of people, I don't think my experience is by any means typical. But there is just way too much tweaking and repairs I have to do and I just don't know enough about computers and Linux. 

My specs:

Acer Aspire 9300 AMD 64
Ubuntu Hardy AMD 64
Nvida Geofoce 6100
Atheros network card

Are the previous versions of Ubuntu any more stable?

---

### Post by jimv on 2008-06-25
That's just kinda how it goes.  I used 7.04 without too many problems.  I upgraded to 7.10 and my machine wouldn't even boot.  I then tried 8.04 when it was in alpha, and I've been using it since.  I also had the freezing problem, which *seems* to have been resolved by installing the RT kernel.  (sudo apt-get install linux-rt)

I guess the best thing to do is to go back to Windows and try the next release to see if it's any better for you.

---

### Post by HalPomeranz on 2008-06-25
I think it has a lot to do with hardware choices.  I'm running 8.04 x86_64 on my Thinkpad X61s and it's rock solid.  But when buying my computer I specifically chose one that was most likely to be compatible with Linux.  IBM/Lenovo have a strong Linux commitment and I went with the lower-end Intel graphics rather than have to fuss with a proprietary video driver.

So maybe you retreat back to Windows for now (though you can keep running Ubuntu inside of VMware to keep in practice).  But the next time you buy a new computer you might think about getting hardware that has good Linux support.  Also by the time you get a new machine more bugs will have been worked out of Linux in general.

---

### Post by drjonze on 2008-06-25
> **jimv said:**
> That's just kinda how it goes.  I used 7.04 without too many problems.  I upgraded to 7.10 and my machine wouldn't even boot.  I then tried 8.04 when it was in alpha, and I've been using it since.  I also had the freezing problem, which *seems* to have been resolved by installing the RT kernel.  (sudo apt-get install linux-rt)

I guess the best thing to do is to go back to Windows and try the next release to see if it's any better for you.

Thanks for your reply. I tried the RT kernel but my pc freezes when it starts to boot. 

I'm going to do a fresh install. I have been stumbling around for a little while trying all sorts of things out and I may have messed something up and not have known it.

I won't quit yet, I've gotten discouraged before and I found things like using my wiimote with the Elisa media centre or Stellarium, and I get excited all over again.

---

### Post by msrinath80 on 2008-06-25
I have nothing against Ubuntu. I just want to point out the Ubuntu has deviated a lot from the standard LSB (Linux Standard Base) guidelines and the folks that create Ubuntu have decided on their own unique ways of handling the init system, the kernel and so on. So hard lockups are to be expected. Before you completely write off GNU/Linux, I would recommend giving either OpenSuSE or Fedora a try. Maybe even Debian as it is still well behaved.

---

### Post by drjonze on 2008-06-25
> **HalPomeranz said:**
> I think it has a lot to do with hardware choices.  I'm running 8.04 x86_64 on my Thinkpad X61s and it's rock solid.  But when buying my computer I specifically chose one that was most likely to be compatible with Linux.  IBM/Lenovo have a strong Linux commitment and I went with the lower-end Intel graphics rather than have to fuss with a proprietary video driver.

So maybe you retreat back to Windows for now (though you can keep running Ubuntu inside of VMware to keep in practice).  But the next time you buy a new computer you might think about getting hardware that has good Linux support.  Also by the time you get a new machine more bugs will have been worked out of Linux in general.

I suspected as much. I bought this machine before I had even heard of Ubuntu so I really had no choice. I have discovered from the forums that nvdia and atheros are just problematic, they just don't play well with linux. I have two strikes on me right there. 

Good news is that I just happen to be buying new machine next month, I have a good idea of what hardware to avoid and what to get. For now, I can avoid must of the freezing problems with adjustments to my power settings. I'm going to try re-installing it and see if I have better luck.

Thanks!

---

### Post by VMC on 2008-06-25
> **HalPomeranz said:**
> I think it has a lot to do with hardware choices.  I'm running 8.04 x86_64 on my Thinkpad X61s and it's rock solid.  But when buying my computer I specifically chose one that was most likely to be compatible with Linux.  IBM/Lenovo have a strong Linux commitment and I went with the lower-end Intel graphics rather than have to fuss with a proprietary video driver.

So maybe you retreat back to Windows for now (though you can keep running Ubuntu inside of VMware to keep in practice).  But the next time you buy a new computer you might think about getting hardware that has good Linux support.  Also by the time you get a new machine more bugs will have been worked out of Linux in general.

I think this is the KEY to life. :)  When you select a new computer and you think you might install a Linux system, make sure that computer supports it, or the hardware does at least. Most all computers are built For Windows. It's that simple.

 I was lucky for some reason. I have a Dell with built in video and my ubuntu 8.04 is rock solid. In fact this is the first time I've been Windows free in 20 years!

---

### Post by HalPomeranz on 2008-06-25
> **drjonze said:**
> 
Good news is that I just happen to be buying new machine next month, I have a good idea of what hardware to avoid and what to get.

If you're in the market for another laptop, I find the write-ups at [http://tuxmobil.org/mylaptops.html](http://tuxmobil.org/mylaptops.html) useful when I'm trying to figure out which machines have the best Linux support.  Typically I'll identify a few laptops that seem to best meet my price/performance requirements and then look at tuxmobil to see how much difficulty people have had getting the laptops working with Linux.

> **drjonze said:**
> 
For now, I can avoid must of the freezing problems with adjustments to my power settings. I'm going to try re-installing it and see if I have better luck.


Good luck!

---

### Post by mempman on 2008-06-25
> **drjonze said:**
> I may have to end my great Linux experiment. I have enjoyed Ubuntu (8.04 64bit) and some of the features are just amazing

BUT....

My PC has crashed more in the last week than it ever has. My system keeps freezing up and there are lots and lots of posts from people with same problem and there are no solutions. I cannot keep hard booting twice a day.

I'm tired of having to reset all of my display settings every two days. I'm tired of the launcher icons on my panel being in a different position every time I reboot. My caps lock and num lock lights don't work. My computer will freeze if it goes into suspend/sleep - it will freeze when my screen saver comes on.

I'm not going to bash ubuntu because its working great for a lot of people, I don't think my experience is by any means typical. But there is just way too much tweaking and repairs I have to do and I just don't know enough about computers and Linux. 

My specs:

Acer Aspire 9300 AMD 64
Ubuntu Hardy AMD 64
Nvida Geofoce 6100
Atheros network card

Are the previous versions of Ubuntu any more stable?


In my opinion, there isn't really much need for 64 bit OS's just yet-unless you are using programs specially crafted to take advantage of the extra bits.  

I have 64-bit dual core AMD processors in my HP laptop but I choose to run 32-bit ubuntu.  It is surprising that ubuntu or any linux works with today's closed-design hardware.  It's remarkable how much the linux community has been able to reverse engineering to the point that Ubuntu is battling for hardware estate with current leaders such as MS and MACs.  

Could you imagine what Canocial would be doing do its competitions if there wasn't any bias by hardware manufacturers?

---

### Post by breadbin on 2008-06-25
did you try running a memory test? I saw a post called instability that describes your situation and most people think its memory related. won't hurt to try it although you might want to go and make yourself a cuppa while its going on!

what about a different ubuntu or different linux. i was in your place a while ago and went back to windows exclusively but got fed up after a while cos there was no challenge. i now dual boot and have the best of both worlds. i actually need linux for the internet so i use it more than windows

---

### Post by Zardus on 2008-06-25
drjonze, I noticed that you nave a Geforce in that comp. My media center has one as well (although an FX5900), and I had bad lockup problems when I put Hardy on it as well. Switching from agpgart to NvAGP fixed the issue for me; the machine is now rock solid.

---

### Post by drjonze on 2008-06-25
Thanks for all the tips everyone. I'm going to try a few out and see how it goes. A friend of mine said I was crazy to try an unsupported operating system. I told him that I get better tech support on this forum than I have gotten anywhere else.

---

