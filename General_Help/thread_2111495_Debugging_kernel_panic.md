---
title: "Debugging kernel panic"
date: 2013-02-02
forum: General Help
---

### Post by MadEgg on 2013-02-02
I have an issue with my Ubuntu 12.10 setup (Kubuntu actually, but not relevant) where I run into kernel panics at certain points.

I have more or less reliably been able to reproduce the problem. It seems related to excessive memory usage.

I have a Java application that analyzes loads of text (using UIMA) and stores results in memory and a PostgreSQL database. When I leave this running for a long time with a lot of memory allocated, it will always crash at some point after, ie:

```

java -Xmx4096M -jar UIMARunner.jar

```

So reduce other factors influencing it, I have executed this from a text terminal after shutting down lightdm

I have captured an image of the kernel panic at some point, the error is more or less like this:

```

[ 8703.160542] BUG: unable to handle kernel paging request at ffff8801afc4dc50
[ 8703.163166] IP: [<ffffffff8108f8c9>] select_no_hz_load_balancer+0x9/0x70
[ 8703.165790] PGD 1c0c063 PUD dfeda067 PMD 0
[ 8703.168417] Oops: 0000 [#1] SMP
[ 8703.171040] CPU 2
[ 8703.171053] Modules linked in:[ 8703.173642]  snd_emu10k1_synth snd_emux_synth snd_seq_virmidi gpio_ich snd_Seq_midi_emu1 snd_emu10k1 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_util_mem snd
_hwdep coretemp kvm_intel snd_seq_midi kvm snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device microcode snd serio_raw lpc_ich soundcore emu10k1_gp gameport usblp fglrx(P0) 17core_edac eda
c_core mac_hid parport_pc rfcomm bnep bluetooth ppdev lp parport nfsd binfmt_misc nfs lockd fscache auth_rpcgss nfs_acl sunrpc vesafb uas usb_storage firewire_ohci hid_generic firewire_core mxm_wmi cr
c_itu_t r8169 usbhid hid pata_jmicron wmi
[ 8703.187509] Pid: 0, comm: swapper/2 Tainted: P       0 3.5.0-18-generic #29-Ubuntu Gigabyte Technology Co., Ltd. X58A-UD3R/X58A-UD3r
[ 8703.190174] RIP: 0010:[<ffffffff8108f8c9>]  [ffffffff8108f8c9>] select_nohz_load_balancer+0x9/0x70
[ 8703.192835] RSP: 0018:ffff880196a25eb8  EFLAGS: 00010046
.....
[ 8703.265376] Kernel panic - not syncing: Attempted to kill the idle task!

```

Hardware:
- Gigabyte X58A-UD3R mainboard
- 3 x GeIL GV36GB1333C9TC (6GB RAM total)
- Intel Core i7 930
- Sapphire HD5770 1GB GDDR5 PCIE (AMD GFX card)

Since I have an SSD in this machine, I don't have any swap space set up. While it might be the case that it's running out of memory (although I should be able to allocate 4GB of the 6GB to Java, right?), this should not cause a kernel panic.

Since it's seems to be a issue related to memory, I tried running memtest86 from a USB-stick (the one supplied with Ubuntu is buggy and always fails at test #7), but the memory came out just fine there.

Since the kernel panic mentions that the kernel is tainted, I tried removing the fglrx driver using jockey-kde, but this results in a similar problem.

The main problem is that I usually turn my monitor off when I start the Java-program, but when I come back and turn the monitor on after it has crashed, I get no screen at all, there's no signal coming from the video card. It's therefore hard to see the exact message after every crash.

Before, this also happened while the same process was running in a graphical environment: what happens then is that the entire screen just completely freezes, I cannot move the mouse, I cannot type, nothing happens. However, I also do not get a error message / kernel panic. Most likely because that does not work in a graphical environment?

Anyway, I would really like to debug this problem and find the cause, but I'm uncertain at how to proceed in pinpointing this problem.

