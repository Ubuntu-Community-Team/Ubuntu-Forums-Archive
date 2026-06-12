---
title: "Lubuntu can run Windows programs and is possible add MATE ?"
date: 2020-07-07
forum: General Help
---

### Post by aug7744 on 2020-07-07
Hello. The number of Linux versions and distributions make difficulties to choice what is the good version for me. I'm a Windows advanced user and I dislike how Windows manage memory and the pagefile.  MATE look to be an good desktop. Is possible add in Lubuntu ?  Lubuntu can run Windows programs ? WINE support is good ? Is possible run Adobe Premiere CS 2018 and Photoshop CS 2020 ? Is possible when starting the system create an RAM Disk and put the Linux swap file in that RAM Disk drive avoinding create an swap partition ?  Thanks for read my post and have an nice week.

---

### Post by guiverc on 2020-07-07
Welcome to Ubuntu Forums.

You mention MAME (*an arcade emulator as I recall*), which I take it was a typo, as your heading mentioned MATE.

You can install a second desktop, eg.  Lubuntu's LXQt, and Ubuntu-MATE's MATE desktop installed on the one desktop & partition, and select at login if you want to use a different one to last time.    I personally love the idea of selecting which desktop I want to use (*this system has Lubuntu's LXQt, & Xubuntu's XFCE, & Ubuntu's GNOME desktop installed*), but there are costs involved with it. 

 If you're new to using any GNU/Linux system, I'd suggest you start with only a single desktop (esp. if efficiency matters, ie. MATE's GTK3 and Lubuntu's LXQt Qt5 won't share many resources.. though if you've enough RAM it matters less).  You can download them, write them to thumb-drives & 'test' without install (ie. running them on a 'live' system).

WINE support in any Ubuntu flavor is about the same as any other GNU/Linux I believe (better than some), but I won't provide much detail there, as I've not used WINE in years.

Creating a RAM disk, and putting swap there would be a waste as far as I can see. Depending on which release of Lubuntu you install, you may get no swap file/partition at install, but a swap file being written to a RAM disk will provide no benefits but still waste the overhead required to create/run the RAM disk (ie. you're better without RAM disk being created/used and having no swap file at all).

Do you need a swap file?  That's not easy, as it'll depend on a number of factors, but it can be of great benefit...  Modern Lubuntu will also use swap files on disk (hdd/ssd), though maybe this is what you meant?  Some releases of Lubuntu don't actually create a swap partition/file automatically, you do it if you feel it's necessary.

What release of Linux is best, or what flavor of Ubuntu is best - in the end is a personal choice, and only you can decide. It's like selecting what flavor of ice cream is best.  (*me I can't decide; why I have three desktops installed on my box; even if I use one far more than the others*)

---

### Post by ActionParsnip on 2020-07-07
You can install as many desktop environments as you like and select which you like when you log in.

---

### Post by aug7744 on 2020-07-08
@guiverc and ActionParsnip. Thanks very much for your reply :)

  "You mention MAME (an arcade emulator as I recall), which I take it was a typo, as your heading mentioned MATE."
 Fixed. The correct is MATE :)

  I dislike how Windows 10 manage the memory and the pagefile. In Windows 10 if you disable pagefile will less memory free even not swapping in disk because the system need pagefile only to allocate memory and thus has better management and ram compression. The problem is that Windows use pagefile swaping ram memory to disk even having very much free memory.
 If you install an RAM Disk using an ramdisk utility that has an option to allocate ram only if using you can create an ramdisk of 8 GB and put the pagefile selecting pagefile min size 16 MB and max 8192 GB. If Windows allocate 4 GB for pagefile and is using 400 MB only 400 MB in RAM is being used and thus you has more memory and yet compression avoiding writes in disk, but need care to avoid several programs at same time. Need also use an good memory utility that remove memory standby list when reach at limit to avoid swap data. That's great to SSD :)
 I use here in an HDDD without problems or crash :) In moment total system memory used is 2,46 GB (plus antivirus, firewall, broswer and few utilities). Linux perhaps use much less memory.
  Perhaps is possible to create all above in Linux and if Linux compress data in pagefile or is possible format and ramdisk with compression the pagefile can be compressed. Need test it.
 Now if Linux not has the same problem that Windows of need an pagefile only to allocate memory even not using perhaps an swapfile can be disabled for use only with emulators, internet and word edit softwares.

  An detail strange is that has distros using funny names. Mint, Mate and etc. One being using an name "car 6 gears" and after other create "airplane".

  Slackware look to be very good, but is much time to configure and understand.
 Oracle Linux use much RAM and look very good also.
Both not are the Linux that I wait to use.

  Lubuntu install and configuration is totally using GUI ? If yes also is possible use text or command line ?  Lubuntu X64 iso is more of 1,5 GB. That ISO has only the system and os components or third software ? I want install Linux not having several software in ISO because of size and also make not sense having and Firefox version that after will be outdated.

