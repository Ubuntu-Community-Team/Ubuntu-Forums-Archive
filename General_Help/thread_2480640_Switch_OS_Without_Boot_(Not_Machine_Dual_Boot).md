---
title: "Switch OS Without Boot (Not Machine Dual Boot)"
date: 2022-11-04
forum: General Help
---

### Post by papertape on 2022-11-04
How do I switch between Windows and Ubuntu without rebooting the machine?

Using a virtual machine is not what I want.
I do not want two OS's resident simultaneously.
I wish to shut down the running OS and jump to grub, without going through the machine's POST and UEFI.

---

### Post by chiashurb on 2022-11-04
It sounds like what you want to do is have two operating systems both installed on bare metal, and to switch between them (shut down one and boot the other) at will without resetting the machine and going back through POST?  

I don't think this is possible.  Can you say more about why you want to do this?  Is it a matter of your machine having a long firmware boot cycle?  

One thought to achieve something *close* to what you want is to have a very light OS on the bare metal and run *both* your Ubuntu and Windows as VMs with all or nearly all your system resources allocated to each VM, so that practically only one can be active at a time.  This will get you something very close to (if not indistinguishable from) bare-metal performance on each VM, without the system firmware boot lag when you switch.  

If that's not helpful, you might want to say a bit more about your situation so that we an help you brainstorm a useful answer.

---

### Post by papertape on 2022-11-04
Thanks!
> **chiashurb said:**
> It sounds like what you want to do is have two operating systems both installed on bare metal, and to switch between them (shut down one and boot the other) at will without resetting the machine and going back through POST?  

Yep, though to be pedantic, I don't want to "boot" the other OS.  Rather, I want to get grub running.  (To me, "boot" is what the machine does when it is powered on.)

> 
I don't think this is possible.  Can you say more about why you want to do this?  Is it a matter of your machine having a long firmware boot cycle?   

Yep.  I don't know what it is doing, but I choose not to wait.

 > 
One thought to achieve something *close* to what you want is to have a very light OS on the bare metal and run *both* your Ubuntu and Windows as VMs with all or nearly all your system resources allocated to each VM, so that practically only one can be active at a time.  This will get you something very close to (if not indistinguishable from) bare-metal performance on each VM, without the system firmware boot lag when you switch.  

If that's not helpful, you might want to say a bit more about your situation so that we an help you brainstorm a useful answer.

I wish to switch between the two OS's quickly.  Waiting for Windows to shut down is nuisance enough, without waiting for unnecessary bootery.

---

### Post by dragonfly41 on 2022-11-04
Let us say you are in Windows desktop and I agree that Windows is a pain in shutting down.

You could create a remote virtual desktop Ubuntu environment and run that while in Windows.

I use a "pay as you go" (PaaS) jelastic host service and you could switch on the Ubuntu remote desktop environment while in Windows. And vice versa.

---

### Post by yancek on 2022-11-05
>   (To me, "boot" is what the machine does when it is powered on.) 

Switching from one OS to another is also "booting" and I am unaware of any standard method of doing what you want.  Using Virtual software would eliminate part of the problem, not going through the BIOS/EFI but it would not speed anything up as it will take at least as long to boot in a virtual machine.  Going through the BIOS/EFI will point to the respective bootloader on either OS and then boot it so a bootloader is necessary.

As to speed, how long does it take to boot?  What hardware do you have?  One thing that can be done is to change hardware to an SSD if you are not using one.  On my laptops, I have a SATA drive on one and an SSD on the other with the same OS's on each and the SSD machine boots each 4 times faster.  If you are already using an SSD, how long does booting take?  There may be some other problem.  Perhaps you could try the suggestion in the post above by dragonfly41.  I'm not familiar with that software or anything similar myself.

---

### Post by dragonfly41 on 2022-11-05
Revisiting this thread I wonder if this is just a "nuisance" problem or a genuine need to quickly switch between desktops (but for what purpose?).  I can see a scenario where you are forced to use Windows (for Windows apps such as Adobe) but then want to jump into Ubuntu. My old Canon scanner for example only works on Windows

Do you need the full power of a Ubuntu desktop or just an app?

I am an advocate of automation for repetitive or routine workflows and I regularly build scripts to jump between Ubuntu apps in "toolchains". I see no difference here.  If while in Windows you anticipate the need to jump into Ubuntu you could launch an automation script which prepares Ubuntu ready to jump into. That is a "count down" background automation script. In effect you run two processes in parallel.

