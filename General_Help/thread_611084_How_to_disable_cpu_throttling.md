---
title: "How to disable cpu throttling?"
date: 2007-11-12
forum: General Help
---

### Post by moxie12 on 2007-11-12
Hi,

I'm trying to install ATLAS, which requires disabling of cpu throttling as described here:
[http://math-atlas.sourceforge.net/atlas_install/atlas_install.html#SECTION00032000000000000000]("http://math-atlas.sourceforge.net/atlas_install/atlas_install.html#SECTION00032000000000000000")

I turned off power management through BIOS, but this didn't work-- got a configuration error that indicated that cpu throttling was still  enabled.

How do I do this? I'm running a Dell Latitude c610 under Feisty.

Thanks!

---

### Post by dacap06 on 2007-11-12
One of the easiest ways to turn off power management and CPU throttling is to turn off ACPI at boot time.  The way to do that is launch your favorite editor in root mode (e.g. the "Run Command.. " menu entry, then enter the command gksudo gedit).  Once your editor is up, open the file /boot/grub/menu.lst.  

You need to add the kernel option to turn off ACPI to the two Ubuntu Linux boot lines.  The appropriate text to add is shown in bold in the example boot line below.

kernel  /boot/vmlinuz-2.6.20-16-generic root=UUID=4f146ca4-8f7f-47c4-a72e-e19e101288cd ro quiet splash **acpi=off**

---

### Post by moxie12 on 2007-12-02
Thanks! I did try your suggestion but it didn't work (get the same error message.)


I also  tried the following:
1.  editing /etc/modprobe.d/blacklist by adding:
#try to stop cpu throttling
blacklist cpufreq
blacklist cpufreq_conservative     
blacklist cpufreq_ondemand        
blacklist cpufreq_stats          
blacklist freq_table              
blacklist cpufreq_userspace 

But this didn't work either and in fact I notice that these modules seemed to have loaded despite my blacklisting them, because if I try:
 lsmod |grep freq

I get:
cpufreq_conservative     8200  0 
cpufreq_ondemand        9228  1 
cpufreq_stats           7360  0 
freq_table              5792  3 speedstep_ich,cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2688  0 
cpufreq_userspace       5408  0 

The CPU Frequency applet running does seem to switch back and forth between 731MHz and 997MHz.  

2. mucking around with BIOS settings to turn off powersaving options. This didn't work.

Might anyone have a suggestion on what's going wrong here?

Thanks again!

---

### Post by moxie12 on 2007-12-02
Never mind, I solved it!

sudo  /usr/bin/cpufreq-selector -g performance seems to have worked.

Still not sure why my blacklists didn't work,  but that's not so important now.

---