I'm seeing that Linux can run even Adobe and others windows softwares I not will use Windows thus switching to Linux.

You think in use Windows after your experience using Linux ? You was an Windows user ? What is your experience ? Linux is much more fast or only an bit more fast than Windows ?
I wait that Nvidia driver has good support in Linux because Linus hate Nvidia ... Have news in internet about it. Strange Nvidia not giving same support level to Linux thus how does in Windows.

---

### Post by guiverc on 2020-07-08
MATE is a desktop, and the word isn't english but "[&#712;m&#593;&#720;te&#618;]("https://en.wikipedia.org/wiki/Help:IPA/English")". a South American plant/herb that is commonly consumed as a caffeinated beverage (like tea).  [https://en.wikipedia.org/wiki/MATE_(software)](https://en.wikipedia.org/wiki/MATE_(software))

Ubuntu-MATE is the Ubuntu base, with the default desktop (GNOME) and default programs replaced by MATE desktop & applications.

Almost of Lubuntu settings can be performed by a GUI, but little parts (eg. `sddm` or the configuration settings for the display manager used by Lubuntu) are best via command line, or in that case an editor.  For Lubuntu I'd suggest you browser the manual - [https://manual.lubuntu.me/stable/](https://manual.lubuntu.me/stable/)

I can't speak to windows personally, I haven't used it in years (the last windows machines I supported was XP), and I'd used unix before the first version of windows was released, so GNU/Linux to me is just *modern* unix.

I won't provide anything about your use of ramdisk/swap-on-rd as I've had no experience with it and don't know (most of what I said was from OS theory I read about back at school and later on courses). I generally don't worry about RAM usage, unless I'm using a box with 4GB of ram or less and then it's mostly trying to use apps that use libraries already in memory (ie. used by desktop), but that applies to any OS (windows, osx & GNU/Linux).

---

### Post by aug7744 on 2020-07-09
I say MATE because is how MATE has better resolution compatibility than Lubuntu default desktop.
Thanks very much about the install information ink :)

Years using Unix and not need to use Windows ? LUCKY :)

Adding RAM Disk is good to temporary files if you not use extremely the RAM.
I wait to use Linux with video editing and old console emulators. I not wait to use current console emulators or current games.
If is possible to run Adobe and Vegas Pro I will remove Windows from my machine.
The problem is that are several distros that is hard to understand and test what is the exact OS for me. In moment I will try Lubuntu and if has very good speed and stability (not crashing extremely) will continue to use Lubuntu.
Others distros ( mainly for gaming and multimedia) has much detail that for me not does the OS to be simple to use.

Lubuntu ISO is only the OS or is added others softwares (firefox etc) ? I want to download an Lubuntu ISO current version without third softwares.
Where I can download an ISO with only OS components ?
Thanks.

---

### Post by guiverc on 2020-07-09
The Lubuntu ISO includes the Ubuntu base & `lubuntu-desktop`, which for *focal* includes all packages found on [https://packages.ubuntu.com/focal/lubuntu-desktop](https://packages.ubuntu.com/focal/lubuntu-desktop)

The leanest Lubuntu would probably be best achieved by starting with a plain Ubuntu ([mini.iso]("http://archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/current/legacy-images/netboot/mini.iso")) then adding `lubuntu-desktop` **without** the recommended packages..  *I used the word probably because I've not installed it that way.*

---

### Post by aug7744 on 2020-07-14
Lubuntu distro is an Ubuntu base without default desktop + all packages from link ?   If yes mean that is a OS where i can add components of my choice ?  The Ubuntu ISO from link is an installer with GUI ? Is possible add any package in Lubuntu in offline mode without an internet connection ?   Nothing above is exactly possible in Windows.  Linux look to be much more advanced than Windows even.  I here will try Lubuntu testing in an Virtual Box before of full install on disk.   Thanks very much  Have an nice week :)

---

### Post by rsteinmetz70112 on 2020-07-14
> **aug7744 said:**
> Lubuntu distro is an Ubuntu base without default desktop + all packages from link ?
Yes
>    If yes mean that is a OS where i can add components of my choice ? 
Yes but usually components are added from the Internet.

>  The Ubuntu ISO from link is an installer with GUI ?
Yes the ISO boots into a live session one of the options is to install Ubuntu or lubuntu or whatrever version.
> Is possible add any package in Lubuntu in offline mode without an internet connection ?
It is possible but you must first get the packages form somewhere. The ISO does not include every package and updates are delivered over the Internet.
>   Nothing above is exactly possible in Windows.  Linux look to be much more advanced than Windows even.  I here will try Lubuntu testing in an Virtual Box before of full install on disk.   Thanks very much  Have an nice week :)
The ISO boots into a live session you can try Linux from there without installing it. You can try different versions from different ISOs to see which one you like.

