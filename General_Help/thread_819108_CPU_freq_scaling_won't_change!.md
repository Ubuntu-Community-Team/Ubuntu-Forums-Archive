---
title: "CPU freq scaling won't change!"
date: 2008-06-05
forum: General Help
---

### Post by El Lance-O on 2008-06-05
So I recently enabled CPU scaling on my laptop so I could save some of the battery. It worked fantastically for awhile, but now it has a mind of it's own.

It will change the frequency when it pleases, and does not change when I set it to.

I've tried using different governors, but it just won't change.

As I am typing, my computer is about to freeze because it won't change to 1.73.

Oh...wait...it decided to. How nice.

Anyways, I have a duel core intel CPU, and here's my cpufreq-info:

```
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 1.73 GHz
  available frequency steps: 1.73 GHz, 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: conservative, powersave, userspace, ondemand, performance
  current policy: frequency should be within 800 MHz and 1.33 GHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 1.33 GHz.
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 1.73 GHz
  available frequency steps: 1.73 GHz, 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: conservative, powersave, userspace, ondemand, performance
  current policy: frequency should be within 800 MHz and 1.33 GHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 1.33 GHz.
```

Please help, I don't want to have to turn it off completely, it was awesome when it worked properly.

---

### Post by El Lance-O on 2008-06-06
Ok this is getting really irritating.

The last several threads I have made, or posts for that matter, have been completely ignored.

What happened to the wonderfully helpful Ubuntu community?

---

### Post by sdennie on 2008-06-06
I don't think userspace is the governor you want to use.  You may want to switch to ondemand.  Also, what did you do to "enable CPU scaling"?  It's generally turned on by default with no user intervention because running the CPU ondemand makes essentially no drop in performance for the vast majority of users and it saves power.

---

