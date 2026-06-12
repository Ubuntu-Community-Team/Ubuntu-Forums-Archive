---
title: "Suspend issue on kernel somewhere after 4.13 - how to debug?"
date: 2019-10-15
forum: General Help
---

### Post by Paul_Jewell on 2019-10-15
Hello all, 

I recently upgraded to 19.04 from 18.04 which caused a kernel switch to some 5.x.x kernel. I noticed that this caused an issue with the suspend on my laptop. The symptoms of the issue are that the screen goes black and all  hdd activity stops, but the power light stays on/sleep light stays off, and the fan keeps running. There is no way to recover from this situation even with magic sysrq so the power button must be held down. Through some brute force testing and using UKUU I found that the 4.13 kernel suspends without issue but the 4.20 kernel has the issue. I did not yet manually check more versions in between to find the exact one which caused the problem, and I am not sure if this would be helpful or not anyway. I of course also tried the 5.4 mainline, where the issue still exists. How can I go about fixing this issue? Could there be some kernel boot parameters I could try to suspend in a failsafe way? Is there some log somewhere that I could access that would detail why the suspend did not complete properly? 

-Additional Thing-

Using a kernel newer than 4.13 is of course the best practice and best solution, but the real reason that I am trying to solve this issue is because I have lost virtualbox usage during this upgrade, which is critical so some work I am doing. The vboxdrv can no longer run because of some memory offset error, which I believe is caused by the 19.04 debs being compiled against a kernel which is to new compared to 4.13, after some change. So unless I install debs for older ubuntu versions for virtualbox, I don't think I can use virtualbox. This is also not good practice. I guess the only option would be to compile it myself (ung)? Is it supported to use old ubuntu deb versions for this to get it working, or some other way if I can't solve the kernel issue so at least I can keep working?

Thanks and I hope this all made sense.

---

### Post by Impavidus on 2019-10-15
I assume you also tried cycling through the TTYs? ctrl+alt+{F1..F7}

The easy solution would be to use Ubuntu 18.04 LTS, which you already know to work (it comes with kernel 4.15). Is there any particular reason why it no longer does what you want, so you have to upgrade to 19.04?

You could hunt the log files for clues and file a bug report, if you have some useful information.
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by Paul_Jewell on 2019-10-15
Hi Impavidus, 

I try to upgrade relatively often. There is no other real reason. So I guess two things:

-is it safe to downgrade back to 18.04 after doing the upgrade already?
-the real concern is that eventually the LTS will run out, and then I have no reason to believe the bug will be patched in more recent versions. 

Thanks for reading.

---

### Post by mörgæs on 2019-10-15
In your case a clean install of 18.04 sounds like a good option. 

It runs out of support in 2023 and noone has a meaningful guess about what the kernel contains at that time.

In a week or two when 20.04 development begins you could test this one and report the bug, if it's still there. This will give you the best chances for a future smooth ride.

---

### Post by CatKiller on 2019-10-15
> **Paul_Jewell said:**
> is it safe to downgrade back to 18.04 after doing the upgrade already?

You can't downgrade, only fresh install.

In your case, you'll want to install from an 18.04 image rather than one of the point releases like 18.04.3. The point releases come with the Hardware Enablement Stack, which upgrades you to a newer kernel: it was 4.15 at release, then 4.18 some time after 18.10 had been out for a while, and then 5.0 after 19.04 had been out for a while.

If the point release images are all you can find, you'll want to install the **linux-generic** metapackage and then, once you've established that that one works better for you, by booting it from the Grub menu, remove the HWE stuff.

Other than putting you on the HWE stack, the point releases are exactly the same as installing the 18.04 image and then running the normal updates.

---

### Post by Doug S on 2019-10-16
> **Paul_Jewell said:**
> ... which caused a kernel switch to some 5.x.x kernel. I noticed that this caused an issue with the suspend on my laptop. The symptoms of the issue are that the screen goes black and all  hdd activity stops, but the power light stays on/sleep light stays off, and the fan keeps running. There is no way to recover from this situation even with magic sysrq so the power button must be held down. Through some brute force testing and using UKUU I found that the 4.13 kernel suspends without issue but the 4.20 kernel has the issue. I did not yet manually check more versions in between to find the exact one which caused the problem, and I am not sure if this would be helpful or not anyway. Yes it would.

