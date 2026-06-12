---
title: "Ubuntu 16.04 crashes with 4.4.0-108 kernel"
date: 2018-01-09
forum: General Help
---

### Post by cbraxton on 2018-01-09
I just ran an update on my Ubuntu Mate 16.04 system, which updated the kernel to 4.4.0-108. (I don't know if this version has changes to mitigate the recently-discovered Intel security flaws.) What happened afterwards is at boot time is the system locked up hard just as the graphical bootup screen attempts to initialize. The CPU is a Core i5-3570K using built-in graphics.

For now I've had to go back to the 4.4.0-104 kernel. Has anyone else here experienced a similar problem with this update?

---

### Post by shinephp on 2018-01-09
The same issue this morning:
Ubuntu 16.04 after the kernel update from 4.4.0-104 to 4.4.0-108 crashes on boot showing text dump. 
Previous kernel version 4.4.0-104 works correctly.
Processor core i5-3570K, GPU GeForce GTX 760/PCIe/SSE2

---

### Post by cbraxton on 2018-01-09
So it seems likely more CPU related than a problem with video. Another small data point, I have an old laptop with AMD "Turion II X2" CPU running Xubuntu 14.04. I just installed the Xenial hardware enablement stack which includes the 4.4.0-108 kernel and it's working with no apparent issues.

---

### Post by mc4man on 2018-01-09
Yeah, that kernel appears to be no good. On one 16.04 install I have the 4.4.0 kernel available, upgraded & it just crashes with a stacktrace.
So use the prior one (-105 here) or the hwe kernel is fine (here at 4.13.0-25-generic #29~16.04.2-Ubuntu

---

### Post by owise1 on 2018-01-10
Yep - same here - did update and lockup at boot screen
Intel Nuc Celeron(R) CPU 847 using onboard graphics.

There is bug report - looks like a Meltdown update which is apt given thats what happens


Dave

---

### Post by djchandler on 2018-01-10
I installed to this machine from 16.04.03 disk, so no major updates yet. I stay on the LTS versions. On 4.10.0-42 now. I don't know what the kernel was on the installation disk. A new kernel was downloaded during installation.

You can download a new install disk, Update sources and use it as a source to update your kernel past 4.4.0-108. Go to the Other Software tab of the Software & Updates utility in System Settings after you have mounted the new 16.04.03 (or greater) .iso. You should  get prompted to update from the DVD when it mounts also.

I hope this is a better solution for you. Keep your kernel as up-to-date as you are comfortable with. Fixes for the recently announced CPU bugs will go into the latest project first, then backported.

---

### Post by mossroy2 on 2018-01-10
Same crash here, with Intel(R) Core(TM) i5-3450S CPU and kernel 4.4.0-108
Booting with 4.4.0-104 works

Looks like there is an open bug on launchpad : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1742323](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1742323)

flags of my CPU : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm epb tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms xsaveopt dtherm ida arat pln pts

---

### Post by vic-0611 on 2018-01-10
Can anybody confirm if this kernel implements the fix for Meltdown vulnerability?

---

### Post by mossroy2 on 2018-01-10
> **vic-0611 said:**
> Can anybody confirm if this kernel implements the fix for Meltdown vulnerability?
I can't confirm, but it seems to be the intention of this 4.4.0-108 kernel update : [https://usn.ubuntu.com/usn/usn-3522-1/](https://usn.ubuntu.com/usn/usn-3522-1/)

---

### Post by ajgreeny on 2018-01-10
A newer kernel has just been released, 4.4.0-109, which I have just upgraded to, and will report back in a few minutes if that is working as it should.

I presume this was to overcome the problem of the 4.4.0-108 which also affected me.
Hopefully this will be an end to the saga.

[COLOR="#FF0000"]**EDIT:**[/COLOR]
I can confirm that the new 4.4.0-109 kernel is working fine, so if anyone is still trying to get their machine running straight from boot up, simply do your normal update to get the new version, then purge 4.4.0-108, as it seems to be useless for many users, perhaps just Intel CPUs, but I have nothing else to use and see if the 108 version works for some hardware.

---

### Post by dipper2 on 2018-01-10
> **ajgreeny said:**
> A newer kernel has just been released, 4.4.0-109, which I have just upgraded to, and will report back in a few minutes if that is working as it should.

I presume this was to overcome the problem of the 4.4.0-108 which also affected me.
Hopefully this will be an end to the saga.

[COLOR=#FF0000]**EDIT:**[/COLOR]
I can confirm that the new 4.4.0-109 kernel is working fine, so if anyone is still trying to get their machine running straight from boot up, simply do your normal update to get the new version, then purge 4.4.0-108, as it seems to be useless for many users, perhaps just Intel CPUs, but I have nothing else to use and see if the 108 version works for some hardware.

Brilliant. Thank you. This worked for me.

This is why I dumped Windows. It's always possible to solve Ubuntu problems quickly.

---

### Post by flix3 on 2018-01-10
Just to confirm that 4.4.0-109 worked for me too.

The problem was that the update manager did not install all the required 4.4.0-109 files for me (maybe because I completely uninstalled and removed the four 4.4.0-108 kernel files via Synaptic).
However I've manually installed the four 4.4.0-109 kernel files (via Synaptic), rebooted, and now it works ("uname -r" tells me the kernel I'm using is correct).

Thanks everybody!

My system:
ubuntu 16.04 LTS 
Intel® Core™ i5-4590 CPU @ 3.30GHz × 4
GeForce GT 630/PCIe/SSE2
64-bit

---

### Post by rt2768 on 2018-01-10
4.4.0-109 working..[https://usn.ubuntu.com/usn/usn-3522-3/](https://usn.ubuntu.com/usn/usn-3522-3/)

---

### Post by DuckHook on 2018-01-10
Unfortunately, my wife upgraded to 4.4.0-108 before I saw this. Her computer is now blacked out from on switch. Totally blind. Can't even see BIOS. Will try a few things and report back.

---

### Post by cbraxton on 2018-01-10
I installed the 4.4.0-109 kernel, headers, and tools via Synaptic but unfortunately did not experience good results. I'm using luks full-disk encryption. The boot process gets a little further than it did with 108 - the graphical password screen comes up, but in low-resolution mode, and keyboard input does not work. The system appears to be effectively hung/locked up at that point. So for me it's back to 4.4.0-104 for now.

---

### Post by N0rbert on 2018-01-10
**[[COLOR=#000000]cbraxton[/COLOR]]("https://ubuntuforums.org/member.php?u=583700")**, do not forget to report bug about your problem.

On my 4 simple 16.04 LTS systems even with Nvidia proprietary drivers upgrade to **4.4.0-109-generic** solves problems. 
AskUbuntu users seem to be happy with [this solution too]("https://askubuntu.com/a/994277/66509").

---

### Post by DuckHook on 2018-01-10
Blank screen solved.

For posterity:

The bad kernel will force some systems to output only to VGA. My wife's system was using DisplayPort. Hence, no signal.

Solution:

[LIST=1]
[*]Plug in VGA cable/monitor.
[*]Boot to older kernel.
[*]*Carefully* purge 4.4.0-108:```
sudo apt purge linux-image-4.4.0-108-generic linux-headers-4.4.0-108-generic
```
[*]Test to see if later kernel exists:```
sudo apt update && sudo apt -s full-upgrade
```
[*]If kernel is later than 4.4.0-108, install it:```
sudo apt full-upgrade
```
[*]Clean up (optional):```
sudo apt autoremove && sudo apt clean
```
[/LIST]
If your monitor has no VGA port, you will have to use a VGA to DP cable/converter.

---

### Post by Jedrek30 on 2018-01-11
The solution to this problem is fully described here. 
[https://askubuntu.com/questions/994067/kernel-panic-after-update-to-4-4-0-108-generic](https://askubuntu.com/questions/994067/kernel-panic-after-update-to-4-4-0-108-generic)

---

### Post by Impavidus on 2018-01-11
> **flix3 said:**
> 
The problem was that the update manager did not install all the required 4.4.0-109 files for me (maybe because I completely uninstalled and removed the four 4.4.0-108 kernel files via Synaptic).
However I've manually installed the four 4.4.0-109 kernel files (via Synaptic), rebooted, and now it works ("uname -r" tells me the kernel I'm using is correct).


Exactly. When you uninstalled and purged 4.4.0-108, the meta-packages linux-image-generic, linux-headers-generic and linux-generic, updates to which pulled in 4.4.0-108 in the first place, got uninstalled too. The new version of linux-generic available now will pull in the new kernel (4.4.0-109) **and future updates**.

If you used linux-lowlatency, linux-signed-generic, linux-signed-lowlatency or linux-virtual instead, reinstall that.

---

### Post by djchandler on 2018-01-11
> **djchandler said:**
> I installed to this machine from 16.04.03 disk, so no major updates yet. I stay on the LTS versions. On 4.10.0-42 now. I don't know what the kernel was on the installation disk. A new kernel was downloaded during installation.

You can download a new install disk, Update sources and use it as a source to update your kernel past 4.4.0-108. Go to the Other Software tab of the Software & Updates utility in System Settings after you have mounted the new 16.04.03 (or greater) .iso. You should  get prompted to update from the DVD when it mounts also.

I hope this is a better solution for you. Keep your kernel as up-to-date as you are comfortable with. Fixes for the recently announced CPU bugs will go into the latest project first, then backported.

Speaking of backports, I guess we're not going to bother. Just got upgraded to kernel 4.13.0-26. AFAIK, this is the latest kernel available. I suggest everyone hold on until this gets to you. This kernel is in the Xenial repository. This is not an unsupported backport. I suggest getting on 4.13 ASAP.

BTW, I use Synaptic for package management. Obsolete kernels can be removed there. Just be careful. Removing a bunch at once is time consuming. GRUB gets updated for every kernel removed, every time.

---

### Post by DuckHook on 2018-01-12
> **djchandler said:**
> …Just got upgraded to kernel 4.13.0-26. AFAIK, this is the latest kernel available. I suggest everyone hold on until this gets to you…

> **del6 said:**
> I was running 4.10 got pushed to 4.13 I'm pretty sure both 4.13.0-25 and -26 both black screened me as did 4.0.0-109 (not to worried about that) so I'm currently running 4.10.0-42-generic, anyone else in the same position?

Please note that this thread is specifically about the 4.4.0-108 problem. The 4.4.0-x kernel series is still a legitimate kernel series and many users have not elected to go to the HWE kernels for Xenial. So this is just a friendly reminder not to hijack this thread. Those who are using the HWE kernels should start their own thread or join the general [Meltdown and Spectre Discussion thread]("https://ubuntuforums.org/showthread.php?t=2381801").

---

### Post by daveginboav on 2018-01-13
> **DuckHook said:**
> Please note that this thread is specifically about the 4.4.0-108 problem. The 4.4.0-x kernel series is still a legitimate kernel series and many users have not elected to go to the HWE kernels for Xenial. So this is just a friendly reminder not to hijack this thread. Those who are using the HWE kernels should start their own thread or join the general [Meltdown and Spectre Discussion thread]("https://ubuntuforums.org/showthread.php?t=2381801").

Good point, but there will be users who are confused over such subtle differences between the various kernels and quite often search engines and social media will direct them to this thread.

---

### Post by vic-0611 on 2018-01-16
Thank you flix3. I was wandering why the system wasn't updating to the 109 version when doing:

```

sudo apt-get update
sudo apt-get upgrade

```

Now I see I must do it directly:
```

sudo apt-get install linux-headers-4.4.0-109 linux-headers-4.4.0-109-generic linux-headers-generic linux-image-4.4.0-109-generic linux-image-extra-4.4.0-109-generic linux-image-generic linux-tools-4.4.0-109 linux-tools-4.4.0-109-generic linux-tools-generic

```

I will do it when I arrive home.

---

### Post by DuckHook on 2018-01-16
> **vic-0611 said:**
> Thank you flix3. I was wandering why the system wasn't updating to the 109 version when doing:

```

sudo apt-get update
sudo apt-get upgrade

```…
Actually, the *apt-get upgrade* command will not upgrade kernels. You need to do:```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by deadflowr on 2018-01-16
> Maybe I'm wrong, but as far as I remember, update+upgrade have been enough to get kernel updates.
Depends on which apt command.
If apt-get, then no, that will only install updates for packages that already exist on your system.
apt-get upgrade will never install a new kernel.

If apt, then yes apt upgrade will install new kernels.

You can read the more technical description in the manpages
```
man apt
man apt-get
```

---

### Post by DuckHook on 2018-01-16
> **vic-0611 said:**
> …I tried first update + dist-upgrade but it didn't work:

So I went for the initial plan:

```
sudo apt-get install linux-headers-4.4.0-109 linux-headers-4.4.0-109-generic linux-headers-generic linux-image-4.4.0-109-generic linux-image-extra-4.4.0-109-generic linux-image-generic linux-tools-4.4.0-109 linux-tools-4.4.0-109-generic linux-tools-generic
```
Hmmm…

There's nothing wrong with installing a specific kernel directly, but you must keep in mind that apt will now mark that package manually installed and not automatic. That means that you will need to manually purge it when it is superseded by new kernels.

I am more perplexed by the fact that *dist-upgrade* didn't work. Did you, perchance, remove the *linux-generic* package from your system? Please post results of:```
apt policy linux-generic
```…and:```
dpkg --get-selections | grep linux
```

---

### Post by vic-0611 on 2018-01-16
Hello DuckHook,

Here are the results:

```
sudo apt policy linux-generic
linux-generic:
  Instalados: (ninguno)
  Candidato:  4.4.0.109.114
  Tabla de versión:
     4.4.0.109.114 500
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
        500 http://es.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
     4.4.0.21.22 500
        500 http://es.archive.ubuntu.com/ubuntu xenial/main amd64 Packages

```
```
 dpkg --get-selections | grep linux
console-setup-linux                install
libselinux1:amd64                install
linux-base                    install
linux-firmware                    install
linux-headers-4.4.0-104                install
linux-headers-4.4.0-104-generic            install
linux-headers-4.4.0-109                install
linux-headers-4.4.0-109-generic            install
linux-headers-generic                install
linux-image-4.4.0-101-generic            deinstall
linux-image-4.4.0-103-generic            deinstall
linux-image-4.4.0-104-generic            install
linux-image-4.4.0-109-generic            install
linux-image-4.4.0-21-generic            deinstall
linux-image-4.4.0-22-generic            deinstall
linux-image-4.4.0-24-generic            deinstall
linux-image-4.4.0-28-generic            deinstall
linux-image-4.4.0-31-generic            deinstall
linux-image-4.4.0-34-generic            deinstall
linux-image-4.4.0-36-generic            deinstall
linux-image-4.4.0-38-generic            deinstall
linux-image-4.4.0-43-generic            deinstall
linux-image-4.4.0-45-generic            deinstall
linux-image-4.4.0-47-generic            deinstall
linux-image-4.4.0-51-generic            deinstall
linux-image-4.4.0-53-generic            deinstall
linux-image-4.4.0-57-generic            deinstall
linux-image-4.4.0-59-generic            deinstall
linux-image-4.4.0-62-generic            deinstall
linux-image-4.4.0-63-generic            deinstall
linux-image-4.4.0-64-generic            deinstall
linux-image-4.4.0-66-generic            deinstall
linux-image-4.4.0-70-generic            deinstall
linux-image-4.4.0-71-generic            deinstall
linux-image-4.4.0-72-generic            deinstall
linux-image-4.4.0-75-generic            deinstall
linux-image-4.4.0-77-generic            deinstall
linux-image-4.4.0-78-generic            deinstall
linux-image-4.4.0-79-generic            deinstall
linux-image-4.4.0-81-generic            deinstall
linux-image-4.4.0-83-generic            deinstall
linux-image-4.4.0-87-generic            deinstall
linux-image-4.4.0-89-generic            deinstall
linux-image-4.4.0-92-generic            deinstall
linux-image-4.4.0-93-generic            deinstall
linux-image-4.4.0-96-generic            deinstall
linux-image-4.4.0-97-generic            deinstall
linux-image-4.4.0-98-generic            deinstall
linux-image-extra-4.4.0-101-generic        deinstall
linux-image-extra-4.4.0-103-generic        deinstall
linux-image-extra-4.4.0-104-generic        install
linux-image-extra-4.4.0-109-generic        install
linux-image-extra-4.4.0-21-generic        deinstall
linux-image-extra-4.4.0-22-generic        deinstall
linux-image-extra-4.4.0-24-generic        deinstall
linux-image-extra-4.4.0-28-generic        deinstall
linux-image-extra-4.4.0-31-generic        deinstall
linux-image-extra-4.4.0-34-generic        deinstall
linux-image-extra-4.4.0-36-generic        deinstall
linux-image-extra-4.4.0-38-generic        deinstall
linux-image-extra-4.4.0-43-generic        deinstall
linux-image-extra-4.4.0-45-generic        deinstall
linux-image-extra-4.4.0-47-generic        deinstall
linux-image-extra-4.4.0-51-generic        deinstall
linux-image-extra-4.4.0-53-generic        deinstall
linux-image-extra-4.4.0-57-generic        deinstall
linux-image-extra-4.4.0-59-generic        deinstall
linux-image-extra-4.4.0-62-generic        deinstall
linux-image-extra-4.4.0-63-generic        deinstall
linux-image-extra-4.4.0-64-generic        deinstall
linux-image-extra-4.4.0-66-generic        deinstall
linux-image-extra-4.4.0-70-generic        deinstall
linux-image-extra-4.4.0-71-generic        deinstall
linux-image-extra-4.4.0-72-generic        deinstall
linux-image-extra-4.4.0-75-generic        deinstall
linux-image-extra-4.4.0-77-generic        deinstall
linux-image-extra-4.4.0-78-generic        deinstall
linux-image-extra-4.4.0-79-generic        deinstall
linux-image-extra-4.4.0-81-generic        deinstall
linux-image-extra-4.4.0-83-generic        deinstall
linux-image-extra-4.4.0-87-generic        deinstall
linux-image-extra-4.4.0-89-generic        deinstall
linux-image-extra-4.4.0-92-generic        deinstall
linux-image-extra-4.4.0-93-generic        deinstall
linux-image-extra-4.4.0-96-generic        deinstall
linux-image-extra-4.4.0-97-generic        deinstall
linux-image-extra-4.4.0-98-generic        deinstall
linux-image-generic                install
linux-libc-dev:amd64                install
linux-sound-base                install
linux-tools-4.4.0-109                install
linux-tools-4.4.0-109-generic            install
linux-tools-common                install
linux-tools-generic                install
pptp-linux                    install
syslinux                    install
syslinux-common                    install
syslinux-legacy                    install
util-linux                    install

```

Just in case a translation is needed:

ninguno => none

"Version table", "installed" and "candidate" are quite obvious...

Thank you for your time!

---

### Post by DuckHook on 2018-01-16
As I suspected, the reason you are not getting results from *apt-get dist-upgrade* is because you are missing the *linux-generic* package. You may have deleted it accidentally while trying to fix 4.4.0-108. But that's not really important now. To fix this:```
sudo apt install linux-generic
```Thereafter, you will be able to keep upgraded to the most current kernel whenever you do:```
sudo apt-get dist-upgrade
```When the next few kernels arrive, and all is well, and you don't want an old kernel like 4.4.0-109 hanging around, remember to purge it manually. Otherwise, it will perpetually exist in your system because you installed it manually this time. Don't do this until at least three new kernels have been installed. You always want a set of old kernels to fall back on.

---

### Post by vic-0611 on 2018-01-17
Thank you for the information. Now linux-generic package is not missing:

```
sudo apt policy linux-generic
linux-generic:
  Instalados: 4.4.0.109.114
  Candidato:  4.4.0.109.114
  Tabla de versión:
 *** 4.4.0.109.114 500
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
        500 http://es.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     4.4.0.21.22 500
        500 http://es.archive.ubuntu.com/ubuntu xenial/main amd64 Packages

```

For purging 109 version when the time arrives, I guess will be enough with:

```
sudo sudo apt-get purge linux-image-4.4.0-109 linux-headers-4.4.0-109 linux-headers--4.4.0-109
```

---

### Post by deadflowr on 2018-01-17
> For purging 109 version when the time arrives, I guess will be enough with:
<snip>


Just run
```
sudo apt autoremove --purge
```
this can/will clear out the old kernels, leaving the last/latest two (it leaves two so you have at least one to fall back on in case the most recent one has issues.)
Only issue with autoremove is that it can remove packages you might want to keep if those packages were originally installed to satisfy the requirements of another package which has since been removed, a little quirk.

If you want a simply way to remove old kernels without any potential fuss you can use the purge-old-kernels command which is built into the package byobu
```
sudo apt install byobu
```
then run
```
sudo purge-old-kernels
```
the default is to remove all but two, since that is the standard.
But you can add a parameter to keep more (or less)
```
sudo purge-old-kernels --keep #
```
replace # with the number you want to keep.

More at the man page: [http://manpages.ubuntu.com/manpages/xenial/man1/purge-old-kernels.1.html]("http://manpages.ubuntu.com/manpages/xenial/man1/purge-old-kernels.1.html")
(But really, not a lot more.)

---

### Post by vic-0611 on 2018-01-21
Than you deadflowr for the information.

You wrote:
> Only issue with autoremove is that it can remove packages you might want  to keep if those packages were originally installed to satisfy the  requirements of another package which has since been removed, a little  quirk.

Well, if the packages were installed to satisfy packages which were removed, I suppose they are expendable, too. Therefore, "autoremove --purge" seems an optimal solution.

---

### Post by deadflowr on 2018-01-21
> **vic-0611 said:**
> Than you deadflowr for the information.

You wrote:


Well, if the packages were installed to satisfy packages which were removed, I suppose they are expendable, too. Therefore, "autoremove --purge" seems an optimal solution.

Indeed like 99.9% of the time you wouldn't notice or care about the leftover cruft.
But just in case, always double check because you never know.
There is always a chance you could install something that needed another nifty package which you like to use.
Then again, reinstalling the package is not too much trouble but more of a low-level ugh.

---

### Post by djchandler on 2018-01-23
Thank you, deadflowr. Didn't know about byobu and purging kernels that way. I knew there must be something easier than the housekeeping task I was assigning myself with every kernel update. I may be old, but I can still learn.

---

### Post by deadflowr on 2018-01-23
> **djchandler said:**
> Thank you, deadflowr. Didn't know about byobu and purging kernels that way. I knew there must be something easier than the housekeeping task I was assigning myself with every kernel update. I may be old, but I can still learn.

purge-old-kernels was only added to byobu with the version around 16.04 uses, maybe 15.10.
Prior to that it was in the catchall bikeshed package which holds packages that have no home yet:
[http://blog.dustinkirkland.com/2010/10/introducing-bikeshed-package.html]("http://blog.dustinkirkland.com/2010/10/introducing-bikeshed-package.html")

So for users running 14.04 the purge-old-kernels is in bikeshed, fwiw.
(In case someone happens upon this thread running 14.04 and complains that byobu did not have the package.)

---

### Post by vic-0611 on 2018-02-23
Hello again deadflowr,

After having updated successfully two new kernels (now the system has 4.4.0-116-generic), I executed:

```
sudo apt autoremove --purge
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias      
Leyendo la información de estado... Hecho
0 actualizados, 0 nuevos se instalarán, 0 para eliminar y 0 no actualizados.
```

But I'm not sure if the old and "damaged" one, 109, was removed. What's the easiest way to check the kernel versions that Grub has to its disposal? It is a bit strange, but pressing the "shift" key while booting isn't working.

---

### Post by deadflowr on 2018-02-23
> But I'm not sure if the old and "damaged" one, 109, was removed. What's the easiest way to check the kernel versions that Grub has to its disposal? It is a bit strange, but pressing the "shift" key while booting isn't working. 

It's easier to find what you have than what you don't.
try a simple ls /boot
```
ls /boot
```
> but pressing the "shift" key while booting isn't working
If using an UEFI system use ESC to get the grub menu.
Or try speed clicking the shift key when the screen starts to change from the first boot screen.

---

### Post by Impavidus on 2018-02-23
Or use```
dpkg --list "linux-image-*"
```to see which kernels are installed as far as the package manager is concerned. First make the terminal window wide, or the output will get truncated.

Although I rarely need the grub menu, I prefer to see it on every boot, just to be sure I can access it without problems that one day I need it. I configured grub to show its menu on every boot for 3 seconds. Just edit /etc/default/grub.

---

### Post by vic-0611 on 2018-02-23
Yes, it seems it is an UEFI system, because the esc key worked:

[ATTACH=CONFIG]278640[/ATTACH]

This information matches with the contents of /boot directory:

```
:~$ ls /boot
total 146M
-rw-r--r-- 1 root root 1,2M ene  9 22:28 abi-4.4.0-109-generic
-rw-r--r-- 1 root root 1,2M ene 19 14:06 abi-4.4.0-112-generic
-rw-r--r-- 1 root root 1,2M feb 13 01:57 abi-4.4.0-116-generic
-rw-r--r-- 1 root root 187K ene  9 22:28 config-4.4.0-109-generic
-rw-r--r-- 1 root root 187K ene 19 14:06 config-4.4.0-112-generic
-rw-r--r-- 1 root root 187K feb 13 01:57 config-4.4.0-116-generic
drwxr-xr-x 5 root root 4,0K feb 23 18:15 grub
-rw-r--r-- 1 root root  37M feb 15 19:32 initrd.img-4.4.0-109-generic
-rw-r--r-- 1 root root  37M feb 23 18:14 initrd.img-4.4.0-112-generic
-rw-r--r-- 1 root root  37M feb 23 18:15 initrd.img-4.4.0-116-generic
-rw-r--r-- 1 root root 179K ene 28  2016 memtest86+.bin
-rw-r--r-- 1 root root 181K ene 28  2016 memtest86+.elf
-rw-r--r-- 1 root root 181K ene 28  2016 memtest86+_multiboot.bin
-rw-r--r-- 1 root root 2,7K feb 13 01:57 retpoline-4.4.0-116-generic
-rw------- 1 root root 3,8M ene  9 22:28 System.map-4.4.0-109-generic
-rw------- 1 root root 3,8M ene 19 14:06 System.map-4.4.0-112-generic
-rw------- 1 root root 3,8M feb 13 01:57 System.map-4.4.0-116-generic
-rw------- 1 root root 6,8M ene  9 22:28 vmlinuz-4.4.0-109-generic
-rw------- 1 root root 6,8M ene 19 14:06 vmlinuz-4.4.0-112-generic
-rw------- 1 root root 6,9M feb 13 01:57 vmlinuz-4.4.0-116-generic
```

It seems that 109 version is still available. I guess there is one more kernel version needed to be able to do without the 109.

---

### Post by vic-0611 on 2018-02-24
Yeah, I tried it before asking, but I discarded it because looks like it shows all the kernels that have been installed:

```
+++-===============================-====================-====================-====================================================================
rc  linux-image-4.4.0-101-generic   4.4.0-101.124        amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-103-generic   4.4.0-103.126        amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-104-generic   4.4.0-104.127        amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-109-generic   4.4.0-109.132        amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-112-generic   4.4.0-112.135        amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-116-generic   4.4.0-116.140        amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-21-generic    4.4.0-21.37          amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-22-generic    4.4.0-22.40          amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-24-generic    4.4.0-24.43          amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-28-generic    4.4.0-28.47          amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-31-generic    4.4.0-31.50          amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-34-generic    4.4.0-34.53          amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-36-generic    4.4.0-36.55          amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-38-generic    4.4.0-38.57          amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-43-generic    4.4.0-43.63          amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-45-generic    4.4.0-45.66          amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-47-generic    4.4.0-47.68          amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-51-generic    4.4.0-51.72          amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-53-generic    4.4.0-53.74          amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-57-generic    4.4.0-57.78          amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-59-generic    4.4.0-59.80          amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-62-generic    4.4.0-62.83          amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-63-generic    4.4.0-63.84          amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-64-generic    4.4.0-64.85          amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-66-generic    4.4.0-66.87          amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-70-generic    4.4.0-70.91          amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-71-generic    4.4.0-71.92          amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-72-generic    4.4.0-72.93          amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-75-generic    4.4.0-75.96          amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-77-generic    4.4.0-77.98          amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-78-generic    4.4.0-78.99          amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-79-generic    4.4.0-79.100         amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-81-generic    4.4.0-81.104         amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-83-generic    4.4.0-83.106         amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-87-generic    4.4.0-87.110         amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-89-generic    4.4.0-89.112         amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-92-generic    4.4.0-92.115         amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-93-generic    4.4.0-93.116         amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-96-generic    4.4.0-96.119         amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-97-generic    4.4.0-97.120         amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-98-generic    4.4.0-98.121         amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-101-gen 4.4.0-101.124        amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-103-gen 4.4.0-103.126        amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-104-gen 4.4.0-104.127        amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-109-gen 4.4.0-109.132        amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-112-gen 4.4.0-112.135        amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-116-gen 4.4.0-116.140        amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-21-gene 4.4.0-21.37          amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-22-gene 4.4.0-22.40          amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-24-gene 4.4.0-24.43          amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-28-gene 4.4.0-28.47          amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-31-gene 4.4.0-31.50          amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-34-gene 4.4.0-34.53          amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-36-gene 4.4.0-36.55          amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-38-gene 4.4.0-38.57          amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-43-gene 4.4.0-43.63          amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-45-gene 4.4.0-45.66          amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-47-gene 4.4.0-47.68          amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-51-gene 4.4.0-51.72          amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-53-gene 4.4.0-53.74          amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-57-gene 4.4.0-57.78          amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-59-gene 4.4.0-59.80          amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-62-gene 4.4.0-62.83          amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-63-gene 4.4.0-63.84          amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-64-gene 4.4.0-64.85          amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-66-gene 4.4.0-66.87          amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-70-gene 4.4.0-70.91          amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-71-gene 4.4.0-71.92          amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-72-gene 4.4.0-72.93          amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-75-gene 4.4.0-75.96          amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-77-gene 4.4.0-77.98          amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-78-gene 4.4.0-78.99          amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-79-gene 4.4.0-79.100         amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-81-gene 4.4.0-81.104         amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-83-gene 4.4.0-83.106         amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-87-gene 4.4.0-87.110         amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-89-gene 4.4.0-89.112         amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-92-gene 4.4.0-92.115         amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-93-gene 4.4.0-93.116         amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-96-gene 4.4.0-96.119         amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-97-gene 4.4.0-97.120         amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-98-gene 4.4.0-98.121         amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic             4.4.0.116.122        amd64                Generic Linux kernel image


```

---

### Post by Impavidus on 2018-02-24
Those with rc have been removed, but not purged. Which doesn't really matter, as this is nothing more than a bit of clutter in dpkg's output.

---

### Post by deadflowr on 2018-02-24
You might have been booting into the -109 kernel whenever autoremove was run, so in that case it might not even try to remove it.
You can remove it manually if you want.
see if apt purging the image and header packages for it clears it
```
sudo apt purge linux-image-4.4.0-109-generic linux-headers-4.4.0-109-generic
```
(Double check my spelling,  please)

You can also clear all those rc'd packages if you like. So the output looks cleaner and more streamlined (and easier to read)
I run this simple one-liner once in a while to clear those:
```
dpkg -l | grep ^rc | awk '{print $2}' | xargs sudo apt purge -s
```
I run this command first as this runs a simulation of what will happen (that's what the -s is for)
If it looks good then I switch that -s to a -y for yes, otherwise it might hang or quit on me.
```
dpkg -l | grep ^rc | awk '{print $2}' | xargs sudo apt purge -y
```
rc'd packages are already removed, but they still have some configuration files leftover.
The long and short of it is  even though you may have a lot, they don't take up much space at all.
So if you clear those out to save space then the most you'll probably get is a couple of megabytes, at best.

---

### Post by vic-0611 on 2018-03-03
Thank you, deadflowr. Finally, the x-109 kernel is dropped out from the operating system. I also cleaned the rc packages, because my desktop has a solid hard drive of only 128 GB, so space matters. I erased them in my laptop, too, which has the same hard drive type and size.

---

