---
title: "kacpid &amp; kacpi_notify"
date: 2007-04-02
forum: General Help
---

### Post by Lockjaw on 2007-04-02
What do kacpid and kacpi_notify do, exactly? I see from searching that they regulate power management, but do I need them on my desktop? Can I shut them off? Also, under "Services settings", I see that there is another power management option, apmd, available -- can I shut that off as well?

Every so often kacpi_notify just eats up cycles, consuming 85% or more of my processor's attention. I noticed from a cursory Google search that Linus was having problems, too. Bleh. If I don't need it, I'd like to ditch it. Any advice would be appreciated! Thank you!

---

### Post by Lockjaw on 2007-04-10
Well, I opened up /boot/grub/menu.lst and added "acpi=off" and "apm=off" to my usual kernel line:

kernel /boot/vmlinuz-2.6.20-14-generic root=UUID=ba4ad4dd-a223-46db-92c8-836b50d0308b ro acpi=off apm=off quiet splash

After rebooting, so far, so good. I'll report back if anything looks or acts bad, but my system doesn't *seem* to be suffering the same way any longer ... kacpid is no longer running. I don't know if this is a bad thing or not, but my fan still seems to operating normally and nothing else is wiggy, so muy bueno as far as it goes.

If anyone has any insights I'd sure be interested ...

Peace all,
G.

:guitar:

---

### Post by dvdkid919 on 2008-01-30
Thanks. That worked perfectly... so far, at least.

---

### Post by velrajan on 2008-02-10
I am also using kubuntu and kacpid process is eating my 75% cpu .I also tried the same thing ( like acpi=off and apm=off ) . It was working and no process are running for kacpid . But when I shutdown the machine , It is not shutowning ...the** OS is searching halt : IDE is not found** . I removed this two parameter from menu list ,then tried the machine was shutdown properly . Can you help on this ? To kill / disabled the kacpid process in kubuntu 
machine ? .

Thanks ,
Velrajan R

---

### Post by manoj_isi on 2008-05-29
Solution to kacpid which works fine for me :
After booting windows when boot linux kacpid starts, to stop it just cut the power supply to your PC including UPS if any , without shutting down (obviously after saving data) when linux desktop is active. yes i am saying that take the power cord out.

Now switch on the power of ur machine & boot linux, kacpid will not appear.(hopefully)

Remember acpi=off will not work on dual core machines , if you use this only one core will get active.

---

### Post by joeyadams on 2008-06-22
To answer your original question, kacpi_notify is a Linux work queue (Google search work queue if you're interested) that the ACPI (Advanced Configuration and Power Interface) driver in the kernel sets up for itself so it can dispatch events to itself.  kacpid is also a work queue, but I didn't look much into what it does.  I think the problem is that some events, when triggered, cause that same event to be triggered again for some reason.  For instance, here is my dmesg when kacpi_notify spins out of control:

```

acpi_ev_notify_dispatch
ACPI: Transitioning device [FAN1] to D3
ACPI: Unable to turn cooling device [f78122a0] 'off'
acpi_ev_notify_dispatch
ACPI: Transitioning device [FAN1] to D3
ACPI: Unable to turn cooling device [f78122a0] 'off'
acpi_ev_notify_dispatch
ACPI: Transitioning device [FAN1] to D3
ACPI: Unable to turn cooling device [f78122a0] 'off'
...

```

I added the acpi_ev_notify_dispatch trace by modifying the kernel source.  That is the function that kacpi_notify is doing.

I personally think that the ACPI driver should detect the number and frequency of kacpi_notify work queue additions and mitigate appropriately.  Sure, other problems with the ACPI driver or BIOS may be revealing the spinning problem, but those bugs don't justify excessive CPU usage that can't be stopped.

---

### Post by velrajan on 2008-06-24
Killing kacpid in kubuntu :

Open : /boot/grub/menu.lst
set this two parameter in :  kcpi=off and apm=on

for example edit menu.lst file : 
kernel /vmlinuz-2.6.22-14-generic root=UUID=80ced2c5-2e16-4b23-be2f-685488794d79 ro acpi=off apm=on quiet splash

Restart the server . 
Now there is no kacpid process are running in your machine .

Thanks
Velrajan R

---

### Post by joeyadams on 2008-06-24
Although that solution is guaranteed to get rid of the kacpi_notify problem, it unfortunately means no ACPI (Advanced Configuration and Power Interface) support at all.  Modern PCs (e.g. newer than 1998 or so) use ACPI instead of APM as their power management system.  If you disable the ACPI subsystem, you'll lose its features as well, such as:

[LIST]
[*]CPU throttling (slowing down the CPU either by you or automatically to save power or cool down the CPU)
[*]Fan control (if it works)
[*]Suspend/Hibernate (if those work)
[/LIST]

My system won't even start with ACPI off because it uses ACPI for a timer source.  With acpi=off, there's no timer, so sleep 1s becomes sleep infinity.

Nevertheless, for a lot of people, I'd imagine setting acpi=off helps more than it hurts.

By the way, could anybody who gets the kacpi_notify issue post their dmesg | tail so as to see if all of them are similar to what I posted above?

Note:  Upon investigation, it seems there's no way to get the fan state (mine would be one of low or high) through the ACPI system on my machine due to a buggy implementation in BIOS.  This could be what's aggravating the bug in the ACPI driver.

---

### Post by DWStrauss on 2008-07-07
I've been getting the same kacpi_notify problem under the same circumstances ever since I upgraded to Ubuntu 8.04 (I was previously running FC3).  The machine is a Gateway 450SX4 notebook, with broken ACPI I believe -- for example, as far as I can tell there is no way for the kernel to turn the fan on or off; it's handled by the BIOS.  Here's my snippet from kern.log (there's 13 Meg or so of this stuff; this snippet is just from when the problem starts):

