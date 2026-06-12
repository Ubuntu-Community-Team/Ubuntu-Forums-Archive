---
title: "VirtualBox High CPU Usage"
date: 2008-06-23
forum: General Help
---

### Post by xdavidx on 2008-06-23
My cpu is always at 100% when i turned on my Vbox. There's any fix or workaround for it?
i've searched already..but no luck. 
thks

---

### Post by danwood76 on 2008-06-23
What spec is your system?
What guest OS are you trying to run?

It may be that you dont have enough RAM to support a virtual machine and so the system is swapping the memory to the disk causing high CPU usage.

---

### Post by xdavidx on 2008-06-23
> **danwood76 said:**
> What spec is your system?
What guest OS are you trying to run?

It may be that you dont have enough RAM to support a virtual machine and so the system is swapping the memory to the disk causing high CPU usage.

Intel(R) Celeron(R) CPU 2.80GHz
2Gb ram
HD 230gb
ATI RADEON 9600 pro 256MB
Mortherboard asus P4S800

Trying to run Winxp.

---

### Post by xdavidx on 2008-06-23
No fix right?!

---

### Post by danwood76 on 2008-06-23
Celeron processors are usually pretty poor with any sort of load, that could very well be the cause of the issue.

What process is actually using all the CPU? (you can check with top or system monitor)

---

### Post by argail1980 on 2008-06-23
how much of the RAM have you given to XP? when that's too little, VB starts swapping and then the whole thing gets awfully slow

---

### Post by jed4czar on 2008-08-22
I wouldn't mind seeing this thread pursued. 

I am also experiencing high CPU (80%-99% according to "top") usage by virtualbox.My CPU is 3.2Ghz and I have a 804 Mb of RAM assigned to Trixbox running inside VB (2Ghz on the "real" machine). 

One suggestion from the user manual presents itself, although I'm not too confident in attempting it:

11.3. Linux guests
11.3.1. Linux guests may cause a high CPU load
Some Linux guests may cause a high CPU load even if the guest system
appears to be idle. This can be caused by a high timer frequency of the
guest kernel. Some Linux distributions, for example Fedora, ship a Linux
kernel configured for a timer frequency of 1000Hz. We recommend to
recompile the guest kernel and to select a timer frequency of 100Hz. 

I would like to give this a go but not sure where to start????

Any guidance would be appreciated. Thanks

---

### Post by jerome1232 on 2008-08-22
3.2ghz but what KIND of processor, clock speed is by far not the whole story when it comes to processors.

---

### Post by jed4czar on 2008-08-22
> **jerome1232 said:**
> 3.2ghz but what KIND of processor, clock speed is by far not the whole story when it comes to processors.

jed@jed-desktop:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 6
model name	: Intel(R) Celeron(R) D CPU 3.20GHz
stepping	: 4
cpu MHz		: 3199.196
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 6
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc up pebs bts sync_rdtsc pni monitor ds_cpl cid cx16 xtpr lahf_lm
bogomips	: 6406.51
clflush size	: 64

---

### Post by Gadgetech on 2008-08-23
VirtualBox OSE eats up about 25% of my CPU even after the virtual machine is shut down, but with VirtualBox still open.  I don't have this problem with the "non-free" version from here: [https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

Make sure you remove both virtualbox-ose and virtualbox-ose-modules prior to installing the .deb from this site.

---

### Post by thunderking2106 on 2008-10-11
After doing this my cpu spikes ceased to spike around 85% - 95% idling. within my XP Virtualmachine with 512mb dedicated memory. If you happen to have a modern processor (Core2Duo, Athlon/Turion) you can increase  your VMs performance by enable hardware virtualization. with your VM shutdown go into the Sun XVM Virtualbox dialogue box. Right-click on your VM go to settings. Click on the advanced tab and check the Enable VT-x/AMDV select ok.

---

### Post by sonoud on 2008-10-27
Hi, I registered ubuntu forum because of this thread. 
still no workaround yet? 
I suffered this problem for 5 years already. 
It seems my both thinkpad 600x and z60m can not run any virtual machines. 
Sorry to say that I am running opensuse 11.0. 
But I have exact the same problem!!!!
CPu is always 100% busy regardless whether the guest OS is installed or not. 
as long as the VM is on. even dummy VM will make 100% cpu busy. 
My CPU should be power enough for this. 

model name      : Intel(R) Pentium(R) M processor 2.00GHz
2 GB RAM. 

Regardless how much CPU and How much RAM I tried to assign to virtual machine. it doesn't help. 

Forget to say that. I tried both VMware Workstation and VirtualBox. all VM softwares will give me the same result. 

Since I suffered this for 5 years. I have kept finding solutions. but so far, no luck. 

other people just keep telling me this is impossible. how can they run VMs easily ........ 