Or should I file a bug report about this?

---

### Post by dino99 on 2013-02-02
as you are describing that problem, it seems to me more an app/process issue than a kernel one. So the first step is to find which one is to blame. There are some usefull tools like valgrind & fwts to lets you know what is going on

[http://stackoverflow.com/questions/143791/how-do-i-find-which-process-is-leaking-memory](http://stackoverflow.com/questions/143791/how-do-i-find-which-process-is-leaking-memory)

[https://wiki.ubuntu.com/Kernel/Reference/fwts](https://wiki.ubuntu.com/Kernel/Reference/fwts)

---

### Post by rnerwein on 2013-02-02
> **dino99 said:**
> as you are describing that problem, it seems to me more an app/process issue than a kernel one. So the first step is to find which one is to blame. There are some usefull tools like valgrind & fwts to lets you know what is going on

[http://stackoverflow.com/questions/143791/how-do-i-find-which-process-is-leaking-memory](http://stackoverflow.com/questions/143791/how-do-i-find-which-process-is-leaking-memory)

[https://wiki.ubuntu.com/Kernel/Reference/fwts](https://wiki.ubuntu.com/Kernel/Reference/fwts)
hi
think you are wright. what does the people think why the unix/linux system always have a swap deviec (not for hibernation). if that guy had some swap device he will get a warning about of running out of swap-space. if you look at solaris you ervery time think the box is using swap - oh no - it's preallocated to be on the saver side. and now to the problem of the guy. 
open a second terminal in parallel with running top. sort the output to memory usage.
i bet you have a run away process. to avoid this (before your box panics) have a look at /etc/scecurity. in the limits.conf you can restrict your user about memory ( soft and hard limit). it's better your application die than the system is running out of memory.
habe a look at the message: 
 Pid: 0, comm: swapper/2 [COLOR=Red]Tainted[/COLOR]: P       0 3.5.0-18-generic  ciao

---

### Post by MadEgg on 2013-02-02
While I agree that it might be running out of swap, that should IMO not be a reason for a kernel panic. When that happens, the kernel should start killing user processes to free memory, not crash altogether.

I currently added a large swap file to see whether that avoids the problem. If it does, I still think it's a bug that the kernel could handle more gracefully.

Btw, it's not a runaway process, it's a process that is meant to consume a lot of memory for local cache of objects stored in the database.

---

### Post by tgalati4 on 2013-02-02
Having a large swap file will allow the kernel to page properly to hard disk, which will in turn slow the machine down to a crawl.  This will give you time to examine CPU utilization, RAM utilization, and other system statistics (sysstat).  But without it, java, being a runtime environment (and hence a virtual machine), the kernel doesn't have the tools to kill it gracefully when it runs out of RAM.  Having a large swap file gives some cushion for this to happen.  Your swap file should probably be 2 to 3 times your largest expected JAVA image.

The *tainted* kernel means you have some binary blobs running--graphics, wireless or other proprietary hardware modules, that if your kernel should crash, you would have no insight into what is going on, if those modules are involved.

I assume that your JAVA app is not crashing because of proprietary modules.  The traceback clearly shows a paging issue, which is tied to moving RAM, which happens when you run out of memory.

---

### Post by MadEgg on 2013-02-02
The kernel is tainted due to the fglrx driver. I also tried the same process with this driver uninstalled, and got the same result. So that indeed does not seem to be the problem.

Interesting to read that Java has a different 'role' in the OS than other processes do. I just ran another instance with a swap file of 4GiB, which did not result in a kernel panic, but to a crash of Java with a request to report it to Oracle... 

The 'weird' thing remains that on Windows (which I also run without a swap file because of the SSD), the same problem just results in the process being killed by Windows, and not in the entire OS crashing.

---

### Post by bantuvez on 2013-02-02
> **MadEgg said:**
> 
The 'weird' thing remains that on Windows (which I also run without a swap file because of the SSD), the same problem just results in the process being killed by Windows, and not in the entire OS crashing.

You can make the kernel to kill the process which triggered the out-of-memory condition. Just pass the

 ```
 vm.oom_kill_allocating_task = 1
```

parameter to the kernel. (Based on [this]("http://www.codeproject.com/Articles/131862/Special-Features-of-Linux-Memory-Management-Mechan"). )

Never tried it, maybe you should try it. 
[]("http://www.codeproject.com/Articles/131862/Special-Features-of-Linux-Memory-Management-Mechan")

---

### Post by MadEgg on 2013-02-03
Still confuses me.

That article says that if OOM occurs and panic_on_oom is set to >= 1, then a kernel panic will occur on OOM. panic_on_oom is set to 0 on my system, so that's no explanation.

It also mentions that if oom_kill_allocating_task is set to 1, it should kill the task that requested memory when OOM occured. Seems reasonable to me, however, this is also set to 0, so this also shouldn't happen.

The article mentions that if oom_kill_allocating_task is set to 0, it will order the process list by badness and kill the 'baddest' process, which might be the same process that tried to allocate too much memory. Also sounds fair, though complicated. This should be the behavior I am experiencing. However, it doesn't mention any kernel panics.

So, while unexpected behavior may be expected if my java process requests more memory than is available (which is weird, because I say it should use 4096M max, while I have 6144M physical RAM, and as I was saying, I wasn't running any graphical desktop at all, just a text console at Vt1), I believe this should not lead to a full stop, even if there's no swap space available.

---

### Post by bantuvez on 2013-02-03
> **MadEgg said:**
> Still confuses me.

That article says that if OOM occurs and panic_on_oom is set to >= 1, then a kernel panic will occur on OOM. panic_on_oom is set to 0 on my system, so that's no explanation.



panic_on_oom set to 1 means that panic occurs at any OOM situation. (the only case when the kernel won't panic is mentioned in the article) It doesn't mean that the kernel wont panic if the panic_on_oom is set to zero. If something intolerable happens during the memory freeing process then the kernel will panic. 

As the article mentions, setting the vm.oom_kill_allocating_task parameter to 1 helps to avoid the resource-expensive tasklist scan and makes OOM killer very predictable. So, IMHO, try setting the vm.oom_kill_allocating_task parameter to 1: If this eliminates the kernel panic, then we can be sure that this problem is related to some OOM problem. If it won't eliminate the panic, then we can be almost sure that its not some kind of OOM problem.

---

### Post by MadEgg on 2013-02-04
Ok, I tried setting vm.oom_kill_allocating_task to 1 and ran the same program again.

I got another kernel panic after a while. Basically the same as I posted before, except the line with 'Tainted' now changed to this:

```

[34648.952263] Pid: 0, comm: swapper/3 Tainted: G       D    3.5.0-18-generic #29-Ubuntu Gigabyte Technology Co., Ltd. X58A-UD3R/X58A-UD3R

```

Does this mean it's not tainted anymore? It shouldn't be, as the flgrx driver is no longer loaded, I'm currently using the open source radeon driver.

I ran it twice, to be fair. The first time the process ended with a SEGV, a segmentation fault. This could occur due to a the process being killed as a result of going OOM, I suppose?

---

### Post by bantuvez on 2013-02-05
Your kernel is tainted with D flag which means there were errors with the kernel preceding this error, so this error report is not trustworthy.  (The G flag do mean that the fglrx driver is not loaded, only open source modules are loaded.)

So you should check the kernel log for BUGs or OOPS before this error.  (If it could capture them before the panic.)

> 
the process ended with a SEGV, a segmentation fault. This could occur  due to a the process being killed as a result of going OOM, I suppose?I guess so.

EDIT: Also the likely OOM kill should be reported in the kernel logs. Check for it.

---

