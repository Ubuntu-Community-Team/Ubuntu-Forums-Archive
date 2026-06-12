---
title: "System started to hang randomly after power outage"
date: 2018-11-26
forum: General Help
---

### Post by anna359 on 2018-11-26
Hi! I've had a power outage recently while I was working in Blender. After reboot I have weird system behavior, it hangs when I work in Blender or scroll sites with Firefox. For instance, I left PC on over night with Blender, Firefox and task manager opened and when I tried to alt+tab to Blender in the morning and I saw that it's hanging. I tried to close Blender window with x button and via task manager (stop process) but it didn't help and caused task manager to hang. I opened terminal, but it also hanged the second it opened. I tried open TTY (ctrl+alt+f1) and it opened and asked me to log in, but after I entered my username - it didn't offered me to enter password, cursor was just blinking below my username. I tried to connect to PC via ssh, but it also stuck at connecting as if PC was unresponsive. I tried `**Alt+SysRq+n**`,`**Alt+SysRq+f**` but the desktop remained stuck. I used `**REISUB**` to soft reboot. Hangs can also occur randomly while i'm working in Blender or other soft. I can't tell if there is any pattern of what causes system hangs. I've already tried boot with Ubuntu liveUSB and used `**fsck -f`** but it found no errors. How can I define what causes hangs? And what logs should I check?

  My specs are: 
     
[LIST]
[*]Xubuntu 18.04 
[*]AMD Ryzen 5 2600X 
[*]AMD Radeon 580rx 
[*]Corsair 2x8 GB RAM 
[*]Nvme SSD Adata 128 GB 
[/LIST]

---

### Post by CatKiller on 2018-11-26
It's possible that the power surge caused damage to the components of your computer. Electricity tends to be rather indiscriminate.

Frazzled RAM would cause the symptoms you've described and is straightforward (but not cheap) to replace if it turns out to be damaged. Other parts get progressively more fiddly, and some of those would also cause that kind of instability if damaged.

I'd start with a memtest, and work from there.

---

### Post by anna359 on 2018-11-26
Thanks for reply! I've already done memtest, 0 erros found. I booted again to remove all non-repository software and now terminal hangs even on simple tasks like apt-get update and apt-get autoremove

---

### Post by 23dornot23d on 2018-11-26
Just some additional information ... you could try .......
Sounds more likely to be a disk drive problem ........

You said you left Blender running - was it doing rendering overnight ?

Any way - I would add smartmontools just to check ......  as when hard drives overheat or get problems then the
system can just hang with no other details .........

**sudo apt install smartmontools**

But smartmontools may highlight something - if not - then that will be memory and hard drive ruled out .........

