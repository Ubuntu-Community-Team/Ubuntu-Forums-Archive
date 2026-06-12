---
title: "problem compiling kernel from ubuntu source"
date: 2006-11-05
forum: General Help
---

### Post by Walldorf2000 on 2006-11-05
I have a similar problem to this [http://ubuntuforums.org/showthread.php?p=1612788]("http://ubuntuforums.org/showthread.php?p=1612788") thread.

I try to compile standard ubuntu 6.10 kernel 2.6.17 for my PC. I created a new .config with make menuconfig.

I optimized for my K6-III with mga and sb16 and removed all kind of unnecessary devices.

Compilation ended with the following errors:
>   CC      arch/i386/lib/usercopy.o
  AR      arch/i386/lib/lib.a
  GEN     .version
  CHK     include/linux/compile.h
  UPD     include/linux/compile.h
  CC      init/version.o
  LD      init/built-in.o
  LD      .tmp_vmlinux1
drivers/built-in.o: In function `ide_wait_not_busy':
(.text+0x3de9b): undefined reference to `touch_nmi_watchdog'
make[1]: *** [.tmp_vmlinux1] Fehler 1
make[1]: Verlasse Verzeichnis '/usr/src/linux-source-2.6.17'
make: *** [debian/stamp-build-kernel] Fehler 2
   

I tried the original .config and this time it ran through.

Thus it is caused by my configuration. Any idea which change in menuconfig causes the problem? How can I find it? Each try which fails costs me hours](*,)

---

### Post by John.Michael.Kane on 2006-11-05
Have a read
[http://ubuntuforums.org/showthread.php?t=217657&highlight=kernel](http://ubuntuforums.org/showthread.php?t=217657&highlight=kernel)
[http://ubuntuforums.org/showthread.php?t=157560&highlight=compiling+kernel](http://ubuntuforums.org/showthread.php?t=157560&highlight=compiling+kernel)
[http://ubuntuforums.org/showpost.php?p=1174954&postcount=507](http://ubuntuforums.org/showpost.php?p=1174954&postcount=507)

---

### Post by Walldorf2000 on 2006-11-12
Thanks, but I had this read before I started.

I took me a lot of time but I could isolate the problem. When I switch off SMP I get the error, when I switch it on the make succeeds.

I have no idea why nobody else runs into this problem :confused:

---

### Post by biker3 on 2006-11-12
Hi! I also have this problem. I have a Centrino Dual Core, but for use ralink drivers for rt2570 from serialmonkey I must disable SMP and PREEMPT, and for this I have to build a new kernel.

But when I start to compile I see the same error](*,)

---

### Post by Walldorf2000 on 2006-11-13
Should we create a bug report? I have read that bug reports concerning kernel compilations will be closed without comment.

If yes, any help is welcome. Which category should I use and which information is needed?

---

### Post by compres on 2006-11-18
I have the same error here with no idea of what to do just like you guys.  Not nice.

---

### Post by compres on 2006-11-20
Are we the only ones with this problem? WTF.  I just trying compiling it with the only change on the architecture to p3 coppermime and it compiled.  I've tried this on the laptop and on my desktop with ubuntu edgy, same problems, so more people should have this problem.

I still don't know which option breaks the compilation.

And to those who say you should not compile your own kernel I have to say on old systems yes you should.  This p3 laptop with 256 of ram is running way faster on a custom 2.6.18.2, but I want the ubuntu's since I get all their patches and support for wireless lan, etc.

By faster I mean faster boot, faster loading of programs, faster compile times, faster at multitasking, and  it is really faster meaning you notice it it's like 1.5-3X as fast as the generic ubuntu's.

I will keep trying until I find which option breaks the compile...

---

### Post by Walldorf2000 on 2006-11-21
> I still don't know which option breaks the compilation.

There is one single option which breaks it for me:
> When I switch off SMP I get the error, when I switch it on the make succeeds.
Thus I need to compile a SMP kernel for my single CPU](*,)

---

### Post by compres on 2006-11-25
I got it working without the SMP option checked.  I am going to review my changes again and let you know later in like one hour.

---

### Post by compres on 2006-11-25
OK guys, I solved the problem by checking this option on processor type and features:

Local APIC support on uniprocessors


It compiles perfectly now, and I do no t have SMP enabled.

---

### Post by Walldorf2000 on 2006-11-27
As far I remember I switched off the APIC option. I thought it is not relevant for my old sockel 7 PC.

Though we have got two solutions.

Either switch APIC on or switch SMP on.

Maybe I give it another try ans switch off SMP and switch on APIC. But I guess I will not have time for that in the next days.

---

### Post by zgornel on 2006-11-27
Interesting. I disabled the touch_nmi_watchdog() reference in the kernel sources and made it work. If I disable SMP (LAPIC already disabled) I get poor X performace (as i dead slow). I'm going to try disabling SMP and enabling APIC and see what happens.


[COLOR="Red"]EDIT[/COLOR]: Worked. It seems that disabling SMP (for uniprocessor machines ofcourse) and enabling Loca APIC solved the touch_nmi_watchdog() issue.

---

### Post by zgornel on 2006-11-27
> **Walldorf2000 said:**
> Should we create a bug report? I have read that bug reports concerning kernel compilations will be closed without comment.

If yes, any help is welcome. Which category should I use and which information is needed?
It should qualify as a bug: First time I compiled the kernel was an out of the box source with the config of the generic kernel and the processor changed from 5x86 to Pentium-M.

---

