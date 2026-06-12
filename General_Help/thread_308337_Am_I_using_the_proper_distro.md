---
title: "Am I using the proper distro?"
date: 2006-11-27
forum: General Help
---

### Post by bg1256 on 2006-11-27
I have an HP a1530n with an Intel Pentium D dual core processor.

I'm running the standard Edgy eft distribution.

Am I running the system that will best utilize my hardware?

I only ask because I visited the Suse website, and it included my processor among the 64-bit processors and recommended the 64-bit OS.

Thanks!

---

### Post by ryan on 2006-11-27
> **bg1256 said:**
> I have an HP a1530n with an Intel Pentium D dual core processor.

I'm running the standard Edgy eft distribution.

Am I running the system that will best utilize my hardware?

I only ask because I visited the Suse website, and it included my processor among the 64-bit processors and recommended the 64-bit OS.

Thanks!

I am running the same processor on a Dell and I installed the i386 distro, the generic kernel will pick up the 2 cores (so you don't need to install a SMP kernel ) you can check and see if it is recognizing  both of them System > Administration > System Monitor > Resources tab. My understanding is that the Pentium D's can handle the 64 bit instruction set. Not sure how much that will help you in the real world unless you have 64 bit software. The main thing you need I think is for the OS to pick up both cores. I am by no means an expert so someone else may have a more detailed answer.

---

### Post by Cynical on 2006-11-27
Your processor is 64-bit, so you could use the 64-bit version of Ubuntu if you wanted to. The main benefits of doing this are support for more than 4GB of memory, faster compile times, and faster compression/decompression. Applications should be faster as well, but it may not be noticeable. The downside is that you have to do a few things differently if you want flash, java, and windows codec support. Read the 64-bit forum here and decide if the extra work is worth it

If you really want to utilize your hardware to its fullest in a 32-bit environment I would suggest compiling your own kernel and getting the latest drivers for your graphics card.

---

### Post by bg1256 on 2006-11-27
Well, it seems it's only picking up one.

[screenie]("http://i123.photobucket.com/albums/o299/bg1256/Screenshot-SystemMonitor.png")

So, anyone with experience with this processor?  

It seems to me that I've run the system monitor before, and it's recognized both cores, but right now, it's definitely not.

---

### Post by bg1256 on 2006-11-27
> **Cynical said:**
> 

If you really want to utilize your hardware to its fullest in a 32-bit environment I would suggest compiling your own kernel and getting the latest drivers for your graphics card.

I'll definitely take your advice.

Compiling me own kernel?  In all honesty, I wouldn't know where to start...

but, I do have the latest drivers for my graphics card - I do know that because I just updated them yesterday.

Thanks for the help.  I'll check it out right away... tomorrow, after the homework is done ](*,)

---

### Post by RAV TUX on 2006-11-27
> **bg1256 said:**
> I have an HP a1530n with an Intel Pentium D dual core processor.

I'm running the standard Edgy eft distribution.

Am I running the system that will best utilize my hardware?

I only ask because I visited the Suse website, and it included my processor among the 64-bit processors and recommended the 64-bit OS.

Thanks!

I have an Intel EM64T dual core processor....and SUSE failed miserably on preformance...

I would first try Ubuntu if it doesn't work for you post for help here in the UbuntuForums...

[SIZE=2](The only 64bit distro I could recommend to you outside of Ubuntu would be rpath x86_64 1.0.4
[http://www.rpath.com/rbuilder/project/rpath/release?id=5141)]("http://www.rpath.com/rbuilder/project/rpath/release?id=5141")[/SIZE]

---

### Post by kerry_s on 2006-11-28
> **bg1256 said:**
> I have an HP a1530n with an Intel Pentium D dual core processor.

I'm running the standard Edgy eft distribution.

Am I running the system that will best utilize my hardware?

I only ask because I visited the Suse website, and it included my processor among the 64-bit processors and recommended the 64-bit OS.

Thanks!


Your kidding right? You gave no info other than the cpu and brand/model and you want to know if something will work with it!
The only way you can really know is through trial and error. 
But with the specs you have given almost any linux will work.

---

### Post by bg1256 on 2006-11-28
> **kerry_s said:**
> Your kidding right? You gave no info other than the cpu and brand/model and you want to know if something will work with it!
The only way you can really know is through trial and error. 
But with the specs you have given almost any linux will work.

Well, thanks for the hostility.

It's a 2.8 GHz Intel Pentium D with 2 processing cores. I have one GB of RAM, upgradeable to four, should I so desire.

The only question I have is if I'd be better of using the 64-bit distribution, rather than the standard version.

---

### Post by Ramses de Norre on 2006-11-28
Probably not, you still need to tweak a lot of things to get stuff like java and flash and so on to run correctly in 64bit and I don't think it's worth the struggle for most people. So if you're system is running fine in 32bit: keep it like that.

---

### Post by bg1256 on 2006-11-28
Well, that's just it.  It's running fine, but I'm  not sure it's recognizing both my processing cores.
The system monitor only shows one.  But thanks for the response :)

---

### Post by doobit on 2006-11-28
I think, if you open the terminal and run uname -a then you will get a list that will tell you if both cores are recognized. 
It should look like two processors, I think. I've actually got two processors and it sees them both, so honestly I don't know what it would look like on a dual core.
<edit>
Actually, if I run dmesg, then it tells me when it loaded CPU#0 and CPU#1 
uname -a will only report the kernel version, processor type etc. I'm using the SMP kernel for multi-processors, It seems to me like you would need that for dual cores as well.

---

### Post by steevk on 2006-11-28
Interesting...check this out:

```
steev@steev-desktop:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 75
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 2
cpu MHz         : 2010.450
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni cx16 lahf_lm cmp_legacy svm cr8legacy ts fid vid ttp tm stc
bogomips        : 4026.10

steev@steev-desktop:~$ dmesg | grep CPU
[17179569.184000] WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
[17179569.184000] Initializing CPU#0
[17179572.416000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f
[17179572.416000] CPU: After vendor identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f
[17179572.416000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179572.416000] CPU: L2 Cache: 512K (64 bytes/line)
[17179572.416000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f
[17179572.416000] CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ stepping 02
```

Does that mean that It's only recognizing one core? that first line of the dmesg output seems to indicate that's the case...

```
steev@steev-desktop:~$ uname -a
Linux steev-desktop 2.6.17-10-386 #2 Fri Oct 13 18:41:40 UTC 2006 i686 GNU/Linux
```

There's that too...Which kernel should I be running for multiprocessing?

---

### Post by doobit on 2006-11-28
I guess you should be using the SMP kernel.

---

### Post by newlinux on 2006-11-28
if you are on edgy you should be using:
2.6.17-10-generic

which will recognize both cores. make sure you are booting into that kernel

---

### Post by bg1256 on 2006-11-28
> **newlinux said:**
> if you are on edgy you should be using:
2.6.17-10-generic

which will recognize both cores. make sure you are booting into that kernel

Okay, if I run uname -a, I get the following output
> benjamin@BG-desktop:~$ sudo uname -a
Linux BG-desktop 2.6.17-10-386 #2 Fri Oct 13 18:41:40 UTC 2006 i686 GNU/Linux
benjamin@BG-desktop:~$ 


which leads me to believe I might not be booting into the proper kernel? I'm not sure what I would need to do to change that. I'm still rather new at all this...](*,)


edit: if I run dmesg, I get the following in the processor section

> [17179569.184000] Processor #0 15:4 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[17179569.184000] Processor #1 15:4 APIC version 20
[17179569.184000] WARNING: NR_CPUS limit of 1 reached.  Processor ignored.

Not sure exactly what that means.

---

### Post by Lord Illidan on 2006-11-28
I am using dual core pentium D quite successfully with Edgy Eft. Also used it with fedora. Just install the smp kernel.

---

### Post by ~LoKe on 2006-11-28
Confirmed.  You need the generic or a custom compiled kernel to utilize both processors.

---

### Post by bg1256 on 2006-11-28
Okay.  How do I go about installing the proper kernel? Does that mean a fresh install of Edgy? Or can I do it without affecting my system?

---

### Post by ~LoKe on 2006-11-28
> **bg1256 said:**
> Okay.  How do I go about installing the proper kernel? Does that mean a fresh install of Edgy? Or can I do it without affecting my system?

It should be as simple as...

```
sudo apt-get install linux-image-2.6.17-10-generic
```

---

### Post by bg1256 on 2006-11-28
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-image-2.6.17-10-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
hmmmm....

---

### Post by Lord Illidan on 2006-11-28
Try this :

sudo apt-get install linux-686-smp

---

### Post by bg1256 on 2006-11-28
> **Lord Illidan said:**
> Try this :

sudo apt-get install linux-686-smp

Before I do this, I should post what I've just discovered.

I realized I'm running the 386 kernel because of some things I did to install Beryl and get aiglx up and running.

When I rebooted my computer just now, I realized I have the generic kernel install, and it is second on my grub menu. However, when I boot through that kernel, it doesn't successfully launch the GUI, and I'm left with only the command interface.

I'm not sure what I did to make it that way... I'll have to re-read the HowTo on the forums here to see if there is a way I can make it work.

My best guess is, I installed the 386 kernel to run Beryl, but not realizing it would only let me use one of my processing cores...

Gotta go to class...

---

### Post by ~LoKe on 2006-11-28
I've got beryl running with the generic kernel.  Well, I compiled my own, but I was using the generic kernel before.  Unfortunately I can't remember what you need to do in order to get it to work.

---

### Post by Lord Illidan on 2006-11-28
I got Beryl up and running with generic kernel and XGL. Perhaps AIGLX is the problem.

---

### Post by kerry_s on 2006-11-28
> **bg1256 said:**
> Well, thanks for the hostility.

It's a 2.8 GHz Intel Pentium D with 2 processing cores. I have one GB of RAM, upgradeable to four, should I so desire.

The only question I have is if I'd be better of using the 64-bit distribution, rather than the standard version.

That's not hostility, i was just saying you did not provide enough info. Sure your cpu's would work but what if your vid card didn't or you have one of those anti linux boards, would you have come back and said "hey you told me this would work".

You basically said "i have a computer will it work?"
When asking a question, the more info you can provide, the more someone can help you. In all likely hood there will be someone running something similar, maybe even the exact setup you have & they have already worked through the problems you might come across.

---

### Post by bg1256 on 2006-11-28
> **Lord Illidan said:**
> Try this :

sudo apt-get install linux-686-smp

This seemingly did nothing. The terminal said it installed fine, but I restarted, and nothing changed.

What should I be looking for?

> That's not hostility, i was just saying you did not provide enough info. Sure your cpu's would work but what if your vid card didn't or you have one of those anti linux boards, would you have come back and said "hey you told me this would work".

Apologies, then, for misunderstanding. I guess that was my frustration doing the talking.

Everything on my system is running fine, except for this problem, and I only realized it yesterday because my system was running slow. Brought up system manager and realized only one of the cores was working.

---

### Post by newlinux on 2006-11-28
You need to somehow get the generic kernel running. That's the one you want. I have it running with Beryl, but on a single proc computer so I don't think I can help you further. What error do you get when you run the generic kernel? Can you start X or a display manager manually?

---

### Post by bg1256 on 2006-11-28
Okay, when I boot into the generic kernel, I get a message telling me that X failed to load properly, and it allows me to view the detailed output.

I'll post what seems relevant:

```
Error: API Mismatch: the NVIDIA kernel module has the version 1.0-9626 but this X module has the version 1.0-9629. Please make sure that the kernel module and all NVIDIA driver components have the same version
```

It's the main error that shows up, and this surely seems to be the problem.

For now, what I'm attempting to do is to uninstall the generic kernel and reinstall it. Perhaps that will help.

Thanks for all the help, by the way.

---

### Post by bg1256 on 2006-11-28
Well, after a little more exploration after X fails to load, I found this:

> FATAL: Error running install command for nvidia
EE) NVIDIA(0): Failed to load the NVIDIA kernel modeul!
EE))NVIDIA(0): ***Aborting***
Screen(s) found, but none have a useable configuration

