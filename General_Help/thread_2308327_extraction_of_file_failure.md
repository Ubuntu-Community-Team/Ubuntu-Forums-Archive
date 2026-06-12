---
title: "extraction of file failure"
date: 2016-01-02
forum: General Help
---

### Post by latha2 on 2016-01-02
Dear all,
  I am trying to patch my linux kernel-2.6.39  with rt patch of patch-2.6.33.9-rt31.xz but after downloading the patch-2.6.33.9-rt31.xz I'm not able to extract it
as it's showing 
  bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Error is not recoverable: exiting now 

So I again started downloading bz2 file and it's showing while extracting 

tar: This does not look like a tar archive
tar: Skipping to next header
tar: Exiting with failure status due to previous errors
 Would you please let me know what to do now..
Thank you.

---

### Post by TheFu on 2016-01-02
xz compression isn't bz compression. You need a different tool that is XZ compression compatible. Sorry, I don't remember the name of it right now, it isn't gunzip, compress, bunzip, bunzip2 or unzip - probably not the answer you want, but at least it excludes some tools while you search for the right one.

Couldn't stand it ... searched and found this: [https://askubuntu.com/questions/92328/how-do-i-uncompress-a-tarball-that-uses-xz](https://askubuntu.com/questions/92328/how-do-i-uncompress-a-tarball-that-uses-xz)

Looks like GNU tar does it already. Please always show **the exact commands being used** to get faster help in the future.

---

### Post by steeldriver on 2016-01-02
Like the second message says, the contents are not a tar archive - in fact they're a plain-text diff file. So you can just use bunzip2 directly:

```

bunzip2 ~/Downloads/patch-2.6.33.9-rt31.bz2

```

The result should be a file called patch-2.6.33.9-rt31

```

$ file ~/Downloads/patch-2.6.33.9-rt31
/home/steeldriver/Downloads/patch-2.6.33.9-rt31: unified diff output, ASCII text

```

BTW, what do you plan doing with it? it appears to be an old (~ 2011) patch that has almost certainly been rolled into current releases of the kernel / rt module

---

### Post by TheFu on 2016-01-02
He has an .xz file, not a .bz file.  OTOH, my suggestion to use tar/gnu-tar isn't useful either.
There are XZ_Utils which contain the programs needed. The xz manpage summary:

```
NAME
       xz,  unxz,  xzcat, lzma, unlzma, lzcat - Compress or decompress .xz and
       .lzma files
```

The **xz** tool was already installed on my Ubuntu 14.04 server.

---

### Post by steeldriver on 2016-01-02
The OP downloaded both .xz and .bz2 files I think, but yes you're right they can use 'xz' for the .xz one

---

### Post by TheFu on 2016-01-02
Wow. Guess I didn't get enough sleep last night at all, plus I'm not wearing my contacts today (world is a little fuzzy; has been a few days).

For the xz file, 
```
unxz patch-2.6.33.9-rt31.xz
``` is needed. Then the patch can be applied.

---

