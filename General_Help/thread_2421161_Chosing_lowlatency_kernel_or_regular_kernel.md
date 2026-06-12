---
title: "Chosing lowlatency kernel or regular kernel"
date: 2019-06-17
forum: General Help
---

### Post by dreweinhorn on 2019-06-17
I have Ubuntu Studio 18.04 installed on a ThinkPad T520 laptop.

By default, it uses the low latency kernel which makes a lot of sense when using it with midi instruments.

But, I wonder if this makes sense when using it as a plain old laptop in situations where real-time performance is irrelevant

I was investigating this with the Phoronix Test Suite and got some anomalous results. Memory performance is better using the powersave governor option than it is with the performance option. Perhaps, this is quirk resulting from the lowlatency kernel. But, that's the topic for another thread in the future with much more detail.

For now, I just want to run some more benchmarks using the regular kernel for comparison. But somehow, the option for choosing which kernel to use is not being presented during boot.

---

### Post by CatKiller on 2019-06-17
You'll get slightly lower performance and lower battery life with the lowlatency kernel than the generic one. Neither of those things is a priority; low latency is the priority. It doesn't make sense to use it if you value those things over having low latency. The differences are small, though. 

> **dreweinhorn said:**
> For now, I just want to run some more benchmarks using the regular kernel for comparison. But somehow, the option for choosing which kernel to use is not being presented during boot.

To have another kernel displayed at boot time, you need another kernel installed (generic, say) and you need Grub configured to display its menu at boot time. It doesn't by default.

---

### Post by garvinrick4 on 2019-06-17
#Link to kernel to use.
[kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/")
Scroll to bottom and choose a kernel say 5.1
open and choose these four and download one at a time to save should be in Downloads
notice what they are for future.
   [linux-headers-5.1.0-050100_5.1.0-050100.201905052130_all.deb]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.1/linux-headers-5.1.0-050100_5.1.0-050100.201905052130_all.deb")
 [linux-headers-5.1.0-050100-generic_5.1.0-050100.201905052130_amd64.deb]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.1/linux-headers-5.1.0-050100-generic_5.1.0-050100.201905052130_amd64.deb")
   [linux-image-unsigned-5.1.0-050100-generic_5.1.0-050100.201905052130_amd64.deb]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.1/linux-image-unsigned-5.1.0-050100-generic_5.1.0-050100.201905052130_amd64.deb")
  [linux-modules-5.1.0-050100-generic_5.1.0-050100.201905052130_amd64.deb]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.1/linux-modules-5.1.0-050100-generic_5.1.0-050100.201905052130_amd64.deb")
 Lets Drag and drop them to desktop just in case other .deb files in Downloads.

#install kernel all 4 at once.

> cd Desktop
see if they are on Desktop
> ls
install
> sudo dpkg -i *.deb
#good idea to update grub most all the time when working with grub,  kernel install will do it but...
> sudo update-grub
> reboot
#Check kernel
Open a terminal
> uname -a
Done

---

### Post by garvinrick4 on 2019-06-17
If anyone ever wants to see their kernels installed without rebooting.
install "synaptic-package-manager'

in search window type:  linux-generic
will show all your installed kernels with green in  box next to;

You can also remove from there if needed always keep a few installed 
in case one doesn't work you have another to boot from
Need to remove "linux-modules'  and linux-headers also make sure they are the same kernel
versions can be just one number different

Remember only ones with green boxes are installed.
Synapic-package-manager is interesting really

---

### Post by Doug S on 2019-06-18
> **dreweinhorn said:**
> I was investigating this with the Phoronix Test Suite and got some anomalous results. Memory performance is better using the powersave governor option than it is with the performance option. Perhaps, this is quirk resulting from the lowlatency kernel. But, that's the topic for another thread in the future with much more detail. I would be very interested in that thread, because those results do not make sense to me. By the way, telling us the CPU frequency scaling governor is not enough information, we also need to know the CPU frequency scaling driver you use. Example:

```
doug@s15:~$ [COLOR="#FF0000"]cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver[/COLOR]
acpi-cpufreq
acpi-cpufreq
acpi-cpufreq
acpi-cpufreq
acpi-cpufreq
acpi-cpufreq
acpi-cpufreq
acpi-cpufreq
```(Note: I normally run the intel_pstate driver, but am in the middle of something just now.)

> **CatKiller said:**
> You'll get slightly lower performance and lower battery life with the lowlatency kernel than the generic one. Neither of those things is a priority; low latency is the priority. It doesn't make sense to use it if you value those things over having low latency. The differences are small, though.Agree, if there is a difference it is small. Since the tickless stuff allows idle CPUs to go into deep sleep for multiple seconds (up to 4 seconds, or even longer if the watchdog timer is disabled) at a time, regardless of the tick rate (250 Hz for Generic and 1000 Hz for Low Latency), the tick rate is less important. At some point, I'll come back with some supporting data for the generic and lowlatency versions for kernel 5.4-rc5.

---

### Post by #&amp;thj^% on 2019-06-18
> **Doug S said:**
> I would be very interested in that thread, because those results do not make sense to me. By the way, telling us the CPU frequency scaling governor is not enough information, we also need to know the CPU frequency scaling driver you use. Example:

```
doug@s15:~$ [COLOR="#FF0000"]cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver[/COLOR]
acpi-cpufreq
acpi-cpufreq
acpi-cpufreq
acpi-cpufreq
acpi-cpufreq
acpi-cpufreq
acpi-cpufreq
acpi-cpufreq
```(Note: I normally run the intel_pstate driver, but am in the middle of something just now.)

Agree, if there is a difference it is small. Since the tickless stuff allows idle CPUs to go into deep sleep for multiple seconds (up to 4 seconds, or even longer if the watchdog timer is disabled) at a time, regardless of the tick rate (250 Hz for Generic and 1000 Hz for Low Latency), the tick rate is less important. At some point, I'll come back with some supporting data for the generic and lowlatency versions for kernel 5.4-rc5.

+1 I agree, and Doug S knows I run low-lat kernels almost excuslviely, my bench's show higher for low-lats than genric, with some adjustments that i won't go into now.
Battery life is almost identical for both versions.
I do remember with a xenial kernel that sucked my battery life on a low-lat kernel and droped my sound card (Doug S might remember that one ;)), and don't remember the version #.
```
 cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver
intel_pstate
intel_pstate
intel_pstate
intel_pstate

```

