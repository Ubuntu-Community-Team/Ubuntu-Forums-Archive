---
title: "Brand New 7.04 install hangs on reboot, but not on shutdown"
date: 2007-07-05
forum: General Help
---

### Post by rscott5 on 2007-07-05
Hi everyone,

I have a brand new machine that I installed Ubuntu 7.04 on. The problem I'm having is that when I hit restart, it acts fine and the Ubuntu splash screen comes up with the orange bars, but then it gets stuck when there is just a sliver of orange left in the progress bar left. The problem first happened immediately after Ubuntu finished installing and it went to restart. Every time it happens, I have to wait a few minutes and then kill the machine by holding in the power button. The strange part is that if I select shutdown instead of restart then it works just fine.

I'm running a brand new Dell XPS 410, Intel Core2 Duo 2.4GHz, 3GB RAM.

Does anyone know what might be causing it to hang like this? Is there a way that I can get some more information (i.e. a logfile or something) to see what is going wrong and be able to give a better description of the problem? Thanks in advance.

---

### Post by kuja on 2007-07-05
You can feel free to check your logs in the /var/log directory. I've had this problem before with a different motherboard. I think it was an ACPI bug or something.

---

### Post by rscott5 on 2007-07-05
Ok I'll check those when I get home from work. Would I be able to see where it is hanging if I go into one of the terminals (Ctrl-Alt-F1) and run shutdown -r now from there?

What do you mean an ACPI bug and how did you go about fixing that? Just curious.

---

### Post by deepclutch on 2007-07-05
u can try disabling acpi if its just hang. there are options u can add to the kernel line in grub(see grub menu below lines when ur system boots) such as "acpi=off" "apm=on"
try.but apm is an older technology.

---

### Post by kuja on 2007-07-05
My fix was to use shutdown instead of reboot (I know, I know, not really a fix. I later changed motherboards and never saw the problem again.) Definitely give that acpi=off option deepclutch mentioned a try, it just might do it (unfortunately though, it could do other things that you dont' want to have happen, but you won't know until you try.)

You probably won't be abel to see anything even if you run the shutdown command from tty1. If it's going to show up anywhere it's probably the /var/log/syslog.

---

### Post by deepclutch on 2007-07-05
there may be some modules fur dell acpi whcih can help may be.else waiting for a newer kernel or compile it enabling custom dell support.
as from google it seems acpi is broken in some dell.
[http://www.google.com/linux?num=50&hl=en&safe=off&q=dell%20acpi&btnG=dell%20acpi](http://www.google.com/linux?num=50&hl=en&safe=off&q=dell%20acpi&btnG=dell%20acpi)

---

### Post by dan828 on 2007-07-05
From the Dell Wiki @  [http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Hang_on_reboot](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Hang_on_reboot)


Description: System may hang while performing a reboot or shutdown
Systems Affected: Dimension E520n, XPS 410n
Impact: System hang
Workaround: Pass the "reboot=b" switch to the kernel at boot time. This workaround is already scripted in the factory preloaded image.
Fix: The kernel that has this fix will be available in a future Ubuntu 7.04 update online.

---

### Post by rscott5 on 2007-07-06
Excellent thanks for your help, I will be sure to give that a shot

---

### Post by nelamvr6 on 2007-07-12
> **dan828 said:**
> From the Dell Wiki @  [http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Hang_on_reboot](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Hang_on_reboot)


Description: System may hang while performing a reboot or shutdown
Systems Affected: Dimension E520n, XPS 410n
Impact: System hang
Workaround: Pass the "reboot=b" switch to the kernel at boot time. This workaround is already scripted in the factory preloaded image.
Fix: The kernel that has this fix will be available in a future Ubuntu 7.04 update online.

How exactly do I do this? Do I edit my menu.lst?

---

### Post by nelamvr6 on 2007-07-13
> **nelamvr6 said:**
> How exactly do I do this? Do I edit my menu.lst?

Never mind, I figured it out.

And it fixed the problem.

Thanks!

---

### Post by dondad on 2007-07-17
> **nelamvr6 said:**
> How exactly do I do this? Do I edit my menu.lst?

I also would like to know exactly how to do this as I have the same problem. I see below that the original poster figured it out, but did not say exactly how. If I edit a file, which file, and where in the file do you put it? I am pretty new to Ubuntu and can generally get around, but am still down the learning curve. Thanks for the help.

---

### Post by bimmerd00d on 2007-10-01
le bump b/c i'm confused on how to do this as well.  I know how to, just not where!

---

### Post by strabes on 2007-10-01
Edit your menu.lst:```
gksudo gedit /boot/grub/menu.lst
```Find the part that looks similar to this:> title		Ubuntu gutsy (development branch), kernel 2.6.22-12-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-12-generic root=UUID=ce85200d-b48c-4be3-a06d-0ffa00c09dfd ro quiet splash
initrd		/boot/initrd.img-2.6.22-12-generic
quiet

Add "reboot=b" to the end of the third line of that section, so the new line would look similar to this:> kernel		/boot/vmlinuz-2.6.22-12-generic root=UUID=ce85200d-b48c-4be3-a06d-0ffa00c09dfd ro quiet splash reboot=b

---

