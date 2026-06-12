---
title: "Please help us test Lubuntu with Phill's non-pae kernel"
date: 2014-04-11
forum: General Help
---

### Post by sudodus on 2014-04-11
*[phillw]("http://ubuntuforums.org/member.php?u=824544")*  has compiled a ***non-pae kernel for Trusty***, and has built an iso  file with an alternate installer around it. He is asking for help now,  help to test it in a computer with a real non-pae CPU. It would be very valuable for the  Lubuntu project, if you can spend some time testing it.

The iso file can  be downloaded from this link (at Phill's own server)

[http://phillw.net/isos/non-pae/](http://phillw.net/isos/non-pae/)[URL="http://ubuntuforums.org/member.php?u=824544"]
[/URL]
The intention is that this re-spin with the non-pae kernel will follow the updating/upgrading cycle with point releases of Lubuntu 14.04 LTS.

Examples of non-pae CPUs

1. ***Early Pentium M with 1.2 GHz*** clock frequency. (The later Pentium M CPUs have PAE capability even if they lack a PAE flag).

2. ***Old ViA-processors around 1GHz***

3. ***Transmeta Crusoe***

(4. Pre Pentium II CPUs are too old and weak to be tested for this purpose)

You can test for the PAE flag with the following command

```
grep --color pae /proc/cpuinfo
```

---

### Post by phillw on 2014-04-11
I've subscribed to this thread. so I will get replies. You can also catch me on freenode at channel #phillw 

Regards,

Phill.

---

### Post by jerrylamos on 2014-04-11
I'll give it a whirl on my IBM Thinkpad R31.  Downloading now.

The R31 hasn't successfully booted any ubuntu since 12.04.  It claims to have pae, but has never been able to run any ubuntu that was pae only.

Phil's previous "old processor" 9W iso booted to a black screen.

It's a Pentium M circa 2005, 1Ghz, maxed out memory 500 mb, and cpuinfo does show pae,

---

### Post by phillw on 2014-04-11
> **jerrylamos said:**
> I'll give it a whirl on my IBM Thinkpad R31.  Downloading now.

The R31 hasn't successfully booted any ubuntu since 12.04.  It claims to have pae, but has never been able to run any ubuntu that was pae only.

Phil's previous "old processor" iso booted to a black screen.

It's a Pentium M circa 2005, 1Ghz, maxed out memory 500 mb, and cpuinfo does show pae,

Can you please ensure that the self test of the CD has reported back that the self test is okay? I really do need this to be checked so that I know where any error is.

Regards,

Phill.

---

### Post by jerrylamos on 2014-04-11
No go.  Started the CD, gets by a bunch of choices on language and keyboard, then says:

"Your installation CD-ROM couldn't be mounted........Retry mounting the CD-ROM?"

I did.  Still no go.

Makes no sense to me at all.  The CD-ROM has been running, install is proceeding, and suddenly decides the CD-ROM can't be mounted.  No comprendo, install has been using the CD-ROM right along.

Maybe there's not enough space on the CD for the live environment?

---

### Post by sudodus on 2014-04-12
Hi *jerrylamos* and *phillw*,

I had a similar problem (not quite the same output) but also complaining about mounting the CD, when I tested in an IBM Thinkpad T42 with PAE capability but without PAE flag (Pentium M 1.7 GHz)

It fails for me with this output when booting from CD as well as USB
-----
Identify and mount cd-rom

Error running "modprobe -v yenta_socket"
-----
Your install CD could not be mounted ...
-----

Does it work in *any* computer for you *phillw*, or only in a virtual machine? What kind of debugging would you suggest?

---

### Post by sudodus on 2014-04-12
I tried your iso, *phillw*, in a new Toshiba laptop with an Intel i5 CPU (and of course running in CSM (BIOS compatible mode)),

[http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/](http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/)

that I use for development and testing, and I had the same error output as *jerrylamos* (or very similar).

My  Thinkpad and my Toshiba laptop are generally good booters, and can run  most distros, (the Thinkpad might need fake-pae, but then it works), so  it seems the iso file does not work with various real computers, where  it 'should' work. There was no such problem during my tests with your  previous non-pae kernel version. I don't say the problem is because of  the kernel, it might be somewhere else in the iso file (I don't know  where it is).

I think it is a bug, and I hope we can find it soon, so that you can make a good iso file in time for the release of 14.04 LTS.

[COLOR=#696969]Unfortunately for this test I have no computer with a real non-pae CPU.[/COLOR]

---

### Post by sudodus on 2014-04-12
> **phillw said:**
> Can you please ensure that the self test of the CD has reported back that the self test is okay? I really do need this to be checked so that I know where any error is.

Regards,

Phill.

I get the 'cannot mount CD-ROM' error also when trying to self-test the CD.

*Edit*: and notice that I get that error also when booting from USB, so I don't think it is because of bad burning.

---

### Post by phillw on 2014-04-12
I'm also seeing this error on VM. Please pause testing until I've conferred with my tutor as to what is wrong. 

Regards,

Phill.

---

### Post by jerrylamos on 2014-04-12
> **phillw said:**
> I'm also seeing this error on VM. Please pause testing until I've conferred with my tutor as to what is wrong. 

Regards,

Phill.

"Check disk for defects" gets:

Loading module 'yenta   [rest of line overlaid by next message]

Configuring d-i
Error while running 'modprobe -v yenta_socket'

Occurs on both the test Pentium M 1 gHz and also on late model Acer notebook.  My guess, you don't need VM to see this bug.  Try it on a pae pc.

The CD can be read fine until "modprobe" is run which can't read the CD which has just been read.  Some bug in modprobe?

Since the CD is being read fine, why is it doing 'modprobe'?

I don't mind running some tests since tahr hasn't been giving me any trouble lately.  (Oops, just wait for the next update....)

---

### Post by phillw on 2014-04-12
As has not been made clear, I've never respun a kernel let alone an ISO!!! .. I know the kernel is okay as it is running on the build machine (having the kernel actually running makes the build less complicated), as I'm basing things on daily builds I will go and pull in the Beta 2 and do a build with that. It will be a few hours, but should be available in a couple of hours. I can then test it in VM to see if the 'cannot mount CD' error is still there.

Regards,

Phill.

---

### Post by phillw on 2014-04-12
There is a load of updates running in today (including a beta of grub). I'm going to try a build with this daily and check on VM before I ask for further testing.

Regards,

Phill.

---

### Post by phillw on 2014-04-13
The ISO has been re-spun.... Now the issue is that, of course, the installer expects to see a PAE flag and complains that it cannot find it. GRRRRR....... Still, at least it now installs! I hope to have the answer as to tell the installer NOT to  look for PAE flag today / tomorrow.

Regards,

Phill.

---

### Post by sammiev on 2014-04-13
Since the beta version came out I could not get lubuntu14.04 to install at all. I never even got into any menu but install without even choosing install. I see the same screen jerrylamos sees. Doesn't matter if I try non-pae or not. I have all other ubuntu flavors installed with no issues. Makes me think it may not be a non-pae issue. I will follow this thread.

---

### Post by sudodus on 2014-04-13
This is the debian installer or old alternate installer, not Ubuntu's standard desktop installer. I am installing from it right now, near the very end of the process. So the installation works much better with this version.

More details later ...

---

### Post by phillw on 2014-04-13
> **sammiev said:**
> Since the beta version came out I could not get lubuntu14.04 to install at all. I never even got into any menu but install without even choosing install. I see the same screen jerrylamos sees. Doesn't matter if I try non-pae or not. I have all other ubuntu flavors installed with no issues. Makes me think it may not be a non-pae issue. I will follow this thread.


I'm installing the standard alternate installed, another tester has got it installed along with the non-pae version (provided we show the installer a pae flag). I need to have a kernel type person help with the question as to how to alter the kernel/i386.sh file and then build from it. 

the guys have been stars, and I have asked Joe what needs to be altered whilst trying a rebuild..

[FONT=arial]I've done a bit more digging and got as far as:[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial][COLOR=#204a87](17:37:08) [/COLOR][COLOR=#204A87]**phillw: **[/COLOR]hi good people... very quick question.. which script checks for the presence of PAE flag in the alternate (server) installer ISO system. I need to disable it as I have a non-pae kernel :)
[COLOR=#9440b1](17:41:42) [/COLOR][COLOR=#9440B1]cjwatson: [/COLOR]kernel/i386.sh in the base-installer source package
[COLOR=#9440b1](17:42:17) [/COLOR][COLOR=#9440B1]cjwatson: [/COLOR]I suggest you make your change by way of the test suite ("make test")
[COLOR=#9440b1](17:43:04) [/COLOR][COLOR=#9440B1]cjwatson: [/COLOR]You'll probably want to change arch_check_usable_kernel for the case where the computed kernel flavour name is "486"
[COLOR=#204a87](17:45:13) [/COLOR][COLOR=#204A87]**phillw: **[/COLOR]Hi Colin, I have the ISO mounted at non-pae (done the replacement of the kernel and rebuilt the md5 sums etc) I'm using make menuconfig can I change the processor type in there also (I use it to drop the High Memory support from 64Gb to 4 GB)
[COLOR=#9440b1](17:45:22) [/COLOR][COLOR=#9440B1]cjwatson: [/COLOR]No idea
[COLOR=#9440b1](17:46:01) [/COLOR][COLOR=#9440B1]cjwatson: [/COLOR]Not a kernel hacker

So, as I know what the issue is - it is fixable :)

Regards,

Phill.[/FONT]

---

### Post by sudodus on 2014-04-13
The installation into my Thinkpad with Pentium M was successful :-)

(The CPU lacks pae flag but it does have pae capability)

I needed the boot option ***forcepae*** to make the installer happy, and I had to wait through a 10-15 minutes long 'silence', when I thought the installation was dead ... but after that it worked as it should.

Checking the disk for integrity works until isolinux/isolinux.bin which failed the md5sum check. But 1. isolinux/isolinux.bin is maybe outside where checksums are regenerated automatically  2. This file is only used during the boot operation, so if the installation proceeds, it might still produce a good installed system, even if the file is bad.

```
tester@ubuntu:~$ uname -a
Linux ubuntu 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686 i686 i686 GNU/Linux
tester@ubuntu:~$ setxkbmap se
tester@ubuntu:~$ grep --color pae /proc/cpuinfo
tester@ubuntu:~$ grep --color sse /proc/cpuinfo
flags        : fpu vme de pse tsc msr mce cx8 sep mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe bts est tm2
tester@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty
tester@ubuntu:~$ 

```

---

### Post by phillw on 2014-04-13
Kernel has been rebuilt... needs a test ... [http://phillw.net/isos/non-pae/](http://phillw.net/isos/non-pae/)

Regards,

Phill.

---

### Post by Matt 6:27 on 2014-04-15
Just burned for a try.  Is there no "try it live" option?  Looks like only a full Install for testing.  Unfortunately, I'm not in a position to run an install on my old Toshiba Satellite A25 just yet.  Thx.

---

### Post by sudodus on 2014-04-15
No, this is 'only' the alternate installer without live session. Furthermore, we are waiting for the next rebuild, because there was problems, with the version announced in post #18. I can't tell when it will arrive. Right now many of us are busy testing the official 'final' version of 14.04 LTS.

---

### Post by Matt 6:27 on 2014-04-15
Understood... thanks.

---

### Post by phillw on 2014-04-15
We've now tracked down what is stopping a non-pae machine from being allowed to progress. As to which part of which script in which file, we have not found - But at least we have the package and source code to search through! To repeat the earlier comment, when we have time we will work on it. It was initially suggested that I aim for a 14.05 release (i.e. next month). If we can get the installer to behave I may yet get it out pretty soon after 14.04 is fully released. Do bear in mind, I also have to set up reprepro so people can pull in the updated kernels during the 5 year life of the kernel otherwise you will need to pull in the .debs and let Gdebi do its magic.

Regards,

Phill.

---

### Post by jerrylamos on 2014-04-15
The 14 April non-pae image installed successfully on:
IBM Thinkpad R31
1.066 gHz Pentium M
512 MB

Installer didn't see the Ubuntu 10.04 for the grub choices at boot, however once up, update-grub added the 10.04.

I did try the tahr lubuntu alternate install.  After much grinding away, install failed because it didn't install all the software. 
Booted up to command line - df showed a small partition usage.
One of the software items missing was LXDE.

Phil's non-pae disk, not an alternate, much preferred.

---

### Post by raptor890 on 2014-04-18
Hello,


I am receiving this error message while trying to install lubuntu-14.04-non-pae.iso (14-Apr-2014).


"Your installation CD-ROM couldn't be mounted".

Any ideas?

Thank you.

---

### Post by sudodus on 2014-04-18
PhillW is working hard to find and fix the problem and upload a new version for us to test. Please read post #22.

I am not sure if jerrylamos used the current version or an earlier one, that is not available for downloading now. Maybe the current version works in his computer, but not in other computers, for example yours and mine.

---

### Post by jerrylamos on 2014-04-22
> **sudodus said:**
> I am not sure if jerrylamos used the current version I used the 14 April version from Phil's site.  I haven't seen any newer version?

I've downloaded the Lubuntu 14.04 with intentions of installing on another partition on a fairly recent notebook.

---

### Post by sudodus on 2014-04-23
> **jerrylamos said:**
> I used the 14 April version from Phil's site.  I haven't seen any newer version?

I've downloaded the Lubuntu 14.04 with intentions of installing on another partition on a fairly recent notebook.

Thank you for making this clear :-) So this version (dated 14 April) works in your computer but not in mine and not in that of raptor890.

---

### Post by mörgæs on 2014-04-23
Moved to General Help, as 14.04 is no longer the development release.

---

### Post by phillw on 2014-04-23
Hi,

as the dust is settling on the 14.04 I hope to have a rebuild available over the coming weekend.

Regards,

Phill.

---

### Post by sudodus on 2014-04-24
> **phillw said:**
> Hi,

as the dust is settling on the 14.04 I hope to have a rebuild available over the coming weekend.

Regards,

Phill.

Will you use the same kernel, **[FONT=courier new]linux-image-3.13.0-non-pae_122_i386.deb[/FONT]** dated April 8, or will there be a new kernel in the next iso file?

---

### Post by phillw on 2014-04-25
Hi folks,

I got some free time and more help. There is a new kernel and ISO at [http://phillw.net/isos/non-pae/](http://phillw.net/isos/non-pae/) something I've not mentioned on here is my numbering system. Very simply, I add 100 to the kernel build from ubuntu kernel team. Hence Linux build 3.13.0-24-generic becomes [linux-image-3.13.0-nonpae_124_i386.deb]("http://phillw.net/isos/non-pae/linux-image-3.13.0-nonpae_124_i386.deb") Along with other tasks, it has taken a while to get the numbering system to work!

With this build, what I seek to be tested is the use of the forcepae parameter in grub. If this parameter works as I think it will, it will save the step of my having to recompile 'build' and inserting it onto the ISO. [https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE) has how to 'cheat' :P

Do please give the ISO a try (if you already have an older image, use zsync to update it.. [https://help.ubuntu.com/community/ZsyncCdImage](https://help.ubuntu.com/community/ZsyncCdImage) ) Please do note, that you will need to rename your existing ISO and remove the - in non-pae to make it nonpae as the file name :)

Regards,

Phillw.

---

### Post by sudodus on 2014-04-25
I tried your new '124' iso, *phillw*,

[http://phillw.net/isos/non-pae/lubuntu-14.04-nonpae.124.iso](http://phillw.net/isos/non-pae/lubuntu-14.04-nonpae.124.iso)

in a new Toshiba laptop with an Intel i5 CPU (and of course running in CSM (BIOS compatible mode)),

[http://www.toshiba.se/laptops/satell...-pro-c850-19w/]("http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/")

I made it isohybrid, flashed with mkusb to a pendrive and booted.

It passed the self-test without issues :-)

It is busy installing ... installed ... rebooted ... and works :-)

Congratulations Phill :KS

-o-

Now I'll do some testing including trying to install '124' into my old Thinkpad T42 with a Pentium M without a PAE flag.

---

### Post by sudodus on 2014-04-25
In the Toshiba

But ```
uname -a
``` tells me the kernel is the generic '24' rather than then 'non-pae 124'

```
Linux ubuntu 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686 i686 i686 GNU/Linux
```

and ```
cat /proc/cpuinfo
``` tells me there the physical address size is 36 bits.

Did you put the standard generic (pae) kernel into the iso file?

-o-

In the Thinkpad with a Pentium M

[http://www.cnet.com/laptops/lenovo-thinkpad-t42-2373/4507-3121_7-31155666.html](http://www.cnet.com/laptops/lenovo-thinkpad-t42-2373/4507-3121_7-31155666.html)

the [boot option forcepae]("https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M") was necessary

```
... quiet splash -- forcepae
```

The installation is running (with a long pause (searching for a floppy?) and then slowly compared to the Toshiba) ... installed ... rebooted ... and works.

But also this guy shows  that the physical address size is 36 bits. I am almost 100% sure it does so only with a pae kernel. So I think you have to make a new iso file with the non-pae kernel.

---

### Post by phillw on 2014-04-25
there is a rebuild on going.. please be patient....

Regards,

Phill.

---

### Post by sudodus on 2014-04-25
I built Phill's 124 kernel into the system basic text screen system that is installed with

[http://phillw.net/isos/linux-tools/9w/TrustyB1npae-text.iso](http://phillw.net/isos/linux-tools/9w/TrustyB1npae-text.iso)

and I intend to upload a current version of it (with the released 14.04 rather than Trusty Beta) during this weekend. The kernel and the system works for me.

---

### Post by phillw on 2014-04-25
Nearly rebuilt.....

[http://phillw.net/isos/non-pae/](http://phillw.net/isos/non-pae/)

I need a helper :P

Regards,

Phill.

---

### Post by phillw on 2014-04-25
Rebuilt,

Not too sure who got me convinced to do this! (Possibly me saying it cannot be too hard :P )

As long as this iso boots, I only aim to update it as the lts kernel gets updated as everything else will update as and when required. (e.g. 14.04.1, 14.04.2 14.04.3 14.04.4)

Please... let it work!!!!!!!

Regards,

Phill.

---

### Post by sudodus on 2014-04-26
Hi Phill,


1. What is the difference between the kernel dated 25 of April and that dated 24 of April. The kernel files differ, but is it a significant difference, some bug-fix or tweak, or only some version or date string?

I ask because I made mini version based on Ubuntu mini.iso, and I want to know, if the version based on the kernel dated 24 of April is good for uploading.


2. I noticed that when other kernels (the generic pae kernels) were present, these kernels had precedence, and one of them was selected as the default one to boot (at the top in the grub menu).


3. Please explain what is different in this current iso file dated 26 of April compared to the previous one!

What should I look for when testing?

---

### Post by sudodus on 2014-04-26
I can't even check that the disk is good. I get the old error again:

Your installation CD-ROM couldn't be mounted ...

*Edit*: And I get it booting from CD as well as from USB.

Please tell me about the kernel (question #1 in post #38)

---

### Post by sudodus on 2014-04-26
> **sudodus said:**
> I built Phill's 124 kernel into the system basic text screen system that is installed with

[http://phillw.net/isos/linux-tools/9w/TrustyB1npae-text.iso](http://phillw.net/isos/linux-tools/9w/TrustyB1npae-text.iso)

and I intend to upload a current version of it (with the released 14.04 rather than Trusty Beta) during this weekend. The kernel and the system works for me.

> **sudodus said:**
> Hi Phill,

1. What is the difference between the kernel dated 25 of April and that dated 24 of April. The kernel files differ, but is it a significant difference, some bug-fix or tweak, or only some version or date string?

I ask because I made mini version based on Ubuntu mini.iso, and I want to know, if the version based on the kernel dated 24 of April is good for uploading.

2. I noticed that when other kernels (the generic pae kernels) were present, these kernels had precedence, and one of them was selected as the default one to boot (at the top in the grub menu).
...
What should I look for when testing?

Anyway, since I think we have to wait for a good iso from Phill, I upload this one, that has the kernel 124 (from the kernel files dated 24 of April). I installed it into a USB pendrive that runs happily in several of my computers including the Thinkpad with Pentium M (where it has 'only' 32 bits physical address size, typical for non-pae).

I upload it so that ***you*** can also test Phill's non-pae kernel :-)

This 9w (debian) installer can run in text mode and graphics mode. The installed Ubuntu system has only text mode. I suggest that you grow the partition and file system with gparted (while still running the 9w installer). Then after booting into the installed system, if you wish, install a desktop environment, lubuntu-desktop or xubuntu-desktop or the minimal lubuntu-core or maybe only lxde or only openbox or fluxbox.[URL="http://phillw.net/isos/linux-tools/9w/Trusty-npae124-text.iso"]

http://phillw.net/isos/linux-tools/9w/Trusty-npae124-text.iso[/URL]

It may help to get or at least view some other files (for example the help file and md5sum file) from

[http://phillw.net/isos/linux-tools/9w/](http://phillw.net/isos/linux-tools/9w/)

See also this link (posts #88 and #89 and following)

[http://ubuntuforums.org/showthread.php?t=2209683&page=5&p=12957586#post12957586](http://ubuntuforums.org/showthread.php?t=2209683&page=5&p=12957586#post12957586)

---

### Post by sudodus on 2014-04-26
> **sudodus said:**
> ...
This 9w (debian) installer can run in text mode and graphics mode. The installed Ubuntu system has only text mode. I suggest that you grow the partition and file system with gparted (while still running the 9w installer). Then after booting into the installed system, if you wish, install a desktop environment, lubuntu-desktop or [COLOR=#0000ff]xubuntu-desktop[/COLOR] or the minimal lubuntu-core or maybe only lxde or only openbox or [COLOR=#0000ff]fluxbox[/COLOR]

[http://phillw.net/isos/linux-tools/9w/Trusty-npae124-text.iso](http://phillw.net/isos/linux-tools/9w/Trusty-npae124-text.iso)

It may help to get or at least view some other files (for example the help file and md5sum file) from

[http://phillw.net/isos/linux-tools/9w/](http://phillw.net/isos/linux-tools/9w/)
...


Just to test the extremes, I installed xubuntu-desktop and fluxbox, and they work (and can be selected at the login screen). So this is definitely a method to install an Ubuntu 14.04 LTS system with a non-pae kernel.

Of course 'text only' or a window manager (for example openbox or fluxbox) or an ultra-light desktop environment (Lubuntu or Lubuntu Core) will suit best for old computers that need a non-pae kernel. And a non-pae kernel is not a good idea with more than 2 GB RAM. But this system with a non-pae kernel works in a wide range of computers.

---

### Post by phillw on 2014-04-26
When I spun the ISO, it was with the standard kernel. I have to install the made kernel onto the build machine. 

ali@build:~$ uname -a
Linux build 3.13.0-nonpae #1 SMP Fri Apr 25 20:34:33 BST 2014 i686 i686 i686 GNU/Linux


This also idiot checks the kernel (as in "does it boot?"). It was late, so I'm now going to check the ISO out.

Regards,

Phill.

---

### Post by sudodus on 2014-04-26
Anyway, your last-but-one non-pae kernel works as tested via the 9w installer :-)

So what remains for you is to fit it into your iso builder and make a working iso file. Sounds easy, but I know, it is hard until you have climbed the last barrier.

---

### Post by phillw on 2014-04-26
The ISO corrupted during scp.... currently sorting that out

original ISO ..

root@build:~# md5sum *.iso
b5d9d5262a8b9fd4d9d004760439620e  lubuntu-14.04-124non-pae.iso
root@build:~# 

scp'd ISO

[root@ks389199 non-pae]# md5sum *.iso
a24cad84ab28eee4bd1643d546175781  lubuntu-14.04-non-pae.iso
[root@ks389199 non-pae]# 

well, that's not going to work!

Let me have a think!

Regards,

Phill.

---

### Post by sudodus on 2014-04-26
use ***rsync*** if it is between linux systems. I think it is quite reliable. (I use it when uploading files to your server.)

---

### Post by phillw on 2014-04-26
human error... I scp from a /home directory and had not copied the ISO from the build area.... Permissions will be the death of me! New version there. I''ve not even zsynced up my local copy yet... So I have no idea if it works or not! I use zsync for updating things (Hence there being a zsync entry)

Regards,

Phill.

---

### Post by phillw on 2014-04-26
still got the not mounting error.....

---

### Post by phillw on 2014-04-26
And I did a rm-rf of /boot so busy installing a kernel, grub etc..... :: SIGH ::

---

### Post by sudodus on 2014-04-26
[Opening post: Please help us test Lubuntu with Phill's non-pae kernel]("http://ubuntuforums.org/showthread.php?t=2216356&p=12984484#post12984484")

[Current post: I upload a 9w installer so that ***you*** can also test Phill's non-pae kernel now ]("http://ubuntuforums.org/showthread.php?t=2216356&page=2&p=13003216#post13003216")while we are waiting for Phill's installer iso file.

If you have a computer with this or similar hardware: ***Early Pentium M with 1.2 GHz*** clock frequency (the later Pentium M CPUs have PAE capability even if they lack a PAE flag), ***Old ViA-processors around 1GHz ***or ***Transmeta Crusoe***

- Please test Phill's kernel in that computer with the iso file [SIZE=3]**[FONT=courier new]Trusty-npae124-text.iso[/FONT]**[/SIZE] from

[http://phillw.net/isos/linux-tools/9w/](http://phillw.net/isos/linux-tools/9w/)

---

### Post by phillw on 2014-04-28
I *think* I need to get the other two of the holy trinity backl on... [COLOR=#333333][FONT=Ubuntu Beta]That will provide the header, firmware and image .deb files that are needed to install said kernel.[/FONT][/COLOR]If that fails, then I will rebuild the build machine. But, I'm still not too  well, so it is not going to happen today.

Regards,
Phill.

---

### Post by phillw on 2014-04-28
Reinstall happening.

Regards,

Phill.

---

### Post by phillw on 2014-04-28
As happens, the volume destroy and re-create decided not to play ball... just done a force.... It will still be 30th April to expect a test ISO ... Bodhi was correct.... 14.05 for me :)

Keep the faith,

Phillw

---

### Post by phillw on 2014-04-30
There seems to have been some changes to the pain of my life.... graphics on virt-manager....  The VM has built and is updating.. next up will install build essentials etc.

Be patient :)

Regards,

Phill.

---

### Post by phillw on 2014-05-02
It now needs testing...


[http://phillw.net/isos/non-pae/](http://phillw.net/isos/non-pae/)

do remember that you may need all of the three for it to work :)

Regards,

Phill.

---

### Post by sudodus on 2014-05-02
1. The md5sum of the iso file matches, but the check at the boot meny complains that the file ./isolinux/isolinux.bin has a bad md5 checksum. I have seen this behaviour before, and I suspect that you have changed that file without changing the corresponding md5sum. See post [#17]("http://ubuntuforums.org/showthread.php?t=2216356&p=12986457#post12986457") in this thread.

2. The installation seems to work in my fast Toshiba.

3. The installation finished and a bootable system is installed. The kernel is 3.13.0.24-generic. So I suspect it is the standard kernel (not the non-pae kernel). 

4. I will test it in my Thinkpad ...

5. The installation finished and a bootable system is installed. The kernel is 3.13.0.24-generic and ***it is a pae kernel***, giving 36 bits physical address size.

---

### Post by sudodus on 2014-05-02
> **phillw said:**
> It now needs testing...


[http://phillw.net/isos/non-pae/](http://phillw.net/isos/non-pae/)

do remember that you may need all of the three for it to work :)

Regards,

Phill.

Which three? Do you mean all three kernel files? The iso file, once downloaded correctly, should be enough?

---

### Post by phillw on 2014-05-02
> **sudodus said:**
> Which three? Do you mean all three kernel files? The iso file, once downloaded correctly, should be enough?

If you're doing builds based on the non-pae kernel, then you need the three .debs. If you are doing ISO testing, then the ISO has them installed.... Well, hopefully :P

Still got the CD not mounted error... back to digging...... :(

---

### Post by sudodus on 2014-05-02
> **phillw said:**
> If you're doing builds based on the non-pae kernel, then you need the three .debs. If you are doing ISO testing, then the ISO has them installed.... Well, hopefully :P

Still got the CD not mounted error... back to digging...... :(

Strange! I did not get any 'CD not mounted error'. But as far as I understand, there was no non-pae kernel, only the standard pae kernel - for me in your iso file that was uploaded early this morning (May 2). But I see that you have uploaded new versions this afternoon (18.54-18.55).

-o-

Is this your problem? You can create a working iso file with the  standard pae kernel, but when you use the non-pae kernel, you get the 'CD not mounted error'.

---

### Post by phillw on 2014-05-02
This appears to be the issue, I've asked bodhi to look into it... His time is limited, so I'm not going to beat myself up over it. The things I've tried, he says should work... So, it's been passed 'upstream'. Can you check the newly built kernel work okay with your variant...

Regards,

Phill.

---

### Post by sudodus on 2014-05-02
> **phillw said:**
> This appears to be the issue, I've asked bodhi to look into it... His time is limited, so I'm not going to beat myself up over it. The things I've tried, he says should work... So, it's been passed 'upstream'. Can you check the newly built kernel work okay with your variant...

Regards,

Phill.

Yes I can check your kernels, but not immediately, because I'm not at home now.

---

### Post by sudodus on 2014-05-05
I tested the current content of [http://phillw.net/isos/non-pae/](http://phillw.net/isos/non-pae/) uploaded May 4 in the evening

```
-rw-r--r--    879K    2014-05-04    21:36    linux-firmware-image-3.13.0-non-pae_124_i386.deb
-rw-r--r--    6,1M    2014-05-04    21:36    linux-headers-3.13.0-non-pae_124_i386.deb
-rw-r--r--    39M     2014-05-04    21:36    linux-image-3.13.0-non-pae_124_i386.deb
-rw-r--r--    723K    2014-05-04    21:36    linux-libc-dev_124_i386.deb
-rw-r--r--    668M    2014-05-04    21:38    lubuntu-14.04-non-pae.iso
-rw-r--r--    1,4M    2014-05-04    21:38    lubuntu-14.04-non-pae.iso.zsync
-rw-r--r--    60      2014-05-04    21:56    md5sum.txt
```

The iso file works, can install Lubuntu into my Thinkpad with a Pentium M CPU without a PAE flag. But it has the 3.14.0.24-generic kernel with PAE (which works with the boot option forcepae). Then I installed the debian packages (of the same date) and rebooted. The first grub menu option uses ***the non-pae kernel*** and it ***works***. I have not tested a lot, but some crucial things, and it works as it should :-)

---

### Post by phillw on 2014-05-05
Hi,

I've been given some additional help on this ISO building. It seems the ISO and the updated kernels are two different projects :) 

I'll get the ISO rebuilt.

Regards,

Phill.

---

### Post by phillw on 2014-05-06
The help has taken a lot of help, But it is one its' way.... Between trial builds, release builds and release +1 builds... I was not aware that the release numbers would break things if you were an amature and did not fully understand the numbering system that they have to use

---

### Post by sudodus on 2014-05-07
A new tarball is created by from Lubuntu 14.04 with 32-bit non-pae and 32-bit generit (pae) kernels with OEM style installation.

[SIZE=3]**[FONT=courier new]Lubuntu_14.04oem-npae.tar.xz   [/FONT]**[/SIZE][SIZE=3][B][FONT=courier new]# in OEM mode, password: 123456
[/FONT][/B][/SIZE]
Use this link [http://phillw.net/isos/one-button-installer](http://phillw.net/isos/one-button-installer)

This tarball contains *PhillW*'s 32-bit non-pae kernel and  can be  used with  most Intel/AMD CPUs including Pentium M and Celeron  M   processors. The  non-pae kernel does not manage memory above 2 GB well  (but it is seldom a  problem with old hardware). The generic (pae)  kernel is better when there is more than 2 GB RAM.

Find more details about [this tarball at help.ubuntu.com/community/OBI/Lubuntu_14.04_OEM-nonPAE]("https://help.ubuntu.com/community/OBI/Lubuntu_14.04_OEM-nonPAE")

If you have a truly non-pae processor, try the experimental One Button Installer of this link

[dd_blank-obi_7.8GB_23_LubuntuTrusty_non-pae.img.xz]("http://phillw.net/isos/one-button-installer/dd_images/dd_blank-obi_7.8GB_23_LubuntuTrusty_non-pae.img.xz")

If you cannot boot from USB, use the 9w installer described in post #40

[http://ubuntuforums.org/showthread.php?t=2216356&page=2&p=13003216#post13003216](http://ubuntuforums.org/showthread.php?t=2216356&page=2&p=13003216#post13003216)

---

### Post by gcoverleyhotmail. on 2014-05-07
from Ubuntu beginner: My Dell 600 with a Pentium M 1.2GHz will not install U14 because of a pae not installed, (The poor thing has only 512Mb so what's the big deal!). So is this a dead-end for Ubuntu on this machine?
Thanks
gordc

---

### Post by sudodus on 2014-05-08
I think you can run several Ubuntu versions, flavours and re-spins in that computer. With only 512 MB RAM I would suggest Lubuntu or some other flavour or re-spin with an ultra-light desktop environment. Your CPU may or may not have PAE capability (it may have PAE capability even if it has no PAE flag).

- ***Lubuntu 13.10*** or ***Lubuntu 14.04 LTS*** are two alternatives if there is PAE capability. Install Lubuntu 13.10 via Lubuntu-fake-PAE or the One Button Installer. Lubuntu 14.04 LTS can be installed directly with the forcepae boot option or via the One Button Installer as described above.

- Non-PAE versions of ***Bento, Bodhi*** and ***LXLE*** based on Ubuntu 12.04 LTS are likely to work well, even if your computer lacks PAE capability.

See this link for more details [Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640")

or try according to posts #40 (9w installer) and #64 (One Button Installer) in this thread.

*Edit* to make things clear:

- If you want to run a stable system in your Dell 600 with a Pentium M 1.2GHz, there are many alternatives, many of them old, debugged and polished, and still supported.

- If you want to try something new, or help develop this community re-spin (developed by *[[COLOR=#000000]phillw[/COLOR]]("http://ubuntuforums.org/member.php?u=824544")*), then try the non-pae versions in this thread. There are already the alternatives according to posts #40 and #64, and I hope and think that Phill will soon spin a good iso file using the standard alternate installer that will install Lubuntu 14.04 LTS with the non-pae kernel.

---

### Post by phillw on 2014-05-08
An update,

as the alternate cd has taken upon itself to update on installation, tomorrow I will be re-installing it and disconnect networking after it has auto configured up the network, this will force it to use the CD thus I will have both my local VM and the build machine in sync.

Regards,

Phill.

---

### Post by sudodus on 2014-05-14
There is a new wiki page for the ***9w*** installer can install systems with 80 MB RAM to install and run the Ubuntu mini.iso based text system.
[B]
Lubuntu Core Trusty[/B] needs 128 MB RAM to run and at least 256 MB RAM to be really useful. 


See this wiki page [https://help.ubuntu.com/community/9w](https://help.ubuntu.com/community/9w) 


and this page, where you can download the 9w iso files [http://phillw.net/isos/linux-tools/9w/](http://phillw.net/isos/linux-tools/9w/)

---

### Post by sudodus on 2014-05-20
There is a new version of the 9w installer, the [OBI-9w installer]("https://help.ubuntu.com/community/9w#A9w_iso_files")

The One Button Installer in run from the 9w installer's debian system. Now there is a super light-weight installer, that can

- install from CD, DVD and USB
- create not only single boot but also dual boot systems.

Prepare partitions with Gparted and run the One Button Installer at the advanced level to create dual boot or multi boot system.

There are special tarballs for the 9w installer, and these tarballs come with the iso file.

---

### Post by blueled on 2014-06-15
Great work. I wanted to thank Phill and everyone else helping with this project.

I successfully installed xubuntu on a Compaq TC1000 tablet with a Transmeta Crusoe CPU.

---

### Post by sudodus on 2014-06-16
I'm glad a current Xubuntu version works for you, *blueled* :-)

And for our project, thanks for confirming that this kernel works with a Transmeta Crusoe CPU!

Would you be interested in testing also future versions of and with Phill's non-pae kernel?

---

### Post by blueled on 2014-06-17
> **sudodus said:**
> Would you be interested in testing also future versions of and with Phill's non-pae kernel?

Absolutely! I'm still installing packages to complete the installation and try to get pen input working etc. It's an experiment for me to try and get it alive using an up-to-date OS rather than the obsolete XP that came from factory.

---

### Post by sudodus on 2014-07-05
There is a new iso file of the OBI-9w installer which is up to date with a new version of PhillW's non-pae kernel and updated/dist-upgraded packages:

[B]obi_Trusty-nonpae-txt5-9w.iso

[/B]that you find at [http://phillw.net/isos/linux-tools/9w](http://phillw.net/isos/linux-tools/9w)[URL="http://phillw.net/isos/linux-tools/9w"]
[/URL]
*Edit*: See the instructions at this wiki page [http://help.ubuntu.com/community/9w](http://help.ubuntu.com/community/9w)

---

### Post by sudodus on 2014-07-09
Once started to make a new installed system for the OBI-9w installer, I continued making tarballs. There are two new tarballs for the regular One Button Installer which are up to date with a new version of Phill's non-pae kernel and updated/dist-upgraded packages:

```
Lubuntu_14.04oem-npae5.tar.xz          # in OEM mode, password: 123456
Trusty-nonpae-txt5.tar.xz              # user: guru, password: changeme
```

You find them at

[http://phillw.net/isos/one-button-installer/](http://phillw.net/isos/one-button-installer/)

See the instructions at this wiki page

[https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)

-o-

Using the ***Lubuntu tarball makes it more convenient*** than to download a standard iso file

Lubuntu 14.04 LTS:
lubuntu-14.04-desktop-i386.iso
lubuntu-14.04-alternate-i386.iso

install and run two months worth of updates/upgrades.

You will also find the installation from

```
Trusty-nonpae-txt5.tar.xz
```

(or the corresponding OBI-9w installer) a convenient alternative compared to starting with

Ubuntu 14.04 LTS:  mini.iso

---

### Post by Melodie on 2014-07-10
Hi,

I have been testing several versions of Phillw's non pae kernels, until the last one which is now working! \o/

Bento Trusty RC1 - Ubuntu Openbox Remix - now works as a live desktop with the latest non pae kernel patched with AUFS provided by phillw. [http://phillw.net/isos/bento-ubuntu-remix/](http://phillw.net/isos/bento-ubuntu-remix/)
(See the readme.txt for some information about Bento).

It boots to the desktop, it can be installed, just in Virtualbox the pae feature must be unticked in the system configuration tab, and the resolution may be improved by adding the following packages: virtualbox-guest-utils and virtualbox-guest-x11, (if in the Live, logout, and login with the username "ubuntu", then click in the password field, don't type anything, hit "enter").

Once installed in Virtualbox you may have to install the same packages again and logout/login. (Bento Trusty is really a draft of what it will become in the future, it still lacks polish, finish, but it's a working system which can be used for testing purposes).

---

### Post by sudodus on 2014-07-13
The standard One Button Installer is updated to version 2.5 based on Lubuntu 14.04 LTS with updates/upgrades to the current date. There is one version with the standard generic-pae kernel and one version with a Phill's non-pae kernel.

The recent improvements are described in [URL="http://ubuntuforums.org/showthread.php?t=2172971&page=2&p=13066252#post13066252"]the posts #22, 23, 24 in this Ubuntu Forum thread
[/URL] 
and in this wiki page [https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)

---

### Post by RobertoRecordo on 2014-11-30
my thanks to Phillw (for tackling this project) and sudodus (for previous posts in the forums about pae issues)

I have a HP Compaq nc4000 with a Intel Pentium M 1.6 GHz 400 MHz 1M Laptop CPU SL6F8 (Banias)
I own, but have not installed or tested a Intel Pentium M 1.6 GHz 400 MHz 1M Laptop CPU SL6FA

It has 768 MB Ram and a WiFi upgrade. This laptop is mint, so I am trying to make it dual boot XP, and discovered my pae problem when I tried to install Ubuntu. 

Is this processor of interest in this study? I am expecting that forcepae will work with Lubuntu, but I could test live CD's or test kernels. I am on the learning curve, but doing these things is in my area of interest, and I think this project is worthwhile.
edit: Lubuntu 12.10 does have pae issue on nc4000, have not tried to frocepae

---

### Post by sudodus on 2014-11-30
Hi Roberto,

I think we know pretty well now, that Phill's non-pae kernel for 14.04 works as it should. And I agree with you that forcepae should work with your Pentium M and Lubuntu 14.04 LTS. A friend of mine has an IBM Thinkpad T41 with such a CPU (and I have a similar computer with a slightly newer CPU (1.7 MHz)). Be sure to install the newest point release (now 14.04.1 LTS).

But I welcome your wish to test it. I would suggest that you try according to this link

[https://help.ubuntu.com/community/9w](https://help.ubuntu.com/community/9w)

installing Trusty from this iso file

[http://phillw.net/isos/linux-tools/9w/obi_Trusty-nonpae-txt5-9w.iso](http://phillw.net/isos/linux-tools/9w/obi_Trusty-nonpae-txt5-9w.iso)

Please post your results here, and particularly, if you notice any differences in performance between the non-pae kernel and the pae kernel running with forcepae.

---

### Post by RobertoRecordo on 2014-11-30
:oops: I did not realize how old this thread is! I will try it, thanks for the reply

---

### Post by Agent24 on 2014-11-30
I just found this thread and it sounds like the perfect thing to get Lubuntu 14.04 on my EeePC 701 - which is still runnning 11.04!

But I am confused over what I should use. As per the last entry on "https://help.ubuntu.com/community/Lubuntu-fake-PAE", I just downloaded [http://phillw.net/isos/linux-tools/9w/Trusty-npae124-text.iso](http://phillw.net/isos/linux-tools/9w/Trusty-npae124-text.iso) - but I see you are suggesting something else.

Which option should I go for, to best get a 'normal' 14.04LTS Lubuntu installed with this recompiled non-PAE kernel? I do want to be able to have all the standard Lubuntu software, LXDE etc.

---

### Post by sudodus on 2014-12-01
> **Agent24 said:**
> I just found this thread and it sounds like the perfect thing to get Lubuntu 14.04 on my EeePC 701 - which is still runnning 11.04!

But I am confused over what I should use. As per the last entry on "https://help.ubuntu.com/community/Lubuntu-fake-PAE", I just downloaded [http://phillw.net/isos/linux-tools/9w/Trusty-npae124-text.iso](http://phillw.net/isos/linux-tools/9w/Trusty-npae124-text.iso) - but I see you are suggesting something else.

Which option should I go for, to best get a 'normal' 14.04LTS Lubuntu installed with this recompiled non-PAE kernel? I do want to be able to have all the standard Lubuntu software, LXDE etc.

I'm sure that all the EeePCs have CPUs with PAE capability, so you need not run a non-pae kernel. But the 701 has a very small internal drive (4 GB?), if I remember correctly, so you'd want a very small system (occupying very little space on the internal drive). But of course, you can try this non-pae kernel and install one of the small systems according to this link

[https://help.ubuntu.com/community/9w](https://help.ubuntu.com/community/9w)

This link shows details of [RAM_&_disk_usage]("https://help.ubuntu.com/community/9w/RAM_%26_disk_usage") for the desktop environments and window managers offered for installation. 

In this case I suggest that you install Trusty from this iso file

[http://phillw.net/isos/linux-tools/9...ae-txt5-9w.iso]("http://phillw.net/isos/linux-tools/9w/obi_Trusty-nonpae-txt5-9w.iso")

-o-

You can also try a new very light distro, ***ToriOs***, which is under development (still not released, but there is a working version at) [http://torios.org/](http://torios.org/) This version is built from Ubuntu 12.04 LTS in order to have compatible drivers for old hardware.

And there are other alternatives, some other ultra-light linux distro, that runs from a USB drive and is known to work well with old hardware, for example ***Wary Puppy*** or ***Tiny Core***, or if you want to run a system built from Ubuntu 14.04: ***Tahrpup*** [http://puppylinux.org/wikka/tahrpup](http://puppylinux.org/wikka/tahrpup)

---

### Post by Agent24 on 2014-12-01
Well, now I just feel silly. I could have sworn I tried the forcepae option on a live CD and had it fail. But I tried just now and it worked fine... so I guess I'll just use plain Lubuntu with that option!

Thanks for the suggestions of those other distros though, they look like they could be quite useful, for other, older machines.

---

### Post by sudodus on 2014-12-01
What is the size of your internal drive in your EeePC 701? If more than 4 GB, I think installing Lubuntu from a standard desktop 32-bit iso file will work for you. Otherwise, with only 4 GB, you should install something else, or install Lubuntu via some other method, that need less drive space during the installation.

Anyway, good luck :-)

---

### Post by Agent24 on 2014-12-02
Yeah, it has the 4GB drive but I use this trick: [http://askubuntu.com/questions/395932/can-i-install-ubuntu-in-a-3-5-gb-mini-pc](http://askubuntu.com/questions/395932/can-i-install-ubuntu-in-a-3-5-gb-mini-pc)

(Boot the Lubuntu live.

Open a terminal. Type gksu leafpad /usr/lib/ubiquity/ubiquity/misc.py. Click on Options and select line number. At about line #853 will be something like "min_disk size = size x 2 #fudge factor", change 2 to 1.4 and then save.

Run the Install Lubuntu. It should now say minimum disk size 3GB)

---

### Post by sudodus on 2014-12-02
So you have installed Lubuntu already :KS

Then it will be important to keep the system clean from unnecessary files, because of the small drive. You can save personal files (documents, pictures etc) in an external drive, and you can remove un-necessary files 'cruft' either manually with terminal window commands or with [Ubuntu Tweak's janitor]("http://www.noobslab.com/2013/10/ubuntu-tweak-reached-to-086-version.html")

---

### Post by Mike_Walsh on 2014-12-02
> **Agent24 said:**
> Well, now I just feel silly. I could have sworn I tried the forcepae option on a live CD and had it fail. But I tried just now and it worked fine... so I guess I'll just use plain Lubuntu with that option!

Thanks for the suggestions of those other distros though, they look like they could be quite useful, for other, older machines.

Hi, Agent24.

Seriously, I would give Puppy Linux 'Tahrpup' a try.

I have a truly ancient Dell Inspiron laptop; an original 1100, from 2002. It has a 'NetBurst'-generation desktop Intel Celeron CPU; although it runs at 2.2 GHz, it has a miniscule 128k L2 cache, and serious problems with the Intel, 'Brookdale'-core, 'Extreme Graphics' 82845 G/GL/GE/PE/PV video chipset.....to the extent that no current 'buntu-based distro will run on it with anything other than a 640x480 display, jammed up into the top-left corner of the screen.

It originally came with 128MB of RAM, and a 20 GB Hitachi 'Travelstar' HDD. It now sports 1 GB RAM, and the HDD has been updated to 40 GB. The CPU does have the PAE flag; but 'TahrPup', running from a 16 GB SanDisk Cruzer 'Fit' nano USB flash drive, is the first Linux distro I have found that allows it to run completely normally...with its full, 1024x768 display.

It's even file-sharing with my 'big' machine via built-in Samba client software, and network printing; stuff I hadn't even considered when it was running Win XP...

I'm so impressed with 'TahrPup' that I've installed it to a partition on the HDD of my main workhorse.....a 2005 Compaq Presario desktop, running an AMD Athlon 64 CPU, along with 3 GB RAM, and a 160 GB WD Caviar 'Black'; on which it simply FLIES!

Highly recommended.

Regards,

Mike. :)

---