---

### Post by MartyBuntu on 2019-06-18
I used a low latency kernel on Ubuntu Studio for 6 years, until installing a regular kernel on an Ubuntu Mate 18.04 install with KXStudio packages for my audio (and some video) production work.
I really haven't noticed much of a difference. It would depend on how precise and highly scrutinized your needs are.

---

### Post by Doug S on 2019-06-18
Some simple test results (kernel 5.2-rc5 1000 Hz tick rate ("lowlatency") and 250 Hz tick rate ("generic"):

Idle system (and by "Idle", I really mean it, as my test server has no GUI and I disabled a bunch of services):
250 Hz kernel: Processor package power: 3.70 watts ( - just a little).
1000 Hz kernel: Processor package power: 3.70 watts ( + just a little).
Note: I would have to do a longer test to be certain, but say 10 milliwatts difference (maybe 0.3%).

pipe-test on 1 core (meaning using both CPUs on the one core, instead of across two cores) X 2 instances. i.e. two cores active, and two idle.
Why this test? Because it spends a lot of time in idle state 0 (polling), which has had some changes in the last 1/2 year.

250 Hz kernel: Processor package power: 40.4 watts ( - just a little) and performance of 4.90 uSec per loop.
1000 Hz kernel: Processor package power: 40.4 watts and performance of 4.95 uSec per loop.
O.K. so that was unexpected, but the 250 Hz kernel seems to go into and out of idle state 0 about twice as often.

The above tests were done using the intel_pstate CPU frequency scaling driver and the powersave governor and the teo idle governor.
Some additional pipe test numbers for the 250 Hz kernel:

intel_cpufreq driver (i.e. intel_pstate in passive mode) ondemand governor, teo idle governor: 32.3 watts 5.5 uSec per loop.
intel_cpufreq driver, ondemand governor, menu idle governor: 32.2 watts 5.6 uSec per loop.

Why such a big difference? I think (have not yet proved) because the intel-pstate driver in active mode (I do not have HWP) includes idle state 0 in its busy calculation, but passive/ondemand does not, and so it scales the frequency down a bit.

For reference, the main turbostat command used for these tests:

```
sudo turbostat --quiet --Summary --show Busy%,Bzy_MHz,PkgTmp,PkgWatt,GFXWatt,IRQ --interval 60
```

Note: My system never hits thermal throttling triggers. actually, thermald was disabled.

---