[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

Best of luck .......

You could install inxi if it will let you ..... maybe that too could give some more details if it will run long
enough for you to get information from it.

[B]sudo apt install inxi

inxi -F[/B]

---

### Post by anna359 on 2018-11-26
No Blender was opened and doing nothing. Anyways, as I have NVME ssd, there is nothing useful smartmontools can tell, SMART says that SELF-TEST is passed, but parameter **Media and data integrity errors **has value **2.** I guess it might be my issue with random hags because some data was damaged?

---

### Post by CatKiller on 2018-11-26
> **anna359 said:**
> Thanks for reply! I've already done memtest, 0 erros found. I booted again to remove all non-repository software and now terminal hangs even on simple tasks like apt-get update and apt-get autoremove

So it's stable enough to run all night doing memtest?

And it's stable long term in a live USB environment?

And the fdisk was successful?

There are still good outcomes and bad outcomes at this point, dependent on further troubleshooting.

> **anna359 said:**
> No Blender was opened and doing nothing.  Anyways, as I have NVME ssd, there is nothing useful smartmontools can  tell, SMART says that SELF-TEST is passed, but parameter **Media and data integrity errors **has value **2.** I guess it might be my issue with random hags because some data was damaged?

> Media and Data Integrity Errors: [FONT=sans-serif]Contains the number of occurrences where the controller detected [/FONT][FONT=sans-serif]an unrecovered data integrity error. Errors such as uncorrectable ECC, CRC checksum failure, or LBA tag [/FONT]mismatch are included in this field.

It might be that those were because of the crash (which is OK) or because of a power surge (which would be bad). That number increasing would definitely be bad.

Currently you're on a scale from damaged data (maybe a full reinstall will be necessary) to damaged components (which would need to be identified and replaced).

---

### Post by 23dornot23d on 2018-11-26
Ok ..... was just a thought ....... hope you sort it out ...... do you run conky - or system monitor ..... maybe when it hangs - you could spot
what process it hangs on .........

---

### Post by anna359 on 2018-11-26
> **CatKiller said:**
> So it's stable enough to run all night doing memtest? 

Yes, test took about 4 hours. 

> And it's stable long term in a live USB environment?
Live usb works fine with my ssd, but I have issues when trying to copy files from my ssd to external drive, copying process just hangs. I can only save small files, pictures and music but not my big projects, that's sad.


> And the fdisk was successful?
I only tried fsck with live USB and it said filesystem of ssd is OK. Is fdisk any different to fsck -f ?



> Currently you're on a scale from damaged data (maybe a full reinstall will be necessary) to damaged components (which would need to be identified and replaced).

System is stable enough when I do little stress on it like listening to music, watching videos. Most tasks harder than that cause system freeze. I was thinking of saving whatever data I can from ssd and do a full secure erase ( overwriting all space on ssd with zeroes). Can this possible force ssd to remap damaged sectors?

---

### Post by CatKiller on 2018-11-26
Sorry, yes, I mistyped. I meant fsck.

It's looking to me like the problems seem to revolve around hard drive access.

Try booting into a live USB and turning swap off. The live environment will use the swap from your installed environment, if it's available, by default.

We want to establish that everything else is still working when the hard drive is completely isolated.

---

### Post by anna359 on 2018-11-26
Thanks, I've booted with liveUSB but Gparted says I have no swap partition. How can I find swap?
[ATTACH=CONFIG]281775[/ATTACH]

---

### Post by CatKiller on 2018-11-26
> **anna359 said:**
> Thanks, I've booted with liveUSB but Gparted says I have no swap partition. How can I find swap?

```
sudo swapoff -a
```

should turn off any swap.

---

### Post by anna359 on 2018-11-26
It seems my swap partition is on encrypted LVM on LUKS. I finally figured it out after doing [B]cryptsetup luksOpen. 
lvdisplay [/B]shows 2 logical volumes: *root* (where my home folder is), and *swap* (which is a swap partition). But I cant disable encrypted swap
Anyways, I did **fsck** on encrypted root LVM and it found no errors. Can't run **fsck** on swap LVM for some reason, I guess because swap is just empty space and doesn't have any filesystem on it.

---

### Post by CatKiller on 2018-11-26
I don't know anything about encrypted swap, or whether it would be used by the live environment or not.

Taking the drive out or disabling it in the BIOS should have the same effect though. We simply want to make sure that the rest of the system is OK when we've excluded that drive.

---

### Post by anna359 on 2018-11-26
Thanks. I'll try to find empty drive and install ubuntu on it tomorrow, and do some stress tests, to check if hardware is OK. Any recommendations on hardware stress tests? I've already done memtest and RAM seems to be OK, but how can I check CPU, GPU under load? The only thing I have in mind is do some Blender rendering

---

### Post by CatKiller on 2018-11-26
[Prime95]("https://www.mersenne.org/download/") is what I use for putting a load on the CPU.

[Unigine Superposition]("https://benchmark.unigine.com/superposition") is what I use for putting a load on the GPU.

If there were particular tasks that were causing it to hang before, other than accessing the hard drive, you'll want to try those too.

Once the hangs are identified as only coming from that drive, we can see if it's possible to restore the functionality of the drive in some way.

---

