---
title: "What will Feisty (7.04) break?"
date: 2007-04-20
forum: General Help
---

### Post by nami on 2007-04-20
I currently have Edgy installed.  The only changes I have made to Edgy are that I have installed VMWare Server, NVIDIA drivers and have TwinView enabled, plus I have installed some codecs to get certain audio and video files to play.

If I upgrade to Feisty, which of my custom additions/configurations to Edgy will break?  I am concerned because when I upgraded from Dapper to Edgy, it killed my install completely and the TwinView stopped working, so I ended up doing a fresh install of Edgy and had to redo all my customizations such as the NVIDIA drivers, TwinView, and installing VMWare Server plus installing all the guess operating systems I use via VMWare.

Any advice, help suggestions will be greatly appreciated.

Thanks

nami

---

### Post by cookfromfrozen on 2007-04-20
I can confirm that VMware Workstation 5.5.3 does not work in Feisty.  I installed it and halfway through the configuration it starts compiling a module because there are no pre-built modules for the running kernel, and then just dies.

Needless to say I won't be upgrading until I can use VMware, though I haven't tried the VMware Workstation 6.0 or VMware Server so those might work.

To be honest I don't have any confidence in upgrading, it's typically less painful in the long run just to reinstall.

---

### Post by nami on 2007-04-20
Thanks for that bit of info.  Would it be a good idea to list all the "currently breakable/broken applications" in the very first post as people reply on this post?

By the way I have VMWare Server 1.0.2.  Will that also break?

---

### Post by cookfromfrozen on 2007-04-20
Hi

I can't really say for certain whether VMware Server will break, but they all use the vmmon module so I'd say it's likely.

VMware "pre-build" the vmmon module for the stock kernels used by popular distributions but they haven't had time to catch up yet since Feisty only came out yesterday.  Now normally if there isn't a pre-built module for your kernel version, you can build it yourself, but this is what doesn't work for me on Feisty, so I can't start VMware Workstation at all.

Hopefully they will release an update or new beta that will include a pre-built module for Feisty, then it will work.

Then again, you could be lucky and it may work for you, you could always give it a try using the LiveCD if you don't want to hurt your Ubuntu that's installed at the moment.

Edit:  As soon as I can I'll give this a try:  [http://ubuntuforums.org/showthread.php?t=413646](http://ubuntuforums.org/showthread.php?t=413646)

---

### Post by solarforce on 2007-04-20
Hi All,