> Jul  6 13:35:46 mobycow kernel: [  400.983154] ACPI: Transitioning device [FAN0] to D3
Jul  6 13:35:46 mobycow kernel: [  400.983174] ACPI: Transitioning device [FAN0] to D3
Jul  6 13:35:46 mobycow kernel: [  400.983179] ACPI: Unable to turn cooling device [df032600] 'off'
Jul  6 13:35:46 mobycow kernel: [  400.985825] ACPI: Transitioning device [FAN0] to D3
Jul  6 13:35:46 mobycow kernel: [  400.985829] ACPI: Transitioning device [FAN0] to D3
Jul  6 13:35:46 mobycow kernel: [  400.985833] ACPI: Unable to turn cooling device [df032600] 'off'
Jul  6 13:35:46 mobycow kernel: [  400.988822] ACPI: Transitioning device [FAN0] to D3
Jul  6 13:35:46 mobycow kernel: [  400.988826] ACPI: Transitioning device [FAN0] to D3
Jul  6 13:35:46 mobycow kernel: [  400.988830] ACPI: Unable to turn cooling device [df032600] 'off'
Jul  6 13:35:46 mobycow kernel: [  400.998791] ACPI: Transitioning device [FAN0] to D3
Jul  6 13:35:46 mobycow kernel: [  400.998811] ACPI: Transitioning device [FAN0] to D3
Jul  6 13:35:46 mobycow kernel: [  400.998816] ACPI: Unable to turn cooling device [df032600] 'off'
Jul  6 13:35:46 mobycow kernel: [  401.004652] ACPI: Transitioning device [FAN0] to D3
Jul  6 13:35:46 mobycow kernel: [  401.004671] ACPI: Transitioning device [FAN0] to D3
Jul  6 13:35:46 mobycow kernel: [  401.004676] ACPI: Unable to turn cooling device [df032600] 'off'
Jul  6 13:35:46 mobycow kernel: [  401.010825] ACPI: Transitioning device [FAN0] to D3
Jul  6 13:35:46 mobycow kernel: [  401.010843] ACPI: Transitioning device [FAN0] to D3
Jul  6 13:35:46 mobycow kernel: [  401.010848] ACPI: Unable to turn cooling device [df032600] 'off'
Jul  6 13:35:46 mobycow kernel: [  401.013428] ACPI: Transitioning device [FAN0] to D3
Jul  6 13:35:46 mobycow kernel: [  401.013432] ACPI: Transitioning device [FAN0] to D3
Jul  6 13:35:46 mobycow kernel: [  401.013436] ACPI: Unable to turn cooling device [df032600] 'off'
Jul  6 13:35:46 mobycow kernel: [  401.022258] ACPI: Transitioning device [FAN0] to D3
Jul  6 13:35:46 mobycow kernel: [  401.022269] ACPI: Transitioning device [FAN0] to D3
Jul  6 13:35:46 mobycow kernel: [  401.022283] ACPI: Unable to turn cooling device [df032600] 'off'
Jul  6 13:35:46 mobycow kernel: [  401.028782] ACPI: Transitioning device [FAN0] to D3
Jul  6 13:35:46 mobycow kernel: [  401.028792] ACPI: Transitioning device [FAN0] to D3
Jul  6 13:35:46 mobycow kernel: [  401.028806] ACPI: Unable to turn cooling device [df032600] 'off'
Jul  6 13:35:46 mobycow kernel: [  401.034515] ACPI: Transitioning device [FAN0] to D3
Jul  6 13:35:46 mobycow kernel: [  401.034524] ACPI: Transitioning device [FAN0] to D3
Jul  6 13:35:46 mobycow kernel: [  401.034539] ACPI: Unable to turn cooling device [df032600] 'off'
Jul  6 13:35:46 mobycow kernel: [  401.041040] ACPI: Transitioning device [FAN0] to D3


I'm currently running kernel 2.6.24-19-generic

---

