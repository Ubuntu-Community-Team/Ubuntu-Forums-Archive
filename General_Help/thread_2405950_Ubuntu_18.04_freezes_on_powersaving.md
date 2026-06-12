---
title: "Ubuntu 18.04 freezes on powersaving"
date: 2018-11-13
forum: General Help
---

### Post by rudiservo on 2018-11-13
I have a Thinkpad T450 with Intel(R) Core(TM) i5-5300U.

this happens whenever I have TLP or powertop savings on.

1st I had random freeze while using Wifi but disabling powersavings on wifi worked while I was on wifi but I still get random freezes.

I read on some forums that disabling C6 or maximum C1 state on grub will help but power consumption will go up but I would rather not go this way.

Already did try the latest 4.19.1 kernel, the machine seems more responsive and stable but still I do have these random freezes...

Am I missing anything? Shouldn't this be more stable?

---

### Post by rudiservo on 2018-11-21
Ok, I have done some testing and for now things are stable

Probably the problem is with the CPU governing or SATA link power.

What I did in TLP was basicly to disable
#CPU_SCALING_GOVERNOR_ON_AC=powersave
#CPU_SCALING_GOVERNOR_ON_BAT=powersave


and change SATA
SATA_LINKPWR_ON_AC=max_performance
SATA_LINKPWR_ON_BAT=min_power

but reading the TLP config file there is something about the governor that I do not know if the kernel already does something and thats why it needs to be disabled in TLP.

# Hint: CPU parameters below are disabled by default, remove the leading #
# to enable them, otherwise kernel default values are used.

# Select a CPU frequency scaling governor.
# Intel Core i processor with intel_pstate driver:
#   powersave(*), performance.
# Older hardware with acpi-cpufreq driver:
#   ondemand(*), powersave, performance, conservative, schedutil.
# (*) is recommended.
# Hint: use tlp-stat -p to show the active driver and available governors.
# Important:
#   powersave for intel_pstate and ondemand for acpi-cpufreq are power
#   efficient for *almost all* workloads and therefore kernel and most
#   distributions have chosen them as defaults. If you still want to change,
#   you should know what you're doing! You *must* disable your distribution's
#   governor settings or conflicts will occur.


maybe the conflicts do freeze the system completly, the SATA link I am not so convinced but if it is stable, I wont change it for now.

---