Another ploy I have used is (if there are no security issues) is to call through your browser [https://www.rollapp.com/](https://www.rollapp.com/) and you can run Linux apps. But note that rollapp has a *.ru server. So I don't use that service. But it gives you ideas.

Yet another approach is to have two PC's running together, one Windows, the other Ubuntu, then use NOMACHINE to view their respective desktops. You can even run Ubuntu on a low cost Raspberry Py.

There are many options we can think up. But are they worthwhile if is this is simply a nuisance factor? How frequently do you need to switch? Is security an issue?  Should it be inhouse? And so on.

Using SSD is the easiest way as suggested above by @yancek. But you can combine multiple ideas.

---

### Post by MAFoElffen on 2022-11-05
I am an advocate of dual-booting, and of running virtual machines.

Grub "is" a boot loader... which rings up a boot menu to select which OS to boot... It depends on "booting". With SSD'es and NVMe's, my desktop reboots in seconds. Whereas my Server, being that it is a true server board, seems like it takes forever to boot or reboot.

The con to dual booting is that except for setting up shared data spaces, you cannot share information between systems... Because neither is "alive" at the same time.

Then comes where you can have both alive at the same time... Virtuals. Where you can have a host and a virtual machine or a subsystem. How I handle this is a Virtual host, where It can kick off or spin up VM's and connect to them remotely... That way, what I am viewing it from, is not affected performance-wise. I can share data between my remote-desktops.

Sub-systems, like WSL are still being worked out. Where both can exist at the same time, on the same machine, without as much resources as two, completely separate systems running at the same time. (Host and virtual guest.)

---

### Post by grahammechanical on 2022-11-06
> Sub-systems, like WSL are still being worked out.

I am already imagining the outcry if someone (that is Canonical) comes out with LSW - Linux Subsystem for Windows. :) :) I just cannot help laughing at that idea being considered acceptable to Linux users.

Regards

---

### Post by TheFu on 2022-11-06
> **grahammechanical said:**
> I am already imagining the outcry if someone (that is Canonical) comes out with LSW - Linux Subsystem for Windows. :) :) I just cannot help laughing at that idea being considered acceptable to Linux users.

Regards

WSL is a virtual machine, just highly optimized for 1 specific purpose.  WSL loses much of the wonderful things that a full Linux provides, not the least of which is a knowledgeable community.  I've only helped others with WSL and while it is capable, there are a few things that are just "off" about the environment.  It doesn't always behave like Linux should.  I'd always run a full VM with a real Linux distro under Windows, if I had that choice.

For the OPs question.  It isn't possible to run 2 OSes on the same machine concurrently without either a VM or a Linux Container.  Only 1 OS can control direct access to the hardware, unless you like spending millions on enterprise hardware that supports "domains", which are electrically separated components inside the same case.  Not possible in any PC that I know about.  Now, with Linux, we can run the main OS and both Linux Containers and VMs under that main OS. Linux Containers tend to be about 1/10th the hardware requirements of a full VM, sometimes even lighter.  IME, Linux VMs are very light when compared to MSFT VMs, but that's probably just the bloat that is MS-Windows being so heavy.

I've deployed a number of these devices inside enterprises a few decades ago.  Before virtualization became excellent, it was the "new thing".  I've never seen that available for x86-64 hardware, however.  We deployed nPARs on PA-RISC systems (Superdomes) and "Domains" on E10K, E12K (and larger) Sun Microsystems UltraSPARC servers.  These were very expensive systems.  On IBM Power Series servers, we'd use LPARs, but those are just virtual machines.

The main OS, the OS running on the hardware directly, is almost always the OS that needs the highest graphics performance, so it can have direct access to the GPU.  If a system has multiple high-end GPUs, it is possible to pass through the PCIe slot with a GPU for exclusive use by a virtual machine.  

