---
title: "ACPI: Setting maximum C-state"
date: 2007-06-21
forum: General Help
---

### Post by theycallhimtom on 2007-06-21
I want to be able to set the maximum C-state that my processor will idle in. I have tried echoing to /sys/module/processor/paramaters/max_cstate. After I do that I see the change in /proc/acpi/processor/CPU0/power. But while it says the maximum C state has been set, the usage of C1 still goes up when the cpu is idle. If I go into the BIOS and disable C states then the usage of C1 does not go up even when the computer is idle. I want to be able to change the maximum C state on the fly without using the BIOS, is there any way to do that? Thanks for the help!

---

### Post by yopnono on 2007-06-21
Put this in the /etc/rc.local script, and reboot.
echo 2 > /sys/module/processor/parameters/max_cstate
Were the number is the state you like to use.

---

### Post by theycallhimtom on 2007-06-21
I put the statement "echo 0 > /sys/module/processor/parameters/max_cstate" into /etc/rc.local. 

After rebooting /proc/acpi/processor/CPU0/power looks like:
active state:            C1
max_cstate:              C0
bus master activity:     00000000
maximum allowed latency: 8000 usec
states:
   *C1:                  type[C1] promotion[C2] demotion[--] latency[000] usage[00026813] duration[00000000000000000000]
    C2:                  type[C2] promotion[C3] demotion[C1] latency[005] usage[00000000] duration[00000000000000000000]
    C3:                  type[C3] promotion[--] demotion[C2] latency[020] usage[00000000] duration[00000000000000000000]

When I look at that file again the usage for C1 has gone up even though the max c state is set to 0. That means that the processor is the C1 state when I want to force it to be in C0. I know that in most cases you do not want to disable C1, but this is for a research project. Again thanks for the help.

---

### Post by yopnono on 2007-06-21
Really don't know but... I don't think you have any C0. Think it's 1-8 so 0 should do nothing.

---

### Post by theycallhimtom on 2007-06-21
[http://acpi.sourceforge.net/documentation/processor.html](http://acpi.sourceforge.net/documentation/processor.html) says that 
"(Note: C0 is not mentioned, it is the CPU "working" state)"

So forcing the maximum C state to 0 should in theory work.

---