Weird.


> 
Try this :

sudo apt-get install linux-686-smp

I'm still unsure why this hasn't done anything for me...it installs just fine, but I don't know what to do from there.

---

### Post by kerry_s on 2006-11-28
Thats saying your nvidia is screwed up, boot the generic kernel & let it drop to command line. login & type> 
sudo nano /etc/X11/xorg.conf
scroll down to driver & change it from nvidia to vesa, then ctrl+ x & y & enter to save.
type> startx 
 that should get you to gui, then uninstall all the other kernels & nvidia. that should you back to the stock setup & you can start again.

---

### Post by bg1256 on 2006-11-28
Aha, okay.  I'm on that right away.

Thanks a million.

edit: the vesa driver must not be the right one for my card... because this is definitely not the way it should be.

I do have a gui in the generic kernel now, but everything is slow, windows distort, and beryl's not working properly either....


edit2:

Well, I updated the nvidia driver, and it's working!

Now, I should uninstall all oterh kernels than generic, yes?

You guys made my night :)

---

### Post by igknighted on 2006-11-28
The only way you will get the 686-smp kernel to boot is to add it to your grub menu...  I've never played around w/ smp before, but there should be some posts on it if you search.

---

### Post by bg1256 on 2006-11-28
Alright, thanks.

Now that I have the generic running and both cores are being recognized, I'm not sure there's a need to mess with the 686-smp kernel, unless it has advantages of which I'm unaware.