They've been working on methods to share a single GPU with native performance between the hostOS and multiple guest VMs.  I've been seeing demos of this for about 7 yrs, but usually the demo crashes after less than 5 minutes.  Perhaps the Virgl or virtio-gpu [https://www.phoronix.com/news/Venus-Vulkan-1.3](https://www.phoronix.com/news/Venus-Vulkan-1.3)  methods are better now?  IDK.  There's always new work, but stability is an unknown to me.  I've never had multiple GPUs in a machine and never had high-end enough GPUs for the passthru to work into VMs.  Nobody tries to support my $50-$100 GPUs for these things.

---

### Post by papertape on 2022-11-06
I do indeed have SSD's.  One for Windows, and one for Ubuntu.
And I do need the full power of Linux.  (See Note.)

I don't need co-resident OS's, with each OS in memory.  Rather, it's good enough to shutdown and roll out one OS, and then roll in the other one.  I don't see why the machine has to do a POST to start the other OS, and then do another POST to get back.

Aside: I remember people talking about co-resident OS's in the 60's.  Perhaps IBM's, Microsoft's, and Apple's jealous monopolistic clutches blocked innovation.  There might be a business opportunity here.

Many thanks to everyone for your advice. 

Note: In 2015, when my attempt to "upgrade" from Windows 7 to 10 bricked my motherboard, I decided to fire Microsoft.  The sticky tentacles of Windows have threaded their way through my soul, what with Windows-only applications and my natural procrastination, but better now than later.  (I know, I know... An OS cannot brick a motherboard.  Don't bet your life on that.)

---

### Post by papertape on 2022-11-06
I just received an email from Quora titled "Stories from your activity".
It has several citations on the multi-boot question.
Presumably spies on the internet blabbed.
Anyhow, other people ask the same question.
One answer suggested going through hibernation. [URL="https://qr.ae/pv3Cvv"]https://qr.ae/pv3Cvv

[/URL]

---

### Post by TheFu on 2022-11-06
There have long been ways to break hardware from programs.  I don't think that has changed, just the specific ways and the specific hardware that can be broken have changed.  A few weeks ago, I saw a story about one of the display servers, I don't recall which, being able to push a monitor beyond limits and destroy it, if the wrong config was set.  I'm guessing that would only work on cheap monitors that don't do limit checking, but it could happen.  

There **is** a difference between a full IPL/BRS power off/on and a reset, even on our weenie Intel/AMD computers.  For the most part, the reboot time is still seconds, so it doesn't really matter.
For example, here's the boot time for my main desktop, which is actually running inside a full virtual machine:
```
$ systemd-analyze 
Startup finished in 2.301s (kernel) + 5.437s (userspace) = 7.739s 
graphical.target reached after 5.425s in userspace
```
I choose to use VMs for the tremendous flexibility they provide over running on hardware.
Whereas the host machine, running on real hardware takes:
```
$ systemd-analyze 
Startup finished in 10.180s (kernel) + 43.015s (userspace) = 53.196s
graphical.target reached after 12.811s in userspace
```
Give me the VM every time, please.  Part of the issue is that hardware gets checked when it is real. With a VM, we use the virtio drivers for storage and networking, so those are nearly instantly ready at boot.  The VM above is running on the exact same hardware as the host above, but boots 8x+ faster.  Virtual machines today aren't like they were in the year 1999.

Since around 2008, I've been getting 90+% of the hardware performance from VMs, so if that isn't your experience, check the configuration and get better at VM configurations.  The only area where I don't see VMs performing about the same as the raw hardware is when the entire capabilities of the hardware are required for the the workload, which doesn't usually happen, or when graphics performance is the mandate.  For everything else, I use a VM for the flexibility.  It doesn't matter to me if a batch job takes 15 minutes or 16 minutes to complete.  The extra flexibility of having a VM vastly outweighs any reduced performance.  With our base hardware having 4 cores and 16G of RAM and SSDs storage, hardly any real-world workloads will care about the extra capabilities.  Of course, this assumes all sorts of things that haven't been discussed or hinted in the OP.   

Of course, setting up and using VMs is all about efficiently sharing resources. When done well, it is seamless and works exceptionally well.  When done poorly, people will blame the hardware for configuration issues.  There are plenty of articles written about tuning hypervisors for performance with some of the easiest things providing huge gains.  I think most are the defaults these days in the hypervisors, but not always.  I've run lots of different hypervisors over the decades and learned how to tune most of them reasonably well assuming over committing resources isn't the goal.  Sharing the hardware between all the running systems, VMs and the host, is important.  I've seen Core i7s misconfigured behave terribly and I've seen low-end Core2 Duos handle 20 concurrent VMs exceptionally well.

Often, having the steps to the desired outcome in a hindrance for getting the best advice.  For my first few years on Unix systems, I'd try to figure out the 10 steps to solve a problem and ask about each 1 of those steps.  Around question 5, someone would see my questions and ask what my end-goal truly was, so I'd say it and they'd produce a 1 line command that did it, skipping 8 of my steps.  Sometimes getting the best advice on the final answer is all we can do, unless we are a systems programmer.  Some solution is better than no solution, right?

---

### Post by QIII on 2022-11-06
You are encountering a condition brought about by the nature of the design of personal computer hardware.  For you to get to what you want, two bare-metal OSes installed on the same machine with a swift switch between them without power off between, you will need to seek the help of OEMs.  You might be able to get to something that looks an awful lot like you are not powering off, but you wouldn't quite be there.  I'm not talking necessarily about a power down where the PSU goes dark or a click of the power button.  Just a re-energizing of the mobo.  The PSU and motherboard can do that easily enough.  I suspect that OEMs will not respond quickly to your idea as stated, as that would be achieved only at great cost -- and there are already other ways to have two systems running simultaneously, or switching between two installed OSes, and avoiding the issue.

You'd still have to use the facilities provided by each OS to reboot to get to a boot loader and choose the other OS. But that's a dual/multiboot still.

In the following I may talk about "power off", but remember that there is a difference between de-energizing/re-energizing the mobo and a full-on power cycle of the PSU.

With regard to your link, there is nothing new there.  When you shut Windows down, it enters a hybrid hibernation mode with the cooperation of the hardware.  You can set your hardware to skip a POST at next startup.  Those things together make it appear that Windows magically boots instantly, but it is nothing more than a clever ruse.  It simply resumes from hibernation without first doing the POST checks that provide you with some measure of safety should there be a hardware fault.  You could do something similar with Ubuntu.  In each case, it might appear that you were switching nearly instantaneously between two installed OSes, but you would still really be re-energizing, maybe skipping the mobo splash, skipping POST and resuming from the point of hibernation (or sleep if you want things to start where you left off).  That might happen pretty quickly, especially with NVMe devices handling the memory state storage, but the OSes would not be "shutting down and swtiching" without a power off step, at least at the point of mobo re-energization.  There would be considerations about the state of the Windows OS drive (if not fully unmounted, Linux will consider the device to be in a read-only state -- to avoid any potential corruption associated with changing the contents without Windows looking.)  There is also the consideration that a "hibernation/sleep file" for each system would have to be large enough to contain the entire contents of the installed RAM if you wanted the switch to return to the other OS where it left off, so each system would need a rather sizable chunk of storage device real estate to be set aside if you wanted to switch between sleep states and retain your work.

One has to ask why, if what you want can be done with consumer grade hardware without a power off, has so much effort been put in by those who created virtual machine products.  Surely if what you want to do were possible on hardware, there would be no, or at least a very diminished, market for VM technology.  Why would enterprises use VM technology?  Why would I have before I turned over the operation of my software company to family so I could retire?  The big thing for us would have been an exorbitant cost associated with bespoke or rare hardware to allow such a thing.  Why would OEMs produce such a thing for anyone but those willing to buy a one-off piece of hardware for the price of a small country?  They make a lot more money doing things the way they are.  Why would anyone bother with creating avenues for multi-booting?

On the machine I am typing from now, I have enough cores (64 threads) and memory (256 GB) to run dozens of very powerful VMs simultaneously.  Even that cost a pretty penny, but it was done for business research.  I had built this machine initially so that I could test client processes in a microcosm of an enterprise.  I am limited to 13 besides the host OS because that is how many NIC ports I have on the machine (an extra on the mobo and 3x4 port cards) and I want each VM to have its own direct connection.  Do you think a hardware manufacturer would have any luck selling me on a motherboard that would cost more to make for one customer than the entire US Apollo program cost?

So -- do you really not want a power-down/power-up step, or do you really just not want to have to notice that it is happening?  The former would cost you more money than you could muster.  The latter already happens with multi-booting if you use the "restart" button in the OSes to get back to the boot loader after the mobo is re-energized.  You don't need to fully shut it down so that the PSU goes dark or even hit the reset button.  Two different things happen there, see TheFu's post above.  VMs provide the advantage of running simultaneously, switching at the blink of an eye and, in some cases, allowing C&P across the OSes.  Very convenient, that. 

Please.  People like TheFu and others have been around and around this question for many, many years.  Hearken to their tuition.

---

### Post by QIII on 2022-11-06
By the way, if you want really good graphics when using something like KVM as your hypervisor for virtual machines, you can add a second video card and let the guest take control of that one.  Don't try that with only a single GPU, or you could find yourself without any I/O on the host while the VM is running.

---

### Post by HermanAB on 2022-11-08
Gnome Boxes is in the repos.  It is a front end for the KVM virtualizer built into the Linux kernel.

---

### Post by TheFu on 2022-11-08
> **HermanAB said:**
> Gnome Boxes is in the repos.  It is a front end for the KVM virtualizer built into the Linux kernel.

There's also MultiPass, if you want a snap-based KVM manager.  I've never gotten it to work, but snaps seldom work on my systems.  Maybe Gnome Boxes defaults are reasonable now, so that could be an easier hypervisor manager.

---