VMware workstation 6.0 Beta runs correctly.
I've tried the 64bit version.
[http://register.vmware.com/content/beta/ws/download.html](http://register.vmware.com/content/beta/ws/download.html)

Regards, 
 Viktor

---

### Post by kpkeerthi on 2007-04-20
> By the way I have VMWare Server 1.0.2. Will that also break?
I can confirm that VMWare server 1.0.2 does not work in feisty. It fails while compiling kernel modules. I have kernel source installed properly.

---

### Post by kimu on 2007-04-20
> **kpkeerthi said:**
> I can confirm that VMWare server 1.0.2 does not work in feisty. It fails while compiling kernel modules. I have kernel source installed properly.


VMWare server 1.0.2 has an error in the source code, that for it fails while compiling kernel modules.
To fix it you have to open /vmware-server-distrib/lib/modules/source/vmmon.tar after unpacking the tar file you donwloaded from vmware website.
Unpack vmmon.tar and edit vmmon-only/include/compat-kernel.h 

find this line 
#define __NR_compat_exit __NR_exit
static inline _syscall1(int, compat_exit, int, exit_code);

and cancel commas after int keywords. This is the result
#define __NR_compat_exit __NR_exit
static inline _syscall1(int compat_exit, int exit_code);

save, repack and launch the installer. Everything should go well.

Bye

---

### Post by hayesben on 2007-04-20
Hello

I've just tried the fix and unfortunately, it doesn't work (well, at least for me it doesn't).  Funny thing is that it creates the VMware Server Console in the menu but the installation bombs out.  Anyone out there been able to get VMWare installed with the above fix?

Ben

---

### Post by mhansen on 2007-04-20
> **solarforce said:**
> Hi All,

VMware workstation 6.0 Beta runs correctly.
I've tried the 64bit version.
[http://register.vmware.com/content/beta/ws/download.html](http://register.vmware.com/content/beta/ws/download.html)

Regards, 
 Viktor

32bit workstation 6.0 beta also works, FYI

---

### Post by riste on 2007-04-20
I was able to repair VMware Server 1.0.2 by fixing the source code and replacing the vmmon.tar file.

---

### Post by NZ-Wanderer on 2007-04-20
Hokay. I can unpack the files required using Krusader (root mode) but after editing the file, Krusader tells me "Writing to tar is not supported" - could you possibly tell me how to get the file back into the tar please?? (in simple terms please :) )

> **kimu said:**
> VMWare server 1.0.2 has an error in the source code, that for it fails while compiling kernel modules.
To fix it you have to open /vmware-server-distrib/lib/modules/source/vmmon.tar after unpacking the tar file you donwloaded from vmware website.
Unpack vmmon.tar and edit vmmon-only/include/compat-kernel.h 
find this line 
#define __NR_compat_exit __NR_exit
static inline _syscall1(int, compat_exit, int, exit_code);
and cancel commas after int keywords. This is the result
#define __NR_compat_exit __NR_exit
static inline _syscall1(int compat_exit, int exit_code);
save, repack and launch the installer. Everything should go well.
Bye

---

### Post by BristolGuy on 2007-04-20
Folks, KIMU's suggestion with altering the function _syscall1() worked like a champ for me.

I installed Edubuntu feisty today and VMware Workstation 5.5.3 on a Dell desktop.  Everything works fine.

To answer the previous post, you have to modify the permissions to make the TAR file r+w, extract the compat_kernel.h file, modify its permissions to r+w, edit the file, save it, then if you are using a GUI, you can drag the .h file back into the TAR file.  After that, rerun your .vmware-install.pl script.

---

### Post by Dream. on 2007-04-20
Well upgrade was not an option I had to do a fresh install and format the partition, so basically everything is broken. All the modifications I have had to do will have to be done again. The ongoing issue with getting the microphone to work correctly has taken a step backwards as its completely broken in feisty whereas it worked to some degree in edgy (although very poorly).

Once again I am very disappointed, and glad I backed up edgy. 

Get your act together and fix your operating system. Many many hours I have waisted fixing this and that, with obviously no success with the microphone. 

Reporting the bug via the official channels was a waste of time.

And basically an O.S. without a microphone is useless to me.

See you in 2020 if and when u even come close to being a decent O.S, listen to the people and fix your issues.

---

### Post by Ziggy72 on 2007-04-20
I'm running Feisty as a Windows guest using VMWare Workstation 5.5.3 build 34685 and everything is working normally. There were no installation problems.

---

### Post by nami on 2007-04-21
Seems like we have to use fixes/work arounds to get vmware server to work.  When will the next release of vmware be available?  Is there a news group we can sign upto to let us know when its here?  so people like me (who are prepared to wait a little) can do a simple upgrade from edgy to feisty without breaking vmware?

---

### Post by cookfromfrozen on 2007-04-21
I may try the Workstation 6.0 beta since that apparently works, but I'm not sure when a stable version will be out.  Like you I'd rather not have to perform messy hacks and I'll give it a few weeks until things just work.

---

### Post by nami on 2007-04-21
I love the "It just works" slogan. :KS

---

### Post by NZ-Wanderer on 2007-04-21
Thanks, I ended up editing the file in my windows partition and repacking it there. lots easier than trying to figure out how to do it in Kubuntu.

Anyway, It worked perfectly, I now have my Vmware server back in my newest Kubuntu..

Thanks greatly...

> **BristolGuy said:**
> To answer the previous post, you have to modify the permissions to make the TAR file r+w, extract the compat_kernel.h file, modify its permissions to r+w, edit the file, save it, then if you are using a GUI, you can drag the .h file back into the TAR file.  After that, rerun your .vmware-install.pl script.

---

### Post by PilotJLR on 2007-04-21
> **Dream. said:**
> Well upgrade was not an option I had to do a fresh install and format the partition, so basically everything is broken. All the modifications I have had to do will have to be done again. The ongoing issue with getting the microphone to work correctly has taken a step backwards as its completely broken in feisty whereas it worked to some degree in edgy (although very poorly).

Once again I am very disappointed, and glad I backed up edgy. 

Get your act together and fix your operating system. Many many hours I have waisted fixing this and that, with obviously no success with the microphone. 

Reporting the bug via the official channels was a waste of time.

And basically an O.S. without a microphone is useless to me.

See you in 2020 if and when u even come close to being a decent O.S, listen to the people and fix your issues.

I'm sorry your thread here and bud report did not produce results, Dream. On rare occasions, close-source drivers are simply never ported or built from scratch for some pieces of hardware; it would seem your mic is one of those.

That being said, your comments are juvenile; I can't tell if you're being serious, or if this post is a troll. It is a let down your mic doesn't work, but understand that the issue is a lack of manufacturer drivers (or the open specs with which the community can create one).


For what it's worth, I have 4 computers (I'm a geek) running either Feisty and Edge, and all work 100%. Even some "Windows only" hardware can be made to work, such as my ATI HDTV Tuners. Again it comes back to drivers for specific chipsets.

---

### Post by Dream. on 2007-04-21
> **PilotJLR said:**
> I'm sorry your thread here and bud report did not produce results, Dream. On rare occasions, close-source drivers are simply never ported or built from scratch for some pieces of hardware; it would seem your mic is one of those.

That being said, your comments are juvenile; I can't tell if you're being serious, or if this post is a troll. It is a let down your mic doesn't work, but understand that the issue is a lack of manufacturer drivers (or the open specs with which the community can create one).

For what it's worth, I have 4 computers (I'm a geek) running either Feisty and Edge, and all work 100%. Even some "Windows only" hardware can be made to work, such as my ATI HDTV Tuners. Again it comes back to drivers for specific chipsets.

