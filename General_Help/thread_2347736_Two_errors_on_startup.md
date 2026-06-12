---
title: "Two errors on startup"
date: 2016-12-28
forum: General Help
---

### Post by 4l3x2 on 2016-12-28
Good morning.

I installed Xubuntu (16.10 with proprietary drivers on and fully updated) in an old pc (of mine), 32bits, but as the system starts I get a generic error two times.
I tried to read something from dmesg, but I wasn't able to find the issue.
Please find attached 2 files:
- the screenshot of the error; it is the same as the second, the window says: An error occurred at a system program; Do you want to report it now? Cancel, Report.
- the output of dmesg -T -H > dmesg.txt (zipped to fit in the limits)

The system works fine (just a little slow, but I don't need speed on this pc) but I'd like to get rid of these errors so that my parents won't get in alarm.

Thank you very much in advance.
Alex[ATTACH=CONFIG]272878[/ATTACH]

---

### Post by DuckHook on 2016-12-28
Two suggestions:

[LIST=1]
[*]Try booting a LiveUSB/DVD of Xenial (16.04). It is **L**ong **T**erm **S**upport, more stable and has more bugs ironed out than Yaketty (16.10). And if for your parents, then presumably, you don't want them to have to deal with Yaketty's End of Life in 6 month's time. If stable, I recommend that you install Xenial rather then Yaketty. General users are best using LTS versions.
[*]When the error box pops up, choose "report the problem" and then look in your apport log. You can also parse through your old apport logs but may need to use *zcat* for older compressed logs. Example:```
zcat /var/log/apport.log.2.gz
```This will often point to further reports in */var/crash/* which you would then parse through as well. I'm afraid that this sort of convoluted detective work is necessary to diagnose such problems.
[/LIST]
Nothing from your dmesg jumps out at me either.

You mention "proprietary drivers". Which drivers are those? It looks to me like you are using nouveau, which is not proprietary. If so, then good. I find that it is best with old HW to keep the default FOSS drivers if they work. Are proprietary drivers for USB WIFI?

Do you need to use a 32-bit OS? Please post results of:```
sudo lshw -C system -C processor | egrep -i 'width|sse|pae'
```

---

### Post by 4l3x2 on 2016-12-29
Wow, really thank you....

This is the output of the command:

```
alex@Alessandro:~$ sudo lshw -C system -C processor | egrep -i 'width|sse|pae'
    width: 32 bits
       width: 32 bits
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow eagerfpu 3dnowprefetch vmmcall cpufreq
alex@Alessandro:~$
``` 

The driver is:

Processor microcode firmware for AMD cpu's from AMD 64 microcode

There is not an alternative driver, the status was simply disabled before installing the proprietary version.

I don't have any apport.log, but after writing this post I'll do a report and try to find the file.

Please find attached the locales.0.crash file, I deleted the dmesg part and many dpkg messages as well, because they were redundant, but if you need I'll re send the complete file.

---

### Post by 4l3x2 on 2016-12-29
Update:
I tried to reboot three times and I didn't get any error.

I also tried to use internet and some software to stress the pc but nothing happened.

I'll try to install some software from synaptic (which sometimes give me a warning of Not able to drop privileges), if I don't get any error anymore I'll consider the issue solved.

Just a question for the version:
how can I avoid an update to the newer version when checking and installing updates from synaptic?
Is there any special message that the system gives to the user of a full system update?

Thank you very much.

---

### Post by DuckHook on 2016-12-29
Your issue is this bug: [https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/1647838](https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/1647838)

It is a newly reported bug with no "me-too"s reported yet, so your instance would be confirmation that it affects multiple users. You would be doing the community a big favour if you would open a launchpad account, go to the above page that I've already linked you to, and report the bug by clicking on the green "This bug affects 1 person. Does this bug affect you?" link. That way, it gets the attention of the developers. If you report it, please attach the same file that you attached to your latest post. That will help them chase down the problem more quickly.

In a nutshell, the *locales* service appears to be generate an error in a subprocess specific to your installation. It may be a combination of your hardware, flavour, version and other obscure settings. The other fellow is running Yaketty too. Since I can't find any reference to this bug in Xenial, it appears to be a Yaketty problem, though this is pretty thin evidence on the strength of just two known occurrences. What this means is that, if you follow my advice and install Xenial, this problem may be rendered academic.

In the meantime, since it is not causing any other problems, it is something you can just ignore. Since Yaketty is only a non-LTS, it may not even get fixed. After all, it does not seem to be critical and Yaketty will be end of life in a few months. This incident exemplifies why non-LTS releases should really be avoided by general users seeking stability and reliability over shiny new gadgets that they will probably never use.

---

### Post by DuckHook on 2016-12-29
> **4l3x2 said:**
> …I'll try to install some software from synaptic (which sometimes give me a warning of Not able to drop privileges), if I don't get any error anymore I'll consider the issue solved.You needn't install additional software just to stress the system. In fact, it's probably not a good idea to install anything more on an old PC than what is strictly necessary. Complexity is the enemy of stability, and given the fact that your CPU and MOBO are truly only 32-bits, it's best to keep things really simple.> …how can I avoid an update to the newer version when checking and installing updates from synaptic?There are arcane ways to do this, but it is not a good idea. Updates are needed to close off security holes and to squash bugs (like the one you have just discovered). For all we know, it may have been a recent update that made your bug go away.> Is there any special message that the system gives to the user of a full system update?The system will not automatically upgrade you to the next version. You will be asked in a pop-up if you want to do so and can refuse. However, because you are on Yaketty, this means that you will quickly reach end of life and go out of support. That would be a really bad move. Neither apps nor the OS itself will be updated and any security exploits discovered by the bad guys will just become gaping holes on your computer waiting to get you pwned.

As has already been stated, you must either resign yourself to the constant upgrade treadmill every six months, or bite the bullet and reinstall with Xenial (16.04) which won't need upgrading until 2019.

---

