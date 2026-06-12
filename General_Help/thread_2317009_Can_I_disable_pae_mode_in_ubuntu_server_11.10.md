---
title: "Can I disable pae mode in ubuntu server 11.10?"
date: 2016-03-12
forum: General Help
---

### Post by artss2 on 2016-03-12
My intel processor cannot support pae mode so I cannot use pae- ubuntu. It seems that ubuntu server 11.10 or 10.04 should support non-pae. I use ready vbox ub. server image so after launching it show ...u.s. 11.10 generic pae option  and recovery mode one. So could I use recovery consol to disable pae?? Or any other way? As far as I remember to enable pae we can use "forcepae", so are there any commands to disable? (but maybe 10.04 and 11.10 version have just pae mode, so maybe my assumption is incorrect?)

---

### Post by Bashing-om on 2016-03-12
artss2; Ouch.

Release 11.10 is way End_Of_Life and has no support. The supporting software structures have been turned down.

The good news is that the current 14.04 lubuntu release supports non-pae installation.
See:
[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)
[http://ubuntuforums.org/showthread.php?t=2211590](http://ubuntuforums.org/showthread.php?t=2211590)
[http://ubuntuforums.org/showthread.php?t=2263647](http://ubuntuforums.org/showthread.php?t=2263647)

You are encouraged to install the current (L)ubuntu 14.04 release.

[INDENT][INDENT]beating dead horses
[INDENT][INDENT][INDENT]does no one good
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by grahammechanical on 2016-03-12
I would not say that forcepae enables PAE. It used used for certain old CPUs like Pentium M that have PAE capabilities but do not show a flag saying so. This causes the installer to refuse to install. The forcepae boot parameter in effect causes the installer to ignore the lack of a CPU PAE flag and install anyway. It forces the install. This is my understanding.

> A number of older [Pentium M]("http://en.wikipedia.org/wiki/List_of_Intel_Pentium_M_microprocessors")  processors produced around 2003-4 (the Banias family) do not display  the PAE flag, and hence a normal installation fails. However, these  processors are in fact able to run the latest (and PAE-demanding)  kernels if only the installation process is modified a little. The  problem is not missing PAE, it's about the processor not displaying its  full capabilities.

[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

So, it is not a case of disabling PAE functions in the Linux kernel but of using a Linux kernel that has been compiled to run on a CPU that does not have PAE capabilities. That is a non-pae kernel.

[https://en.wikipedia.org/wiki/Physical_Address_Extension](https://en.wikipedia.org/wiki/Physical_Address_Extension)

[http://askubuntu.com/questions/117744/how-can-i-install-on-a-non-pae-cpu-error-kernel-requires-features-not-present](http://askubuntu.com/questions/117744/how-can-i-install-on-a-non-pae-cpu-error-kernel-requires-features-not-present)

Regards.

---

### Post by Bucky Ball on 2016-03-12
*Thread moved to **General Help**.*

> **Bashing-om said:**
> artss2; Ouch.

Release 11.10 is way End_Of_Life and has no support. The supporting software structures have been turned down.

^^^
This.

Suggest you install a supported version. Your machine hasn't had updates in literally years, and that includes security updates. At this point, I'd be starting to get concerned about having this machine online.

---

### Post by goofprog on 2016-03-12
I believe PAE is compiled in the kernel.

---

### Post by artss2 on 2016-03-13
So, can I forcepae during launching the pae-kernel on my non-pae cpu?

---

### Post by sudodus on 2016-03-13
If your computer's CPU can manage a PAE kernel, but has no PAE flag, fine, you can use ***Lubuntu 14.04.1 LTS*** and later releases. Use the boot option **forcepae**, as described in earlier posts in this thread.

See also the following link: [AdvancedMethods#Pentium_M_and_Celeron_M](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M)

If your computer's CPU can ***not*** manage a PAE kernel, you cannot use Lubuntu 14.04.1 LTS, and no other linux distro or re-spin based on Ubuntu 14.04 LTS, because there is no non-pae kernel, at least no *official* kernel.

Please tell us about your computer and in particular, about the CPU (brand name and model) :-) Then we can help you find a suitable linux distro or re-spin based on Ubuntu or maybe not based on Ubuntu.

Non-pae alternatives:

***Debian Jessie*** and distros or re-spins based on Debian Jessie, for example ***ToriOS Debian***.

***Wary Puppy*** and ***Tiny Core*** are two ultra-light linux distros.

See this link for more details: [Old hardware brought back to life](http://ubuntuforums.org/showthread.php?t=2130640)

---

### Post by artss2 on 2016-03-13
My cpu - intel pentium 4 2.8 ghz. Anyway I need ubuntu server for packet sniffing, as  desktop one returns permanently - "no suitable device found". So my main question is do ubuntu server 10.4/11.4 support non-pae mode? Where I can check which ubuntu server distributions support non-pae on official websites?

---

### Post by sudodus on 2016-03-13
I am rather sure that your Intel pentium 4 2.8 ghz works with a PAE kernel. I have such a CPU (in a Dell Dimension 4600). All Pentium III and Pentium 4 have PAE capability and also a PAE flag. You need no forcepae boot flag :-)

Do not use the versions 10.04 or 11.04! They have passed end of life and there is no support, no security update, nothing.

I suggest that you install Ubuntu Server ***14.04.1 LTS***.

Edit: Your problems might also depend on the graphics. Please tell us about the graphics chip/card (brand name and model) :-)

---

### Post by artss2 on 2016-03-13
I tried to define if it is pae. But windows service when launched and checked do not have the line which should show is it pae or non-pae. So how I can force pae at using at least live ubuntu cd mode? As when I boot from bootable 12.04 ubuntu pangolin the initial boot is very long and when screen for choosing demo or full install appear, and language list, i got mouse hanging and the whole booting... 2. My main issue is that desktop ubuntu gcc compiler returns "no suitable device found" so I hope that server could be behaving otherwise. 3. And about graphic card: the low 3.3 v (2.5 v sometimes) brings black screen but I do not know is there connection between this one and cpu overheat (70-80 Celsius), and should I repair motherboard or power box ATX for  3.3 v stabilization?

---

### Post by sudodus on 2016-03-13
You need not 'force' pae. Use an iso file with a pae kernel, and it will use pae automatically. Maybe your problem is due to low amount of RAM or graphics.

Try Lubuntu 14.04.1 LTS or Ubuntu Server 14.04.1 LTS.

Please specify as much as possible about your computer! You have told us about the CPU, but if you tell us more, it will be easier to help :-)

- Brand name and model
- CPU (we know: Pentium 4, 2.8 GHz)
- RAM (size)
- graphics chip/card
- wifi chip/card

---

### Post by sudodus on 2016-03-13
I don't know much details about power supply units, but I know, that it can cause severe problems. Maybe your problems would be solved if you get a good power supply unit (it could be a used 'second hand' unit from another old computer).

---

### Post by artss2 on 2016-03-13
My memory is very low just 512 mb. But xubuntu 12.4, ubuntu 10.4 boot fine when i have made vbox image and use just 256 mb. So why my ubuntu 12.04 boot fails, hangs when it have full of 512 mb. So here you can assume why it hangs at second step due to low memory or pae absence. // my power supply is already second hand got from another pc, from repair master

But my vbox machine apparently do not support pae when loading ready images so why it did not appear automatically

---

### Post by sudodus on 2016-03-14
Have you tried to run Ubuntu in the computer itself or only in a virtual machine?

Maybe if you are running the virtual machine in Windows, and Windows is a non-pae system, you cannot have a pae virtual machine. But if you are running the virtual machine in a pae host system (Windows or linux), you can select pae or non-pae as one of the settings of the virtual machine. (I have used that setting in the menus of VirtualBox, so I know it is there.)

Can you ***try*** to run a live ***Lubuntu 14.04.1 LTS*** or ..., or ***Lubuntu 14.04.4 LTS*** system booted from a DVD disk or USB pendrive. See this link:

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

If it works live, it should also be possible to install Lubuntu alongside Windows. And you will have much more 'horsepower' when running in the computer itself compared to running in a virtual machine.

---

### Post by artss2 on 2016-03-14
I wiil try today (but not now) to launch ubuntu 14.04, but not lubuntu 14.04 that is far smaller then ubuntu (and lubuntu is very bare, there are the nessecity to install a lot,  even for gcc compiler that I need in my case). Indeed i do not know is the lubuntu fake-pae the same as ubuntu force-pae, what is better? Meanwhile here is my processor (probably) description -- [http://download.intel.com/design/Pentium4/datashts/29864312.pdf](http://download.intel.com/design/Pentium4/datashts/29864312.pdf) -- and it has no info about pae. So I will try to find it out by coreinfo or maybe to include "/pae" key inh boot.ini.
As well I need to know exactly do such ubuntu servers as 10.4 and 11.4 supports non-pae?

---

### Post by sudodus on 2016-03-14
Under the hood Lubuntu and Ubuntu are the same. Only the graphical desktop environment and the selection of program packages differ. But this makes a big difference. With a Pentium 4 CPU and 512 MB RAM you can barely run a current version of Lubuntu. Ubuntu needs much more CPU horsepower, more RAM and (probably) also a more powerful graphical chip/card.

The Ubuntu operating system has developed in order to match the development of the computer hardware and the tasks that people expect a computer to manage. This means that standard Ubuntu is made for new and middle-age computers. But there are also medium light flavours of Ubuntu: Xubuntu and Ubuntu MATE, and an ultra light flavour, Lubuntu. These flavours work well with older computers.

-o-

Fake-pae was a tool for older versions. The boot option forcepae makes things easier to manage in 14.04 LTS and newer versions (with the kernel series 3.13 and newer). But ***you need not use it with a Pentium 4 CPU***, because it has PAE capability and also a PAE flag.

Ubuntu Server and all the desktop flavours of Ubuntu (Kubuntu, Lubuntu ..., Xubuntu) of the same version, for example 14.04.1 LTS, have the same kernels (32-bit alias i386 and 64-bit alias amd64). All the 32 bit kernels are PAE kernels, and the 64-bit kernels manage large amounts of RAM without the PAE work-around. There are no non-pae kernels in Ubuntu and Ubuntu-based operating systems after the version 12.04 LTS (kernel series 3.2).

-o-

It is as easy to use gcc in Lubuntu as in Ubuntu.

-o-

Yes there were non-pae kernels in the Ubuntu versions 10.04 LTS and 11.04. But these versions are long gone, they passed end of life long ago, and you will have big problems with

- no updates, not even security updates, so stay away from the internet!
- no repositories, so it is difficult to install programs, that are not available from the iso files.

---

### Post by artss2 on 2016-03-16
Would you tell me where I can find 32-bit CoreValue Sysinternals to check if my CPU supports pae or not?

---

### Post by sudodus on 2016-03-16
If you know that you have a Pentium 4 CPU, it should be enough (unless you have some very odd motherboard or run a virtual machine via a host system, which is non-pae).

If you run linux (I think all linux distros), you can run the following command line (in a terminal window or text screen)

```
grep pae /proc/cpuinfo
```

In modern linux, you can run the following command line and get a colour mark of the string pae (if it exists)

```
grep --color pae /proc/cpuinfo
```

If there is no pae flag, there will be no output from the command(s).

Edit: See also [https://serverfault.com/questions/85980/what-processors-do-do-not-support-pae](https://serverfault.com/questions/85980/what-processors-do-do-not-support-pae)

---

### Post by artss2 on 2016-03-16
My host system is based on Pentium IV, so it can not have its own specific. I have seen similar topic to this one and there is reference on some iso of 14.04 nonpae tahr about 600-700 mb (probaly user creation). But I am not aware is it reliable one... And about Corevalue tool that reflects cpu features: all I have found was for 64-bit system so not applicable for my one.

---

### Post by artss2 on 2016-03-20
Really, my p.iv cpu 2.8 hz works with xubuntu 14.04 even without forcepae, as well as with ubuntu server 10.04 -- but in vain - no interfaces it could not found. I will try just vbox image of fedora 10, so trying to make it working more is without any use.  I also will try your commands on defini pae kernel of cpu in linux.

---

### Post by sudodus on 2016-03-21
It seems to me that we have sorted out the pae issue: There is no problem with pae. Otherwise it would not be possible for your computer to work with Xubuntu 14.04 without forcepae.

Instead I think you have a problem with the network - I guess you mean network interfaces, when you write interfaces. If this is the case, I suggest that you start a new thread in the [networking sub-forum](http://ubuntuforums.org/forumdisplay.php?f=336). Write a ***good descriptive title*** and describe your problem as detailed as possible in the first post.

If you mean some other interfaces, please explain :-)

---

### Post by Bucky Ball on 2016-03-21
And if you do post a thread in the networking sub-forum it helps a lot if you include the output of the wirelessinfo script in your post. You'll find a link to the script at the bottom of my post. Easy to run and gives loads of info for potential helpers about your internet configuration. ;)

Stick the output between code tags (link to how to do that in my sig also).

---

