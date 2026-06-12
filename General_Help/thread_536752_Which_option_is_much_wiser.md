---
title: "Which option is much wiser?"
date: 2007-08-28
forum: General Help
---

### Post by chunchengch on 2007-08-28
Some people pefer to use VirtualBox, VM or Wine to run Windows applications, some prefer to have dual boot system with Windows and Linux installed on sperated partitions, which option will be the best on considering the performance and convenience together?:confused:

---

### Post by kuja on 2007-08-28
It depends what you intend to use. Dual boot is the most robust but the least convenient. Virtualizing brings a performance hit (not so bad that things aren't usable though, because they are or it wouldn't be this popular). Keep in mind that games requring 3d acceleration won't run in a virtualized environment (as of yet, may change in the future)

---

### Post by chunchengch on 2007-08-28
I ever installed Wine on my brand new laptop, however it took more than ten minutes to start up and froze my Ubuntu, now I would like to try VirtualBox or VM, what is your suggestion? thanks!

---

### Post by kuja on 2007-08-28
I found vmware to be easy to setup and use, I've not tried VirtualBox though. You can find information on setup in the Ubuntu wiki.

[https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)

---

### Post by Dark Star on 2007-08-28
See Vmware is a good option. But since Most I mean nearly all the distros comes with Live C d option its is useless to run them under Vmware :| So better use Live Cd for experience and installing Linux will give you a gr8 option to explore the GNU world :)

---

### Post by aquavitae on 2007-08-28
I found virtual box quite easy - but never tried vwmare.  I'm not sure if vmware is in the repos though - and I think virtualbox is.  If that makes any difference...

---

### Post by TeaSwigger on 2007-08-28
> **chunchengch said:**
> I ever installed Wine on my brand new laptop, however it took more than ten minutes to start up and froze my Ubuntu, now I would like to try VirtualBox or VM, what is your suggestion? thanks!

Take the frozen ubuntu. Make a mocha. 

hehe seriously, you are the one best suited to decide. Dual-boot can be the most inconvenient and WINE could be the most convenient, but it depends... I offer three questions to consider:

1 - What are the specs of your computer? If it's not more than 512mb memory, I do think you'd be far better served by either getting WINE working properly or dual-boot.

2 - How often will you use the windows environment? If it's to be used at any length or requires its best performance, you'd best dual-boot; if it's only a program or a few you need, and all can run good enough under WINE, sort WINE.

3 - What are you needing Windows to run? If it's gaming, a virtual box won't fly (yet); you'd have to go WINE or failing that you'll need a Windows dual-boot.

Or toss a coin ;) More questions, ask.

---

### Post by anaconda on 2007-08-28
I prefer virtual windows to dual-boot.

I have found Virtualbox easier to install, BUT I newer got the networking to work through Virtualbox. And in VMWare networking worked out of the box.. So I still prefer VMWare.

Also VMWare server is free for companies also (needs registering) Virtualbox on the other hand isn't free for non-private users!!!!

And both of those work better if installed from the .deb files that are provided from their pages. (not from repositories.)

---

### Post by AndyCooll on 2007-08-28
Well ...pays your money (figuratively speaking) takes your pick.

For 3D gaming dual-booting is really your only choice. After that it depends on what you want to do and whether an app works with Wine (some do, some don't). You should always remember though that any form of virtualisation (and I'm using this in the broadest possible meaining here to include Wine) will mean some performance hit no matter how good the virtualisation app is.

I used to use VMware (the player is in the repos, Server needs downloading from the VMware site) and now occasionally use VirtualBox (which currently isn't in the repos but an Ubuntu deb can be downloaded from their website) to look at new distros. I have an XP Vmare image and formerly used it to play my Football Manager game. 

So ...for this one game, even booting into VMware, loading the image, and then the game was time-consuming. Thankfully, I've now got it working with Wine and I just click on the game icon and it boots straight up. And it runs at a speed comparable to that as if it was in a native Windows environment. For this one app Wine is the best solution for my purposes.

The moral of the story is that there is no one "wise" scenario, it really depends on what you want to do.

:cool:

---

### Post by notwen on 2007-08-28
I myself use Virtualbox.  Depending on what you need to do within Windows is the question.  Gaming is certainly worth dual-booting, other than that I believe a VM solution(Virtualbox or VMWare) is a perfect solution.  There are many very easy installs for both, I myself just have more luck w/ Virtualbox.  Good luck with whatever you decide.

---

### Post by chunchengch on 2007-08-28
Thank you all!

> **TeaSwigger said:**
> 
1 - What are the specs of your computer? If it's not more than 512mb memory, I do think you'd be far better served by either getting WINE working properly or dual-boot.


I have 1.5GB memory in my laptop with Duo T2250 (1.73 G) CPU, it should be more than enough, however, I don't know why the Wine 0.9.42 can not run smoothly on my laptop?

BTW, I don't play games, I just want to use Adobe Acrobat to modify my PDF files and to surf some IE-only websites.

---