> **Paul_Jewell said:**
> I of course also tried the 5.4 mainline, where the issue still exists. Keep trying the mainline kernels to know if the issue is fixed upstream. There is a lot of suspend related activity on the linux power management group e-mail list.

> **Paul_Jewell said:**
> How can I go about fixing this issue?I can only suggest that you do a kernel bi-section to isolate the exact commit that introduced the issue. (it is a lot of tedious, time consuming work though.)

> **Paul_Jewell said:**
> Could there be some kernel boot parameters I could try to suspend in a failsafe way? Is there some log somewhere that I could access that would detail why the suspend did not complete properly?are there any files under /var/log, such as pm-suspend.log or pm-suspend.log.1 or pm-whatever with useful information?

---

### Post by Paul_Jewell on 2019-11-28
Hello, 

Sorry for taking so long to respond to this, I had to take care of some things before getting back to it. I did some additional testing and found that the issue seemed to be present in version 4.19 and not version 4.18.20, so now I know which code was updated at least. However 4.19 has quite a few patch notes so I am not even sure where I would start testing. I am familiar with python and javascript but C is a little beyond me currently. I would still not be opposed to trying if anyone could link me to a good method to build and install a custom kernel? 

Also in /var/log/ there is nothing that begins with "pm-*', unfortunately...

---

### Post by Doug S on 2019-11-29
O.K., actually i see that, on my test computer, the files in /var/log/pm* are all dated 2016, so guess not used anymore.

You should see information in /var/log/kern.log and /var/log/suspend and dmesg.

Have you tried the final version of [mainline kernel 5.4]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.4/")? Actually, I see a [5.4.1]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.4.1/") there already. There continues to be a lot of suspend related e-mails on the upstream linux-pm e-mail list, so try kernel 5.5-rc1 when it comes out in about 1.5 weeks.

If you want to isolate the exact commit that caused your problems via bisecting the mainline kernel using git, then start with [this]("https://askubuntu.com/questions/718381/how-to-compile-and-install-custom-mainline-kernel/718662#718662"). Suggest you try/verify kernels 4.18 and 4.19-rc1 as your good and bad start points. Bisection will take about 18 kernel compiles, give or take. If you have a limited /boot partition, it will be annoying, as you will have to cleanup as you go. A very very excellent tool for kernel package removal management is [here]("https://bugs.launchpad.net/linux-purge/+bug/1853757").

---

### Post by Paul_Jewell on 2019-11-30
Hey Doug S, appreciate your follow up. 

I saw 5.4.1 was out like literally a day ago. I tried it but unfortunately the problem remains unfixed. 

I have /vag/log/kern.log, /var/log/dmesg, and /var/log/syslog, which all seem to be some of the same information as each other. For whatever reason I do not have a /var/log/suspend*. Also the information does not seem to be very useful in general. MY procedure was to boot into 5.4 kernel, echo a separator line like '--------' to these files, then perform the failed suspend. After this I booted into a live USB and copied the files as is:

In kern.log, after the separator, there is just one line like:
```

Nov 30 16:18:41 luna-T70 kernel: [  151.051846] PM: suspend entry (deep)

```