anyway, hopefully, some virtualbox experts or VM experts around here can provide me some tips.....

---

### Post by yaknowwat on 2008-10-27
I also suggest the non-free version it has bug fixes and improvements versus the full open version.

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

also so people know they do have a repo for intrepid they just don't have it listed.

deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) intrepid non-free

Make sure to get the verification key too.

---

### Post by danwood76 on 2008-10-27
Have you tried qemu?

If you are running an x86 guest on an x86 host kqemu is really fast. (kernel mode accelerator)
Slow downs come when you are trying to run a, for example, mips guest on an x86 host.
Because of the translation of commands its a lot slower.

I use Qemu now, virtual box I found to be too slow, vmware is too bulky and proprietry (and very slow).
Also your processor is quite slow and outdated, with a faster processor you will end up with much better performance.
And also having dual cores helps a lot (as you obviously have the guest running mainly on one core and your host mainly on the other)
I currently run XP in a qemu virtual guest on my laptop and my desktop. Its fast enough to use happily on my laptop and its natural speed on my desktop.

---

### Post by stickman77 on 2008-11-24
I has a slightly different issue with xp guest on ubuntu 8.10.

while the xp guest was idle is was virtualbox sitting at around 70% cpu constant on the host.

I have since discovered that it was googletalk causing the problem. I uninstalled googletalk and now the cpu usage on the host is 7% while the guest is idle.

I hope this may help others.

cheers

---

### Post by Delever on 2009-03-29
I moved from vmware to VirtualBox recently, and I think I managed to pin this problem more accurately.

See this bug report:

[http://www.virtualbox.org/ticket/3613](http://www.virtualbox.org/ticket/3613)

It would be helpful if you try to repeat this scenario on your VirtualBox installation (by installing and running Google Chrome).

EDIT: or Google Talk (you need to login)

---

### Post by jed4czar on 2009-05-07
OK, a year down the track and I am using this solution - It seems a bit counter-intuitive but... Run a second VM, in my case, [DSL]("http://damnsmalllinux.org/download.html") with 64 mb ram (I think DSL can run with as little as 8mb) I turned everything else off (audio usb etc) so as not to interfere with other apps in the real pc. CPU loading comes down to <30%. Apparently it has something to do with Load Balancing of the CPU by VB. I can live with it.

Post Script: - You don't even need an OS in the VM. Just set up a new VM and boot to "no bootable medium found! System Halted" and it will still do the job"

---

### Post by Lockheed on 2009-05-25
> **jed4czar said:**
> Post Script: - You don't even need an OS in the VM. Just set up a new VM and boot to "no bootable medium found! System Halted" and it will still do the job"

ROTFL This hardly elegant solution is totally working!

---

### Post by kammajaega on 2009-06-16
thx a lot,  seems to work here too, but only slightly changing cpu usage...

---

### Post by kknull on 2009-06-17
does not work with me...

host: ubuntu 9.04 64bit
guest: windows xp x64 edition

---

### Post by gombihu on 2009-06-18
I managed to solve it for my 9.04-VB 2.2.4:
I simply changed the Computer from ACPI to Standard PC. First boot the XP crashed, but next time it re-detected all devices. Though I have an old one core computer. 
The CPU usage dropped down from 50-60 to 1% :)

---

### Post by danwood76 on 2009-06-18
You could try using qemu (kvm). I find it to be better than virtualbox.
Or you can use the free version of vmware server.

---

### Post by Jose Catre-Vandis on 2009-07-01
I tried both solutions on an XP (SP3) guest. 

Changing to Standard PC would not allow boot to desktop and would freeze the VM. I could get into Safe Mode but would not boot up to normal desktop. So I had to change back to get my VM working again, but with the high CPU load.

Adding in a dummy VM worked a treat, knocking CPU usage down from 60% to 4%

---

### Post by hsachdevah on 2009-07-09
> **Jose Catre-Vandis said:**
> I tried both solutions on an XP (SP3) guest. 

Changing to Standard PC would not allow boot to desktop and would freeze the VM. I could get into Safe Mode but would not boot up to normal desktop. So I had to change back to get my VM working again, but with the high CPU load.

Adding in a dummy VM worked a treat, knocking CPU usage down from 60% to 4%

I trid the same. But didn't helped me. What exactly are you dong. 
I am using 9.04

---

### Post by ksraju007 on 2010-08-03
Thanks for sharing this excellent workaround.. running centos as guest.

cpu usage was always above 90%. just added a dummy VM with 8 mb ram and kept it running parallelly. processor usage comes down immediately to < 10%.

:)

---

### Post by ja4 on 2010-10-06
Making a Dummy with no OS worked for me too, 100% CPU goes down to 1%.

---

### Post by soldier1st on 2010-10-07
did you try the Virtualbox non free version and still had the issue?

---