I could understand my comments being juvenile if I was to swear and abuse everyone, but I didn't. I simply stated my experience and expressed my feelings toward ubuntu. As far as the soundcard goes, I have bashed my head against the wall with the following trying to get the mic working...

Sound cards tried: creative vibra 128, creative sound blaster live ct4830, creative sound blaster live 5.1 digital Audigy4 SB0610, 

Onboard sound: intel audio chipset.

creative vibra128 & onboard audio works very poorly with mic. Other two dont work at all.

What sound cards/onboard audio are you using in your four computers where you have everything working 100%:confused: 

I would be interested to know so I can try one myself, cheers.

---

### Post by PilotJLR on 2007-04-21
I understand it can be very frustrating... the reason I remarked on your comments is because it sounded like you feel people on this board are responsible for making the mic not work, or that no one cares about the bug report. People do, of course, want to fix reported bugs... but this is sometimes a slow process. In your case, the problem is a closed standard driver for the sound board; this isn't something that can be arbitrarily fixed. The chipset would either need an open standard, vendor support, or be reverse engineered.
Strictly speaking, the problem isn't linux, but rather a vendor using a closed standard. Still frustrating though, I know.


I'm using onboard sound cards on all of my machines, so I don't know if this will help you... but here is what I'm using.
2 desktops with nVidia CK804 audio chipsets
1 desktop with an Intel HD Audio controller (the HD one of their core 2 duo boards). this is the mythtv box.
1 laptop with an ALI M5451 audio board

---

### Post by nami on 2007-04-27
I just got an alert telling me that a new version of VMWare Server is out 1.0.3.  I currently have 1.0.2, how do I update to 1.0.3 and leave my existing virtual machines intact an in working condition?

---

