---
title: "Ubuntu 12.04 (64 bit), Skype and Microsoft Lifecam HD-3000"
date: 2013-05-02
forum: General Help
---

### Post by amtrakuk on 2013-05-02
Hi.

I'm trialing moving to Ubuntu from a Mac.  All is going well except the Webcam (M$ Lifecam HD-3000) which works fine under 12.04 (32 bit) but doesn't appear to initialise correctly under 12.04 (64 bit).  I will only be using it with Skype.  I have tried after a fresh reinstallation of Ubuntu (both before and after any updates).  The symptoms shown seemed to be with the initialisation of the hardware, the LED blinks 4-5 times and then gives a long flash which usually the point it is sucessfully initialised however under the Ubuntu 64 bit version it seemes to go though an endless loop of reinitialising.  Reconnecting the webcam seems to resolve the situation until the cam is reused.  Has anyone got any fixes or is there a patch I need to apply?

No other applications except Skype has been installed at the point of testing.

Any help resolving this issue would be welcome.

Thanks in advance.

---

### Post by fantab on 2013-05-02
Install "Cheese" on 64bit and see if the webcam works. If it does, then there could be some issue with 32bit libraries. Skype is not available in 64bit so we use 32bit on 64bit, with 32bit libraries. Confirm with 'cheese'.

---

### Post by amtrakuk on 2013-05-06
Just tried 12.04/64 with cheese.   The cam works however it does seem as though with Skype (both versions) the cam does eventually initialise but after the app has duimmed down (not responding).   I have gone back to 32 bit and the cam is working fine.  I'm guessing it is something to do with the lib files compatability with the 64 bit kernel.   Hopefully it will be resolved soon.  I have done some googling to no avail ;(

Interesting.  I think the problem could be with the 64 bit drivers.   The lifecam works fine under ubuntu 12.04 32 bit but not 64 bit.   I have just done a fresh install of ubuntu 12.04/64, the cam was initialised ok during the installation while deciding on my avitar also fine on first boot (tested with cheese) before I installed the updates.  Ever since installing the updates the cam starts doing its repeated intialisation cycle, even when all applications are closed.

I did try 12.04/64 on another machine that had problems with skype audio - on that occasion the skype audio worked fine until you played a MP3 or went onto a website that used audio (Youtube etc).  From then on Skype audio failed.  After a lot of reading it seems skype needs the 32 bit drivers (I think).  The audio problem was fixed by running : sudo apt-get install libasound2-plugins:i386 then rebooting.  Then Skype was happy and I was able to make and receive calls before, during and after listening to MP3s.

Going on the same basis as the audio problem and the cam working fine under a 32 bit OS, I was wondering if the problem was 64 bit drivers?   If so where can I download and try install 32 bit drivers?

Many thanks

It seems running sudo apt-get install ia32-libs then rebooting seems to resolve.   just done a skype test cam call which worked well with the cam inisitalising as expected ;)

---

