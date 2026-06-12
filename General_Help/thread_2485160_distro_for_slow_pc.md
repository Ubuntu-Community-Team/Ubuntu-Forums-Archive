---
title: "distro for slow pc"
date: 2023-03-21
forum: General Help
---

### Post by guest123487 on 2023-03-21
What distro can I install on a celeron &#8203;with little ram and that can install updated browsers and updated programs?
thanks

---

### Post by Impavidus on 2023-03-21
A little more information might help.

What CPU is it exactly? There are several generations of celerons. And how much RAM? A modern browser may not even run on an old computer, even if the OS does run.

If you're unsure, there are some diagnostic commands. For example,```
sudo lshw -sanitize -c processor
sudo lshw -short -sanitize -c memory -c display
```The -sanitize option removes potentially sensitive information. You can run this from a live disk, even a very old one. In that case, just don't connect to the network.

---

### Post by DuckHook on 2023-03-21
Please post only with default fonts and styles. Unusual formatting makes your posts difficult to read on small screens and offends netiquette as a form of shouting.

To answer your question, we need more information.

Please provide details of your HW including:
[LIST]
[*]Is CPU capable of 64 bit?
[*]How much RAM is installed?
[*]What is your graphics subsystem?
[/LIST]
Please provide sufficient info for us to help.

Have a look at the link in my sig: "The Best 'buntu Flavour"

---

### Post by guest123487 on 2023-03-21
```
cpu                   
       description: CPU
       product: Intel(R) Celeron(R) CPU          530  @ 1.73GHz
       vendor: Intel Corp.
       physical id: 4
       bus info: cpu@0
       version: 6.6.1
       serial: [REMOVED]
       slot: U2E1
       size: 1730MHz
       capacity: 1730MHz
       width: 64 bits
       clock: 133MHz
       capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm




H/W path        Device      Class       Description
===================================================
/0/0                        memory      105KiB BIOS
/0/4/5                      memory      64KiB L1 cache
/0/4/6                      memory      1MiB L2 cache
/0/10                       memory      1536MiB System Memory
/0/10/0                     memory      512MiB SODIMM DDR2 Synchronous 533 MHz (1,9 ns)
/0/10/1                     memory      1GiB SODIMM DDR2 Synchronous 533 MHz (1,9 ns)
/0/100/2                    display     Mobile GM965/GL960 Integrated Graphics Controller (primary)
/0/100/2.1                  display     Mobile GM965/GL960 Integrated Graphics Controller (secondary)
```

---

### Post by DuckHook on 2023-03-21
With these kinds of specs, you are unlikely going to be happy with any of the 'buntu flavours.

This sort of machine can still be useful if you run it as a server with no GUI overhead, but even Lubuntu (the lightest GUI flavour) will be very sluggish and will often run out of RAM and crash. In your case, the GPU probably steals RAM for its graphical memory which only makes matters worse.

You can try a different distro altogether like Puppy Linux, but note that these days, the OS is only a part of the larger problem: a modern browser alone requires something like 1GB and a decent GPU. You can try running a lighter browser, but you will find the experience quite frustrating.

I used to be quite enthusiastic about salvaging old HW and repositioning them for alternate use, but those days are now behind us. If you calculate the extra power usage alone, that strategy has become inefficient and outdated. Linux is powerful and flexible, but it is not magic.

Under no circumstances should you be loading an ancient, obsolete version onto this machine. Doing so will turn you into a menace to the computing world. Repositioning it as a command line server is your best bet.

---

### Post by ne29914 on 2023-03-21
It's borderline for a lightweight distro, eg, Lubuntu or Xubuntu. Mate might also be an option. Don't even think about std. Ubuntu.
You'll need to upgrade RAM to at least 2 GB.

---

### Post by guiverc on 2023-03-21
I still use old *pentium M *laptops from 2004-2005 on occasion, and they have only 1GB of RAM (*sometimes 1.5GB*), but I don't think there is a *'best'* OS for any machine.

On hardware with limited resources; you need to consider firstly what apps you'll use, what libraries or toolkits they'll use, THEN pick a desktop that will use those same libs/TKs so you're not wasting RAM.  ie. the *flavor* to me is decided as a consequence of the apps you'll use.

In the last 48 hours I've used an old IBM Thinkpad pentium M box (*i386 only; so 32-bit x86*; 1.5GB RAM) and I have multiple desktops installed on it; including Lubuntu, Xubuntu and more. It's currently running 18.04 (*the last OS that supports i386*) though will soon move to running Debian... but my point here is I have multiple DEs installed & select which I'll use in a session based on what apps I'll use in that session.   My box has far more disk space available (*so I don't care that Lubuntu, Xubuntu & more exist on disk*) & login using the DE that will use the least RAM during my session, or if I don't consider there will be a difference - which best suits my mood.  (my system isn't dual boot, just multiple-desktop/WMs are installed selected at login)

When I saw "*celeron*" I *winced* though, those boxes are usually *underpowered* and the specs, whilst correct, are often misleading.  On many boxes video cards include at least some of their own memory; on boxes using celeron they don't (*thus RAM available to the OS reduces*), it's a 533MHz CPU but marketed at 1730MHz etc.. 

On boxes with less RAM, choosing your apps will be important.

Use a WM (*window manager*) and not a DE (*desktop*). 
Use apps that share resources with each other, and are light on the resources.

When browsing the web on *i386* devices, I'm often opting to use `lynx` as a browser, as its super fast (*it's text only! so you're using the internet like we used back in ~1992 before it was common*), but as I mostly want to read the text I have no issues with it. I do *stream* videos etc too (*using a normal browser*) but I'm using that machine very differently to how I use more modern boxes, and consider what is already in RAM & often close things down before starting new apps so performance stays *high* (*I do this on any box with <2GB RAM*)

I concur with @DuckHook's suggestions the most.

---

### Post by BBQdave on 2023-03-21
> **guest123487 said:**
> What distro can I install on a celeron &#8203;with little ram and that can install updated browsers and updated programs?

I am sorry to say, that is a conflict that can not be overcome. Even if you find a super light weight distro, the moment you add a browser or other updated applications you will tank your system.

As mentioned before, you could use the hardware as a server, administering from the command line.

Old hardware can make great file servers, backing up your data. Or you could pull the hard drive and put it in an USB case, portable backup drive.

---

### Post by MAFoElffen on 2023-03-22
This wouldn't happen to be an old HP G7000 notebook? Just seeing those spec's reminds me of them.

It it were mine, Ubuntu Server Edition 22.04. Then install lxqt-core.

Spun up a Penryn (class 2) CPU KVM VM with 1536MB RAM...

The Server Live installer pegged the memory on the initial install, but it did install. It just took a while. That is a challenge with the current Server Live installer on limited memory. The installer log status is going to look like it is hung at "curtain command target"... But it is not hung. Just still working on it... LOL It took about a half hour before it took off again and finished the install.

As Ubuntu Server (console) it was somewhat responsive. With a load average of 2.01, on what I threw at it, it was still only running at about 900MB of memory used.

Installed lxqt-core, sddm, and falkon web browser... Well, when apt upgrades or installs packages, when it does the unpacking process, it's going to almost peg that 1.5GB RAM and take a while. About an hour.

But once it is installed, it runs pretty fast. See attachment...

---

### Post by BBQdave on 2023-03-22
> **MAFoElffen said:**
> Spun up a Penryn (class 2) CPU KVM VM with 1536MB RAM...

Installed lxqt-core, sddm, and falkon web browser... Well, when apt upgrades or installs packages, when it does the unpacking process, it's going to almost peg that 1.5GB RAM and take a while. About an hour.

But once it is installed, it runs pretty fast.

That is some magic MAFoElffen, I am amazed :)

---

