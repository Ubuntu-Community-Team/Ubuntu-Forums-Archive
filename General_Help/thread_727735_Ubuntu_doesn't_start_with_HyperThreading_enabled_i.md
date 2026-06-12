---
title: "Ubuntu doesn't start with HyperThreading enabled in BIOS."
date: 2008-03-18
forum: General Help
---

### Post by BlackDex on 2008-03-18
Hello there,

I have a DELL computer at work, and Ubuntu installed.
During the install (few months ago) HyperThreading whas enabled, and all worked fine.

Now for some reason, sometimes Ubuntu refuses to start.
GRUB loads, and i can select the OS, but then the system restart and everything start again looping.
This also happens with the recovery mode, and several other Linux Live-CD's.

When i disable HyperThreading in the BIOS, everything seems to work as it should, only it is noticeably slower.

I tryed to add "ht=on" to the boot line, but this doesn't work.

It worked fine for a few months, but now it isn't anymore.

Any help/suggestions would be nice.
Thx in advance.

---

### Post by BlackDex on 2008-03-18
**bump** :)

---

### Post by PmDematagoda on 2008-03-18
This is very strange since HT works flawlessly with Ubuntu on my end.

When your system restarts can you remember where exactly the system restarts? Do you get any errors before the system restarts?

---

### Post by BlackDex on 2008-03-18
Well GRUB starts with the selection menu.
I Select the first option, i get the default grub text.
Then the screen goes blank, and reboots.
Normaly it goes blank, and then the Ubuntu logo shows after a second or less.

So i can't see any error.
The same goes for the 'Recovery mode'.
I see all the text passing by, and before i can see what is the last line, it reboots.
Tryed to press pause etc.. didn't helped.

[UPDATE]
Some strange thought of mine.
Could it be the kernel upgrade from 2.6.20 to 2.6.22?
Should i try to install the 2.6.20 again and boot with that to test?

---

### Post by PmDematagoda on 2008-03-18
Do you mean that you upgraded the Ubuntu 7.04 kernel to the Ubuntu 7.10 one? Or was it a complete system upgrade?

---

### Post by BlackDex on 2008-03-18
It was Ubuntu v7.10 to start with.
There was an kernel update a few months ago if im correct.

Now i don't know for sure if it started after that, but i think it is.
I Looked to see if i could install an older kernel version, but this wasn't the case.

---

### Post by BlackDex on 2008-03-19
**bump** :)

---

### Post by BlackDex on 2008-03-25
Well i can't find anything, except that Windows does work with HT on.
Also i tested the CPU (In Windows) with several utilities, nothings seems wrong.
So i don't think it is a hardware error.

I really find this frustrating, that just at once HT and Linux aren't compatible anymore.
There should be a explanation, but i can't find it.

---

### Post by Mogurijin on 2008-03-25
If you got a kernel upgrade, you should be able to select your older kernels through GRUB, unless you specifically edit the menu.lst to not show them.

---

### Post by dcstar on 2008-03-25
> **Mogurijin said:**
> If you got a kernel upgrade, you should be able to select your older kernels through GRUB, unless you specifically edit the menu.lst to not show them.

Installing the **generic** kernel (which supports SMP) will also help, using the ancient** i386** kernel may cause issues.

---

### Post by BlackDex on 2008-03-25
It already has the generic kernel installed (2.6.22-14).
It always was the generic kernel.

I just tryed to do a re-install of the kernel-image etc.., but this doesn't have any effect.

About the kernel update/upgrade, i don't know if it updated, but i can remember something about the kernel-image beining updated from 2.6.22-*. or from 2.6.2x-*, i can't remember.
So it isn't that a big upgrade imo.
Also if there were 2 kernel entries in my grub, i probelby removed the older kernel after a month or so, to save space.

Also normaly you can see other versions using Synaptic, but with the current kernel vesion and reposetories i can't.

---

### Post by BlackDex on 2008-03-25
bumpy

---

### Post by BlackDex on 2008-03-26
Bump again.
I realy can't find why it isn't working anymore.
If someone has some suggestions to try, i would be very very pleased.

---

### Post by BlackDex on 2008-03-27
Well i can only think of one thing to try and fix this.
Is there a way to prevent the pc from rebooting?

So i can see what grub is doing, and then mabye i can see what goes wrong?
If i can prevent the reboot, and enable some debug stuff or something, mabye i can track down the error.

---