### Post by latha2 on 2016-01-04
yes ,Thank you sir !:D 
I got it !
While patching I got like this
```
patching file Documentation/hwlat_detector.txt
patching file Documentation/trace/histograms.txt
patching file MAINTAINERS
Hunk #1 succeeded at 2923 with fuzz 2 (offset 474 lines).
patching file Makefile
Hunk #1 FAILED at 1.
1 out of 1 hunk FAILED -- saving rejects to file Makefile.rej
patching file arch/Kconfig
Reversed (or previously applied) patch detected!  Assume -R? [n] y
Hunk #1 succeeded at 30 with fuzz 1 (offset -14 lines).
patching file arch/alpha/include/asm/rwsem.h
Hunk #1 FAILED at 18.
Hunk #2 FAILED at 38.
Hunk #3 FAILED at 47.
Hunk #4 FAILED at 79.
Hunk #5 FAILED at 94.
Hunk #6 FAILED at 121.
Hunk #7 FAILED at 130.
Hunk #8 FAILED at 155.
Hunk #9 FAILED at 184.
Hunk #10 FAILED at 208.
Hunk #11 FAILED at 227.
Hunk #12 FAILED at 250.
12 out of 12 hunks FAILED -- saving rejects to file arch/alpha/include/asm/rwsem.h.rej
patching file arch/alpha/kernel/time.c
Hunk #1 FAILED at 106.
Hunk #2 FAILED at 136.
2 out of 2 hunks FAILED -- saving rejects to file arch/alpha/kernel/time.c.rej
patching file arch/arm/Kconfig
Reversed (or previously applied) patch detected!  Assume -R? [n] y
Hunk #1 succeeded at 245 (offset 5 lines).
patching file arch/arm/mach-shark/leds.c
Reversed (or previously applied) patch detected!  Assume -R? [n] y
patching file arch/arm/mm/cache-l2x0.c
Hunk #1 FAILED at 26.
Hunk #2 FAILED at 47.
Hunk #3 FAILED at 59.
Hunk #4 FAILED at 83.
Hunk #5 FAILED at 97.
Hunk #6 FAILED at 109.
Hunk #7 FAILED at 123.
Hunk #8 FAILED at 135.
8 out of 8 hunks FAILED -- saving rejects to file arch/arm/mm/cache-l2x0.c.rej
patching file arch/arm/mm/context.c
Reversed (or previously applied) patch detected!  Assume -R? [n] y
Hunk #1 succeeded at 16 with fuzz 2 (offset 2 lines).
Hunk #2 FAILED at 32.
Hunk #3 FAILED at 54.
2 out of 3 hunks FAILED -- saving rejects to file arch/arm/mm/context.c.rej
patching file arch/arm/mm/copypage-v4mc.c
Reversed (or previously applied) patch detected!  Assume -R? [n] y
Hunk #2 succeeded at 76 with fuzz 1.
patching file arch/arm/mm/copypage-v6.c
Reversed (or previously applied) patch detected!  Assume -R? [n] y
Hunk #2 succeeded at 89 (offset -7 lines).
Hunk #3 succeeded at 102 (offset -7 lines).
Hunk #4 succeeded at 122 (offset -7 lines).
patching file arch/arm/mm/copypage-xscale.c
Reversed (or previously applied) patch detected!  Assume -R? [n] y
Hunk #2 succeeded at 98 with fuzz 1.
patching file arch/arm/mm/fault.c
Reversed (or previously applied) patch detected!  Assume -R? [n] y
Hunk #1 succeeded at 289 (offset 16 lines).
patching file arch/arm/mm/mmu.c
Reversed (or previously applied) patch detected!  Assume -R? [n] y
Hunk #1 succeeded at 31 (offset 1 line).
patching file arch/arm/oprofile/common.c
Hunk #1 FAILED at 48.
1 out of 1 hunk FAILED -- saving rejects to file arch/arm/oprofile/common.c.rej
can't find file to patch at input line 2132
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/arch/arm/oprofile/op_model_xscale.c b/arch/arm/oprofile/op_model_xscale.c
|index 724ab9c..cbe91ee 100644
|--- a/arch/arm/oprofile/op_model_xscale.c
|+++ b/arch/arm/oprofile/op_model_xscale.c
--------------------------
File to patch: 
```

Can you please help me out ..
Thanks a lot in advance :)

---

### Post by matt_symes on 2016-01-04
Hi

Are you really using a kernel this old ?

```
2.6.33.9
```

I doubt it very much and i suspect that was the kernel the patch was developed for ;)

Just install a low-latency kernel from the repositories. It kind of replaces the real time kernels now.

Kind regards

---

### Post by latha2 on 2016-01-04
I installed  linux kernel-2.6.39 in ubuntu 14.04  in which I want to patch rt-2.6.33.9 (I'm attempting this to do .. but not sure whether going in the correct direction to get real time kernel )

---

### Post by matt_symes on 2016-01-04
Hi

> **latha2 said:**
> I installed  linux kernel-2.6.39 in ubuntu 14.04  in which I want to patch rt-2.6.33.9

Fair play but it's still the wrong kernel version if the patch name is accurate.

>  (I'm attempting this to do .. but not sure whether going in the correct direction to get real time kernel )

Some info about the kernels

[https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel](https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel)

Kind regards

---

### Post by matt_symes on 2016-01-04
Hi

Have you come across this ?

[https://rt.wiki.kernel.org/index.php/Main_Page](https://rt.wiki.kernel.org/index.php/Main_Page)

Kind regards

---

### Post by latha2 on 2016-01-04
sir,
Sorry, for this question/doubt ,how can I distinguish in the linux kernel pub whether it's low latency or not !
can you suggest me which is better to get the kernel into rtkernel.
(As I heard that ubuntu 12.04 is better platform than ubuntu-14.04)

---

### Post by latha2 on 2016-01-05
Sir ,Is it necessary for 4.3.3 kernel thr RTPATCH should be 4.3 ?
Because I found 4.1 and 4.4 RTptach

---

### Post by matt_symes on 2016-01-05
Hi

> **latha2 said:**
> Sir ,Is it necessary for 4.3.3 kernel thr RTPATCH should be 4.3 ?
Because I found 4.1 and 4.4 RTptach

Yes it usually is.

Kind regards

---

### Post by latha2 on 2016-01-06
When I tried to unzip the rt patch of 
 patch-3.8.13.14-rt31.tar.xz
by using unxz  patch-3.8.13.14-rt31.tar.xz this is what it showed 

unxz: patch-3.8.13.14-rt31.tar.xz: No such file or directory

What can be done to unzip this patch ?

Thank you.

---

### Post by matt_symes on 2016-01-06
Hi

You need to be in the same directory as the patch.

Once you have patched the kernel ....

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

Kind regards

---