---

### Post by newlinux on 2006-11-28
686-smp and many other kernels have been obseleted by the generic linux kernel. The generic linux kernel does SMP. You don't want to use 686-smp, stick with the generic. Look at the comments of
```
 aptitude search 686 
```
and
```
 aptitude search linux-image
```

Glad you got it going! good luck with Beryl and Nvidia. VESA is slow, you'll probably want to get the nvidia binary drivers working again...

---

### Post by bg1256 on 2006-11-28
> **newlinux said:**
> 
Glad you got it going! good luck with Beryl and Nvidia. VESA is slow, you'll probably want to get the nvidia binary drivers working again...

Yes, vesa is slow.  I did get the binary drivers up and running again. And thanks for this... I'll check it out tonight.

---

### Post by kerry_s on 2006-11-28
> **bg1256 said:**
> Yes, vesa is slow.  I did get the binary drivers up and running again. And thanks for this... I'll check it out tonight.

Oops, sorry i forgot to mention you had to reinstall nvidia on the generic kernel to get all the matching parts. Just For future reference, the reason for the error was because you installed the nvidia drivers while using a different kernel, thus the mismatch. If something happens to your X remember you can always try the vesa driver as it will work on 90% of videos & can at least let you get to the gui to determine what is wrong. You can also use "nv" for yours since you have nvidia, nv is the free version.

Now just remove all the other kernels there no use to your setup. There just taking up space. Don't remove anything that says generic.

---

### Post by bg1256 on 2006-11-28
Thanks, kerry_s.

I've got everything running as smooth as silk now, thanks to your help :-D

---