In syslog:
```

Nov 30 16:18:40 luna-T70 NetworkManager[896]: <info>  [1575148720.1242] manager: sleep: sleep requested (sleeping: no  enabled: yes)
Nov 30 16:18:40 luna-T70 NetworkManager[896]: <info>  [1575148720.1242] device (enp2s0): state change: unavailable -> unmanaged (reason 'sleeping', sys-iface-state: 'managed')
Nov 30 16:18:40 luna-T70 NetworkManager[896]: <info>  [1575148720.1462] device (E0:2C:B2:F1:BF:6B): state change: disconnected -> unmanaged (reason 'sleeping', sys-iface-state: 'managed')
Nov 30 16:18:40 luna-T70 NetworkManager[896]: <info>  [1575148720.1468] device (p2p-dev-wlp3s0): state change: disconnected -> unmanaged (reason 'sleeping', sys-iface-state: 'managed')
Nov 30 16:18:40 luna-T70 NetworkManager[896]: <info>  [1575148720.1471] manager: NetworkManager state is now ASLEEP
Nov 30 16:18:40 luna-T70 nm-applet[3134]: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed
Nov 30 16:18:40 luna-T70 nm-applet[3134]: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed
Nov 30 16:18:40 luna-T70 nm-applet[3134]: Can't set a parent on widget which has a parent
Nov 30 16:18:40 luna-T70 nm-applet[3134]: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed
Nov 30 16:18:40 luna-T70 nm-applet[3134]: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed
Nov 30 16:18:41 luna-T70 systemd[1]: Reached target Sleep.
Nov 30 16:18:41 luna-T70 systemd[1]: Starting Suspend...
Nov 30 16:18:41 luna-T70 compiz[3049]: WARN  2019-11-30 16:18:41 unity.glib.dbus.proxy GLibDBusProxy.cpp:515 Calling method "Inhibit" on object path: "/org/freedesktop/login1" failed: GDBus.Error:org.freedesktop.login1.OperationInProgress: The operation inhibition has been requested for is already running
Nov 30 16:18:41 luna-T70 compiz[3049]: ERROR 2019-11-30 16:18:41 unityfree <unknown>:0 g_variant_get_va: assertion 'value != NULL' failed
Nov 30 16:18:41 luna-T70 compiz[3049]: ERROR 2019-11-30 16:18:41 unitydbus <unknown>:0 g_unix_fd_list_get: assertion 'G_IS_UNIX_FD_LIST (list)' failed
Nov 30 16:18:41 luna-T70 compiz[3049]: WARN  2019-11-30 16:18:41 unity.lockscreen.suspendinhibitormanager SuspendInhibitorManager.cpp:83 Failed to inhbit suspend
Nov 30 16:18:41 luna-T70 systemd-sleep[4182]: /lib/systemd/system-sleep/displaylink.sh: line 7: /tmp/PmMessagesPort_out: No such file or directory
Nov 30 16:18:41 luna-T70 systemd-sleep[4182]: Suspending system...
Nov 30 16:18:41 luna-T70 kernel: [  151.051846] PM: suspend entry (deep)

```

I am not sure if any of these are relevant. To make sure that the displaylink driver was not really involved with this, I have also tried booting into a 19.10 ubuntu USB and suspending there. The same problem persists. I am not sure if any of the other messages there are significant for this issue. 

The 'dmesg' file contained no additional entries after the separator. 

For 'partitioning the kernel' I am not too familiar with it. Is there some way to git checkout all versions between 4.18.20 and 4.19? Is there a logical way to know which git branches are for which release versions? For example, how can I get the source code checked out for the first new commit after the 4.18.20 version? I should be able to then continue to increment from there. I will try to follow your linked instructions to compile one version to start...

thanks!

---

### Post by Doug S on 2019-12-01
> **Paul_Jewell said:**
> For 'partitioning the kernel' I am not too familiar with it. Is there some way to git checkout all versions between 4.18.20 and 4.19?
No, GIT will manage the process of bisection for you, using successive approximation. 

> **Paul_Jewell said:**
>  Is there a logical way to know which git branches are for which release versions? No, the suggestion is to use the mainline branch, which doesn't even know about Ubuntu.

> **Paul_Jewell said:**
>  For example, how can I get the source code checked out for the first new commit after the 4.18.20 version?
I should be able to then continue to increment from there.You really do not want to to that, because there are probably 1000's of commits.
For example, assuming your start points are 4.18 and 4.19-rc1:

```
doug@s15:~/temp-k-git/linux$ git bisect start
doug@s15:~/temp-k-git/linux$ git bisect good v4.18
doug@s15:~/temp-k-git/linux$ git bisect bad v4.19-rc1
Bisecting: 6112 revisions left to test after this (roughly 13 steps)
```


> **Paul_Jewell said:**
> I will try to follow your linked instructions to compile one version to start...Yes, always start with no changes, just to get going.

---

