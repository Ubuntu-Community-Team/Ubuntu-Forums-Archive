---
title: "Help installing ubuntu alongside vista - Boot issues"
date: 2015-07-24
forum: General Help
---

### Post by jordan47 on 2015-07-24
Hello  After searching exhaustively, I decided it would be a much better use of time to ask directly for help. Please excuse me as I am new to this.  I have two hard drives, the original one I would like to use for Vista and Ubuntu 14.10, and the other one I am using for storage of media. I have installed Ubuntu alongside my Vista installation after dusting off an old PC I haven't used in a couple of years. I attempted to get into Ubuntu and Linux back then, and may have left a bit of a mess. I can't seem to boot into Ubuntu! Vista works fine.  I have the boot info script: [http://paste2.org/gmweYeKt](http://paste2.org/gmweYeKt)  Would it be easier to just backup windows onto the storage drive, format the entire OS drive, and then restore my data after reinstalling Vista and Ubuntu? I'd prefer to just sort out this boot issue.  Details would be nice as I would like to understand this! Thank you!

---

### Post by Vladlenin5000 on 2015-07-24
Hi and welcome.

So you installed Ubuntu inside Windows, by using Wubi.
Such method isn't a true dual boot - more like a virtual machine than anything else -, it's been deprecated, sooner than later it'll simply stop working, and it's not supported here.

Please uninstall everything you did, in Windows, then proceed to shrink the partition where Windows is installed (again, from Windows) in order to have enough free and unallocated space for Ubuntu, then boot from the installation media and do a proper dual boot installation. Post back any doubt or question you may have.

---

### Post by jordan47 on 2015-07-24
Thanks for the reply.

Do I uninstall "Ubuntu" from Windows? I had allocated enough space as ext4 and swap at the end of my disk for the new installation, will I need to format these so they are unallocated and do it over again? Or can I still use those partitions?

Edit: Also, will Boot-repair fix this issue for me?

---

### Post by oldfred on 2015-07-24
It does look like you also have a full install in sdb7.
But it tried to install grub to sda which is its normal default. But gpt partitioned drives require a 1 or 2MB unformatted partition with the bios_grub flag for grub to correctly install to sda.

You have sda as a gpt partitioned drive and sdb as a MBR(msdos) partitioned drive. Windows only boots from MBR with BIOS.

Your wubi install is in the sda2 partition. But one of the main reasons wubi has been discontinued is that it does not work with gpt and all new systems with Windows 8 pre-installed use UEFI with gpt partitioning. Or wubi will not work from gpt. You could create a smaller ext4 partition on sda for Ubuntu if you did not want it on the same drive as Windows.

If system is 64 bit, you do need to use 64 bit for everything unless you have less than 2GB of RAM. And many of Boot-Repair's fixes require Interent as it is downloading updates or reinstalling applications to "fix" issues.

---

### Post by jordan47 on 2015-07-24
OK, so I uninstalled "Ubuntu" from Windows, and I don't have the Windows Boot menu at startup anymore (the one that lets you choose Windows or Ubuntu), so I'm hoping I am headed in the right direction. 
I am still unsure of what to do now, however, as you said I do indeed have a full Ubuntu install in sdb7. 
Should I try boot-repair to try and fix this now? I am able to connect to the internet.

Edit: I reinstalled Ubuntu, however, it tried to install the bootloader into sda again, said it was unable to, and after prompting me, I chose to install it to sdb. However, when I restart the system, it still goes directly to Windows. Should I have installed it in the partition called "Windows (Loader)" ? What am I doing wrong?

---

### Post by Vladlenin5000 on 2015-07-24
I'm not sure it'll work but you can try to move the sdb drive as the first boot device thus allowing Grub to boot both Ubuntu and Windows, if everything went according the plan during the installation. 
I'm not sure it can chainload the Windows loader from the other drive. 
As mentioned before, the GTP and MBR mix makes things harder.

And yes, I didn't notice your other installation. I stopped reading your report as soon as I found Wubi...

---

### Post by jordan47 on 2015-07-24
Success! I used the boot-repair and followed the instructions, the bootloader was installed again on sdb. This is what I ended up with: [http://paste2.org/6IgaCH14](http://paste2.org/6IgaCH14)

Thanks for the help guys

---

### Post by oldfred on 2015-07-24
Glad you got it working.

If you ever want grub in MBR of sda, you will need the bios_grub partition. It shows error code 1 and any error code other than 0 means it did not work.

> grub-install: warning: this GPT partition label contains no BIOS Boot Partition; embedding won't be possible.

grub-install: error: embedding is not possible, but this is required for cross-disk install.
grub-install /dev/sda: exit code of grub-install /dev/sda:1



---

