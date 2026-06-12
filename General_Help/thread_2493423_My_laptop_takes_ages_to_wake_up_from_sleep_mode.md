---
title: "My laptop takes ages to wake up from sleep mode"
date: 2023-12-14
forum: General Help
---

### Post by smogol on 2023-12-14
Hi everyone,
I have a big issue after the last update of Ubuntu 22.04.
Once I set my laptop on sleep, 3 to 4 times, I had to hard reset my device to use it under linux.
After some tests, I found out that I have to wait more that 1 minute to get a chance to get my laptop to run again.

Is there any known issue of that behaviour?
I am quite a newby on these problem,
I tried the trick to change to ubuntu xorg but without big success.

Thanks to to all for any help!
Greetings

---

### Post by TheFu on 2023-12-17
Standby or hibernation?  There's a big difference.

---

### Post by MAFoElffen on 2023-12-18
I have found that most [s]hibernation[/s] 'wake from sleep' problems are either related to the graphics driver, or the c state that the CPU is allowed to go down when when it enters a sleep state. Modern CPU's, different than those in the past are now allowed to go down to a 9, where somewhere between 4 & 6, it cuts the power to the cores...

I think that is where a lot of wake problems occur.

What I usually recommend it (for both AMD & Intel CPU's) that seem to have a problem waking from sleep, is to add the "intel.idle_cstate=4" boot parameter to the GRUB_CMDLINE_LINUX_DEFAULT= line of file /etc/default/grub file and do 
```

sudo update-grub

```
to pick up the change... I don't know why that parameter has "intel" as part of it for AMD CPU's (also), but that is it and it does work. That seems to allow them to sleep, without "dying".

And to make sure they have a good recent graphics driver.

---

### Post by ne29914 on 2023-12-19
Hibernate is not an "idle" or "sleep" state. It's a total power down.
Waking is a cold boot plus reloading the previous system state. It takes a little longer than a normal cold boot, which should be obvious.

---

### Post by MAFoElffen on 2023-12-19
> **ne29914 said:**
> Hibernate is not an "idle" or "sleep" state. It's a total power down.
Waking is a cold boot plus reloading the previous system state. It takes a little longer than a normal cold boot, which should be obvious.
@ne29914 --

I did say "hibernation", didn't I... Bad choice of words. I meant to say "wake from a sleep state..."

Then answer on your own, in your own words why that boot parameter does help users to wake from a sleep state?  That has helped over 20 users here in just the past year. Especially if they had AMD CPU's with amdgpu.

I'm listening... It sounds like you think you know. Please explain further to share with everyone. I have an open mind. Please present your case.

---

### Post by ne29914 on 2023-12-21
No contest, I agree with what you said. The problem was using the term "Hibernate".
And we still don't know which it is from the OP.

---

### Post by MAFoElffen on 2023-12-21
True... Posting the results of these posted within Code tags:
```

grep -m1 -E 'model name' /proc/cpuinfo 
sudo lspci -nnk | grep -A3 -E 'Display|VGA|3D'

```
Would give us a start at that information...

---

