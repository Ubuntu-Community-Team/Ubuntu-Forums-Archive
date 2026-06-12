---
title: "Fans At Max RPM on Dell XPS 9570 and nothing seems to work"
date: 2018-07-26
forum: General Help
---

### Post by guguma2 on 2018-07-26
Hello All,

I just came back to Ubuntu after a long time since I need a unix based system to do some work. I managed to successfully install Ubuntu 18.04 LTS on my Dell XPS 9570, after switching the SATA mode, disabling nouveau since it just hangs, installing nvidia-390 and registering its modules due to safe boot etc. etc. and finally managed to boot into a freshly installed Ubuntu sytem. Just as I hoped that nothing would break:

 I realized that my fans are running at full speed all the time.

Here is what I tried:

1. used cpufreq to set spu in powersaving mode, did not work.

2. installed lm-sensors, fans are running at around 4000 RPM, GPU Temp at 47 C, CPU Temp 55 C at idle. Not too bad.

3. installed i8kutils and configured it so that fans only work at setting "2" if the temperatures go over 70 C. Tried it with both i8k and dell-smm-hwmon modules. i8mon registers the temps correctly, attempts to set fan speeds correctly as I have assigned in config file. It says temp is at 55 C, i8kfan 1 1, yet the fans keep spinning in setting 2.

I read somewhere that I can disable bios fan control entirely, yet it comes with a huge warning that this change persists along restarts and I should remember to give fan control back to bios if I happen to boot into my windows system. Not going to do it since I am a forgetful person and I do not intent to burn my CPU.

This is a dealbreaker as fans blazing like this would prevent me from doing my work, and it is detrimental to the health of my laptop. I am at a loss here, what am I supposed to do, a solution to this problem would be greatly appreciated, as I have to get to work urgently as well.

Thanks in advance.

---

### Post by pascal-masschelier on 2018-07-31
Hi,
another dell xps 9570 owner here, running ubuntu 18.04
same problem with fan spinning at full speed.
I can't explain why, but the following command seems to calm down the fans:

[FONT=courier new]sudo systemctl status lm-sensors[/FONT]

---

### Post by pascal-masschelier on 2018-08-02
I have installed nvidia drivers with 
ubuntu-drivers autoinstall

in nvidia-settings (as root)
you may choose in PRIME Profiles, Intel (Power saving mode). it has a good effect on fans and battery.

---

### Post by ivandolchevic on 2018-10-13
Change the profile cannot be a solution. A temporary workaround may be. 
You can read the same on the Dell forum. That's an hardware issue. The graphic card fans aren't even detected by any tools like tlp, thermald or others.

---

