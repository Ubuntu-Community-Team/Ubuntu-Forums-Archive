---
title: "Can't access BIOS options on MSI Wind U100 stuck in Grub Rescue"
date: 2015-02-07
forum: General Help
---

### Post by basementwall on 2015-02-07
**My main problem:** I can't access BIOS boot options on my MSI Wind U100. I get the main BIOS screen, but it's conspicuously missing the "hit del for options" that used to be there--and when I try hitting various F keys and/or del, nothing ever brings up any option. Instead, I just go straight to Grub Rescue, and I can't get out.

**Why I want to get to boot options:** because I have a Windows XP bootable USB that I want to use to get into recovery mode and fix my MBR. But I can't figure out how to get that USB to boot when BIOS won't cooperate and when my only other option is Grub Rescue.
[B]
How I got in this mess: [/B]I was dumb. I had a dual-boot Ubuntu/Windows XP system that I wanted to restore to factory default, with Windows only. So in Windows I deleted the Ubuntu partitions and rebooted without fixing MBR first. Ugh.

To fix the problem, on another computer, I made my XP bootable USB, but as I said, I can't get my Wind to boot into it (or anything else, or give me any BIOS options at all). Any suggestions? (I've read a lot about Grub Rescue, but it seems that it doesn't have USB drivers...?)

---

### Post by basementwall on 2015-02-09
Do you ever get that sinking fear that your problem is so unique that no one knows how to solve it...? *shivers*

---

### Post by Gvarelov on 2015-02-10
While in GRUB rescue:
```
set
```
this will give you a list of variables that drive GRUB during boot process. Of PARTICULAR importance are "prefix" and "root". Make a note of their values. After that:
```
ls
```
this will list all the devices and partitions on your system. Make a note of feedback in the form of "hd0,msdos_something" as these are partitions that you have on the disk, as seen by GRUB. And then, the magic:
```
set root=value_you_noted_when_you_ran_set_command
set prefix=value_you_noted_when_you_ran_set_command
insmod normal
normal
```
after which normal boot should commence and you should be able to boot into whatever default OS is GRUB set to boot. And lucky you if it's Ubuntu. Fire up Terminal and at the prompt issue:
```
sudo grub-install /dev/sda
```
after which you may be warned that you need additional packages, go get them and proceed with install. GRUB 2 has OS prober scritps that should be able to detect your Windows installation and include it in the boot menu.
About BIOS, you may need to upgrade it, but that my friend would be something you won't need if all you wanted is to enable the double- boot.

---

### Post by basementwall on 2015-02-10
> **Gvarelov said:**
> 
```
set root=value_you_noted_when_you_ran_set_command
set prefix=value_you_noted_when_you_ran_set_command
insmod normal
normal
```


Thanks tons for the response. I got as far as "insmod normal," and the response I got was "no such partition." Not sure where to go from there.

If it helps, my response to ls was:
```

(hd0) (hd0,4) (hd0,3) (hd0,2) (hd0,1) (hd1) (hd1,1) (fd0)

```

---

### Post by Gvarelov on 2015-02-13
And what was reported for the value of "prefix" when you issued "set" command? And what was root?
Unusual response for ls command. It'd be something like (hd0,msdos1) or msdos2 etc.

---

### Post by Gvarelov on 2015-02-13
You may have gotten the "no such partition" message since you deleted Ubuntu partition. I overlooked that detail initially.
So... You are essentially shooting for change of order of boot devices and would like to have the USB on top of that order. Have you tried esc key?
And to what OS are you booting after you turn your computer on? Is it bootable at all? Are you thrown to the grub_rescue screen straight away?
Seems like you will have to reinstall Ubuntu again, and then do the revert to factory defaults, this time properly.

---