### Post by BlackDex on 2008-03-31
Isn't there any way to enable some debug stuff or prevent the reboot? or show some log of the last 2 boot attempts etc..

---

### Post by Lord Illidan on 2008-03-31
What other Linux live cds have you tried?

---

### Post by BlackDex on 2008-03-31
Knoppix, Damn Small Linux, and if i remeber correct, even the SuperGrub disk faild a few times.
And i also tryed something with the name RepairDisk i think.
All didn't start. Knoppix and DSL I am sure of.

---

### Post by Mogurijin on 2008-04-01
If multiple OS's are failing, are you sure it isn't a hardware problem? How old is your BIOS and have you ever flashed it? Sorry if you already answered these questions...

---

### Post by BlackDex on 2008-04-01
I checked for hardware errors with several test utilities, both Windows and Linux.
Now i don't know if that was efficient enough or not, but it all seemed fine.

The BIOS is the latest version available.

Because i still can't rule out the posibility of a hardware error, i want to see if i can get the error message, if there is one, just before the reboot/reset during the boot stage.
Because, it loads GRUB, and then about a second or so it resets/reboots.
Normaly after that second or so, i see the ubuntu logo, and everything starts booting nicely.

If there is a way to check the booting logs or something, i would like to know this, or someway to log it to a specific file by adding options to the GRUB boot parameters or something, that mabye would help, but i don't know how, and i can't find anything, also because i don't exactly know where to look for.

So i hope that there is a way to log it, and it can help me further with my problem.

---

### Post by dcstar on 2008-04-01
> **BlackDex said:**
> I checked for hardware errors with several test utilities, both Windows and Linux.
Now i don't know if that was efficient enough or not, but it all seemed fine.

The BIOS is the latest version available.
........

Do a full BIOS reset to defaults, then boot up to the memtest option and let that run for a decent time.

Then enable the HyperThreading and try it again - it may just be that the latest kernel has a problem with your particular hardware configuration.

You could also try getting the Hardy beta CD and booting off that, it has a much later kernel.

One important thing is to check is the cooling efficiency of your system (if it isn't new), clean out any dust from the fans/heatsinks as these gradually get less efficient and start to cause strange problems.

---

### Post by BlackDex on 2008-04-02
Those tests i already did.
It appeard that nothing went wrong.

But the Hardy CD i didn't think off.
I have it running on my Laptop, and it works very well..
So ill try the Hardy Live CD, and let you all know.

---

### Post by BlackDex on 2008-04-02
Well i tested it with Hardy.
And it works like a charm.

The only strange thing now is.. i forgot to change the HyperThreading option back to Disable, and Gutsy still started :| .
When i first noticed this, it did this a few times, starting normaly or reset.
So i think it is just lucky this time :).

But anyway, i think i just have to wait 22 day's from today and upgrade to Hardy :).

---

### Post by BlackDex on 2008-04-03
It seems i have spoken to soon :(.
This morning i started my pc again, and it started resetting.
I Thought, lets try that Live CD again, and also that rebooted.

I realy want some way to log GRUB and/or the kernel booting process if posible.

---

### Post by BlackDex on 2008-04-16
Well i had some time to do some checking again.
And it seems that the system reboots at the line "setting up standard PCI resources".
That is the last message i can see during the 'Recovery Mode'.

I Hope that someone knows a way to do something about this?
Thx.

UPDATE:
I tryed adding acpi=ht and ht=on to the boot options.
Now Ubuntu starts, but it seems without HyperThreading.
In the 'System Monitor' i only see one CPU, and normaly with HT on i saw 2 CPU's.

I Realy hope someone can help me with this problem :).

---

### Post by BlackDex on 2008-04-16
bumpy (whelp)

---

### Post by torgrot on 2008-04-16
I have a Dell 4550 with the same symptoms.  There are a few command line switches to add to the grub menu.lst.  It would appear that at least on my Dell that they didn't implement the APIC in a standard manner.  When the kernel starts looking for interrupts and hardware associated with it, blooey, reboot.  You can still get the HT, but you will lose some of the power management facilities.  I am at work now and can't remember the switches off the top of my head, I should be able to post them later this evening.

torgrot

---

### Post by BlackDex on 2008-04-17
Ah... that would be greate :).
I Don't need power management.

---

### Post by BlackDex on 2008-04-28
@Torgrot: Could you please send me the paramaters?

---

### Post by BlackDex on 2008-05-06
(very late bump)
Isn't there anyone else with this problem and have fixed it???

---