Earlier in this thread you mentioned using some Windows software in WINE, you should check to see if the specific software you want to use will work in WINE, not every package does - most popular software does work but specialized packages may not. 

Also you mentioned a swap file - they are no longer required. The common recommendation is to install enough RAM so you won't ever use it, the current default for Ubuntu is to make a swap file if necessary or desired, but on my computers it is seldom used, although if you are doing video editing it may become necessary.

---

### Post by aug7744 on 2020-07-15
I have downloaded the ISO from [http://archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/current/legacy-images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/current/legacy-images/netboot/mini.iso) Started the install, but not progress how if is requiring package from internet. The machine is offline. Is possible add manually packages from [https://packages.ubuntu.com/focal/lubuntu-desktop](https://packages.ubuntu.com/focal/lubuntu-desktop) in the mini.iso ?  That mini.iso not is an version that install without internet access and after I can add manually the packages ? Hmm is possible add packages in any Linux distro ISO without need internet access ?

---

### Post by Holger_Gehrke on 2020-07-15
The problem with adding packages manually is dependencies. If you take a look at a package with 'apt show *packagename*' you'll see a list of other packages that this one needs to work. And those packages might need other packages which need other packages which ...  If you're installing with an internet connections, this is taken care of automatically, the installer goes through the chain of dependencies and installs everything that's needed. If you're trying to do it manually it gets really complicated quickly. There are tools to make it less problematic (synaptic (GUI) offers to create a script for you which you can run on another internet connected machine to download everything you need, aptitude can probably do something similar and there's also something called apt-offline), but since these are not installed by default and need to be installed from the internet you've got a chicken-and-egg situation here.

Also, the mini.iso is a very bare-bones variant that comes without any GUI AFAIK. It's not beginner-friendly and not meant to be. It's for people who know their way around the system and want a maximum of control over what exactly gets installed.

Holger

---

### Post by guiverc on 2020-07-15
There are many choices of ISO available.  

The *mini.iso* I provided is also called the netboot ISO, ie. it's assumed to be on a network, is ideal for diskless/thin-client like devices booted from network & everything gets downloaded from the main online mirrors, **or** a local (offline) mirror managed locally (but synced from online mirrors).

It's my understanding the mini.iso does not include a GUI, as GUI desktops are only found on desktop ISOs. You can add a GUI yes, but it's added during or after installation.

 A server ISO contains more than the mini.iso, however will include server configurations, software not found on desktop ISOs (`openssh-server` for example, desktops contain client ssh software only) but without desktop/GUI software thus are still leaner. Finally there are multiple desktop ISO choices.

If you want everything - starting from a server or desktop ISO makes a lot more sense to me if you're off-line, as it's already included.

My answer was because you asked 
> **aug7744 said:**
> 
I want to download an Lubuntu ISO current version without third softwares.
Where I can download an ISO with only OS components ? 

ie. the mini.iso is the minimum necessary; the rest gets added subsequently if desired/needed.I don't use mini.iso installs, as I start with a desktop ISO, then adjust from there.

---

### Post by TheFu on 2020-07-15
I didn't read everything in this thread, but have some experience trying to get WINE to work with complex commercial product.

After a few years using the product under WINE - it never worked 100%, only about 80% of it worked, I gave up and have been running that software under Windows in a virtual machine ever since.  It wasn't a video or image tool, so the added layers to between the program and the screen were/are unimportant.

For Windows programs that have a heavy GPU requirement, there are only 2 viable answers, IMHO. WINE is not part of either.
[LIST]
[*]Run those programs on Windows and dual-boot.
[*]Run Windows inside a virtual machine hypervisor, on the specific hardware which supports GPU passthru, and meet all the requirements for that (1 high-end video card dedicated to Windows-VM, IOMMU enabled, sufficient RAM, sufficient CPU, sufficient HDD).
[/LIST]

Every update for WINE can break a working Windows program. Beware.
Similarly, every new kernel will break the GPU passthru to a Windows virtual machine.  The good news for this method is that many people are running this way, so the required motherboard, required GPUs, and required hypervisors are fairly well understood at this point.  In general, the GPU will need to be US$300 or more. Cheaper GPUs don't get the needed instructions.

If I were trying to get commercial adobe products to work, have a dedicated Windows computer just for those. The only reason to have Adobe anything is if you make your living using those things. That software costs more than the computer needed to run them, so just get a dedicated computer with 16-32 Cores and 16-32GB of RAM, then add as many SSDs as you need to hold the temporary video files and get a cheap $600+ NAS device to hold the non-temporary work files.

If you aren't or won't be earning a living from the Adobe software, then just start using the professional-grade Linux tools instead. There are many video editors and The Gimp for images.

IMHO.

---

### Post by aug7744 on 2020-08-09
Thanks for all replies.

---

