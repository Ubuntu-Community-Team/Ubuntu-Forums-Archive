---
title: "Can't boot. Help!"
date: 2015-05-24
forum: General Help
---

### Post by rivera151 on 2015-05-24
I'm stumped. I'm getting a message that says: 
error opening /dev/sda no medium found

Obviously, I can't boot. I'm sent to a root shell. I've tried some things from here, but haven't gotten far. Anyone want to walk me through some diagnostics to figure out what the hell is going on?

Of note, I had updated the kernel and needed a reboot, but I tried booting to the previous kernel and couldnt. I also installed lm-sensors and ran a detection script. It disabled some kernel modules, and I'm not sure which ones it disabled.

Thanks in advance.

---

### Post by rivera151 on 2015-05-24
OK. So I had added the line:
```
none /proc/bus/usb usbfs devgid=132,devmode=664 0 0
```

To /etc/fstab so that USB devices would show in my Virtualbox VM, and apparently this was causing the halting in the boot process. I commented out that line and now the system boots. I guess I'll have to find a new way to get my USB working in Virtualbox.

---

### Post by Bashing-om on 2015-05-24
rivera151; Hello;

Great, never the mind for my below as you have found the fault.
Good job !
-----------------------------------
What you have determines a path of diagnoses. We sure could use some additional info:
Is this a UEFI system ?
Is the partitioning GPT ?
What processor Family is the mainboard ?
What graphics chip set is onboard ?

Is this a condition of grub not able to find it's config files, OR the GUI graphics layer not able to start, OR  the graphics driver failing ?

We need to get to a terminal somehow to answer these questions.
So does " I'm sent to a root shell. " mean you have a "grub >" prompt maybe a "grub rescue >" prompt ?
-Maybe we can bot the system from the grub > prompt .

Do you have on hand a liveDVD(USB) ?
Would make things much more convenient to look at the system.

We want to know the results from terminal commands:
```

sudo fdisk -lu ##legacy partitioning scheme##
sudo parted -l ##will also show GPT partitioning##
cat /proc/cpuinfo
lspci -vnn | grep VGA -A 12
sudo lshw -C display

```

to get an idea of where the fault lies .

[INDENT][INDENT][INDENT]it be fault isolation to effect restoration
[/INDENT][/INDENT][/INDENT]

---

### Post by rivera151 on 2015-05-24
Thanks for pitching in!

---

### Post by Bashing-om on 2015-05-24
rivera151; Hey;

No problem; that is what we do here - try and help.

As this matter is concluded:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

and we look forward to the
[INDENT][INDENT][INDENT]next adventure
[/INDENT][/INDENT][/INDENT]

---

