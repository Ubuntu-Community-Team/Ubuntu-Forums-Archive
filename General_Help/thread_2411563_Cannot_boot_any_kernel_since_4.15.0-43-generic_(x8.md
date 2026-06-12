---
title: "Cannot boot any kernel since 4.15.0-43-generic (x86_64)"
date: 2019-01-31
forum: General Help
---

### Post by cscj01 on 2019-01-31
There have been two new kernels (4.15.0-44 and 4.15-45) since my last bootable kernel.  With the last two, the system takes a long time (well over a minute) before it puts me into emergency mode.  I have looked at the Journal mentioned in the message given at the point I am put into emergency mode, but I cannot tell what is happening.  Can someone give me some help here to find out why these last two kernels won't boot properly?

I just found this could be an FSTAB issue.  For reference, here is my FSTAB:```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=9ef58828-ffae-4248-ad25-44596e6440d1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=7677ace4-168d-4f94-87fe-d5a5c1372ff5 none            swap    sw              0       0
#Entry for /dev/sdb1
UUID=f3676964-3fac-407e-88f9-9b345f83c687 /media/Data_Three	ext4    errors=remount-ro 0 1
#Entry for /dev/sdc1 :
UUID=b61632e9-7186-4ec9-9e4c-214c01d39a4e /media/Data_Two 	ext4	errors=remount-ro 0 1
#Entry for /dev/sdd1 :
UUID=3573b59f-77c9-460d-9a29-9f6730954125 /media/Data_One	ext4	errors=remount-ro 0 1
#Entry for /dev/sde1 :
UUID=8e82c472-7f56-4183-8156-84d428887b43 /media/Data		ext4	errors=remount-ro 0 1
#Entry for External USB Data Backup Drive
UUID=ac5ef499-beec-42ba-b34b-a5a0d86d49b6 /media/butch/Ubuntu_Data_Back	ext4	errors=remount-ro 0 1
#Entry for NFS Server on drive g on cp2
192.168.1.102:/media/brenda/Ubuntu_Data_Backup /nfs/Ubuntu_Data_Backup nfs _netdev,vers=3 0 0
#Entry for NFS Server shared documents on cp2
192.168.1.102:/media/brenda/cp2_data /nfs/cp2_shared_docs nfs _netdev,vers=3 0 0
```

---

### Post by ajgreeny on 2019-01-31
Why do you think the /etc/fstab file is causing your problem; did you make a manual edit it at the same time as the 4.15.0-44 kernel or the -45 version was added to the system?

Though I am not expert in this situation, I see nothing wrong with the fstab content assuming your UUIDs are all correct.

Does the 4.15.0-43 kernel still boot as you expect it to, ie, much faster than the -44 and -45 versions?

---

### Post by cscj01 on 2019-01-31
> **ajgreeny said:**
> Why do you think the /etc/fstab file is causing your problem; did you make a manual edit it at the same time as the 4.15.0-44 kernel or the -45 version was added to the system?

Though I am not expert in this situation, I see nothing wrong with the fstab content assuming your UUIDs are all correct.

Does the 4.15.0-43 kernel still boot as you expect it to, ie, much faster than the -44 and -45 versions?

I saw a few [posts that indicated the same issue was caused by something in fstab.  I did not, and have not, changed my fstab for a good while (since 16.04). so I do not think that is it.

I can still boot with the same fstab with the 4.15.0-43 kernel.  I looked at the journal with ```
journal -xb
``` after I had rebooted with my old kernel.  I see a number of ACPI errors.  They are here:```
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: No Local Variables are initialized for Method [_GTF]
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: No Arguments are initialized for method [_GTF]
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.SPT4._GTF, AE_NOT_FOUND (20170831/psparse-550)
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: No Local Variables are initialized for Method [_GTF]
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: No Arguments are initialized for method [_GTF]
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.SPT3._GTF, AE_NOT_FOUND (20170831/psparse-550)
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: ata5.00: ATA-9: WDC WD3003FZEX-00Z4SA0, 01.01A01, max UDMA/133
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: ata5.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: ata4.00: ATA-8: WDC WD5000AAKS-00A7B0, 01.03B01, max UDMA/133
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: ata4.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: No Local Variables are initialized for Method [_GTF]
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: No Arguments are initialized for method [_GTF]
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.SPT0._GTF, AE_NOT_FOUND (20170831/psparse-550)
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: No Local Variables are initialized for Method [_GTF]
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: No Arguments are initialized for method [_GTF]
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.SPT4._GTF, AE_NOT_FOUND (20170831/psparse-550)
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: No Local Variables are initialized for Method [_GTF]
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: No Arguments are initialized for method [_GTF]
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.SPT5._GTF, AE_NOT_FOUND (20170831/psparse-550)
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: ata6.00: ATAPI: HL-DT-ST BDDVDRW UH12NS30, 1.02, max UDMA/100
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: No Local Variables are initialized for Method [_GTF]
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: No Arguments are initialized for method [_GTF]
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.SPT2._GTF, AE_NOT_FOUND (20170831/psparse-550)
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: ata3.00: ATAPI: HL-DT-ST BD-RE  WH16NS40, 1.03, max UDMA/133
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: ata5.00: configured for UDMA/133
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: No Local Variables are initialized for Method [_GTF]
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: No Arguments are initialized for method [_GTF]
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.SPT3._GTF, AE_NOT_FOUND (20170831/psparse-550)
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: No Local Variables are initialized for Method [_GTF]
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: No Arguments are initialized for method [_GTF]
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.SPT1._GTF, AE_NOT_FOUND (20170831/psparse-550)
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: ata4.00: configured for UDMA/133
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: ata2.00: ATA-8: WDC WD1501FASS-00W2B0, 05.01D05, max UDMA/133
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: ata2.00: 2930277168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: ata1.00: ATA-10: WDC WD2003FZEX-00SRLA0, 01.01A01, max UDMA/133
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: ata1.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: No Local Variables are initialized for Method [_GTF]
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: No Arguments are initialized for method [_GTF]
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.SPT5._GTF, AE_NOT_FOUND (20170831/psparse-550)
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: ata6.00: configured for UDMA/100
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: No Local Variables are initialized for Method [_GTF]
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: No Arguments are initialized for method [_GTF]
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.SPT2._GTF, AE_NOT_FOUND (20170831/psparse-550)
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: ata3.00: configured for UDMA/133
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: No Local Variables are initialized for Method [_GTF]
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: No Arguments are initialized for method [_GTF]
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.SPT1._GTF, AE_NOT_FOUND (20170831/psparse-550)
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: ata2.00: configured for UDMA/133
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: No Local Variables are initialized for Method [_GTF]
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: No Arguments are initialized for method [_GTF]
Jan 31 13:12:39 Car-Photo-Ubuntu kernel: ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.SPT0._GTF, AE_NOT_FOUND (20170831/psparse-550)

```I don't really know what I'm looking for though... Most of the other messages that are in red are about daemons not being started or are already running.  But, as I say, I'm running blind.

---

### Post by cscj01 on 2019-02-04
It seems no one can offer any suggestions about this issue.  Should I re-post it on another forum?  This is a significant issue because I understand there are significant security issues with the kernel I am running.  I would have thought someone would have some ideas about how to proceed.

---

### Post by cscj01 on 2019-02-04
I booted into emergency and ran the command```
journalctl -xb > journal.txt
```Journal.txt is here[https://spaces.hightail.com/space/AfPlwTvoey/files/fi-feb270f3-2329-486b-9e1f-9bfbd61da86e/fv-d95a9263-caab-49d8-a811-094ee1cdec05/journal.txt]("https://spaces.hightail.com/space/AfPlwTvoey/files/fi-feb270f3-2329-486b-9e1f-9bfbd61da86e/fv-d95a9263-caab-49d8-a811-094ee1cdec05/journal.txt").  I also installed the latest BIOS even though it was Beta.  It changed nothing.  I checked all my disk file systems (SATA and USB). They are fine.  Would someone, anyone, take a look at the Journal.txt file to see if they have any ideas?  What about forum moderators?  Help????

---

### Post by webaake on 2019-02-13
Since you seem to know how to choose kernels at boot, I'd recommend trying an even newer kernel than 4.15.x. I've done this many times when the default Ubuntu kernel seems to create problems.

More here: [https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
And kernels here: [https://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D](https://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D) 

Go for kernel 4.16.1 to start with and see what happens.

---

### Post by cscj01 on 2019-02-13
> **webaake said:**
> Since you seem to know how to choose kernels at boot, I'd recommend trying an even newer kernel than 4.15.x. I've done this many times when the default Ubuntu kernel seems to create problems.

More here: [https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
And kernels here: [https://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D](https://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D) 

Go for kernel 4.16.1 to start with and see what happens.

Thanks for the reply.  Just a question.  If I install 4.16.1 for example (any one of them would do), and it boots properly, will it get updated through the normal update process?

I installed 4.16.1 and it booted to my Desktop.  I did get a number of ACPI errors, but this does not seem to have mattered.  What are ACPI errors about anyway?e

---

### Post by webaake on 2019-02-14
No it won't, since update manager will continue to update the 4.15.x range. But 4.16.x will contain most security updates you'll need, as it is newer than 4.15.x . Ubuntu is always a bit conservative and a small step behind in its own default repos, I think anyway.

A good tool for kernel handling is Ukuu kernel update utility. It lists your current installed kernels and newer ones (older too). Look here: [https://www.omgubuntu.co.uk/2017/02/ukuu-easy-way-to-install-mainline-kernel-ubuntu](https://www.omgubuntu.co.uk/2017/02/ukuu-easy-way-to-install-mainline-kernel-ubuntu)

---

### Post by speartip on 2019-02-14
If you are going to install & boot into another kernel, then I would suggest the latest one in the repos.
```
sudo apt install linux-generic-hwe-18.04
```
Should get you the 4.18.0.15 kernel.

---

### Post by cscj01 on 2019-02-15
> **webaake said:**
> No it won't, since update manager will continue to update the 4.15.x range. But 4.16.x will contain most security updates you'll need, as it is newer than 4.15.x . Ubuntu is always a bit conservative and a small step behind in its own default repos, I think anyway.

A good tool for kernel handling is Ukuu kernel update utility. It lists your current installed kernels and newer ones (older too). Look here: [https://www.omgubuntu.co.uk/2017/02/ukuu-easy-way-to-install-mainline-kernel-ubuntu](https://www.omgubuntu.co.uk/2017/02/ukuu-easy-way-to-install-mainline-kernel-ubuntu)

> **speartip said:**
> If you are going to install & boot into another kernel, then I would suggest the latest one in the repos.
```
sudo apt install linux-generic-hwe-18.04
```
Should get you the 4.18.0.15 kernel.
Thanks to both for the tips.  webaake, I will investigate Ukuu.
speartip, I presume you mean the ones not listed as release candidates when you refer to the latest in the repos.  Does```
sudo apt install linux-generic-hwe-18.04
```avoid the release candidate kernels?

---

### Post by speartip on 2019-02-16
The ones in Ubuntu's official repos are always tried & tested. They are never release candidates.

---

### Post by cscj01 on 2019-02-16
> **speartip said:**
> The ones in Ubuntu's official repos are always tried & tested. They are never release candidates.

Thanks.  One last question before I close this as solved (maybe I should say bypassed): When 4.n (n>15) kernel becomes available through normal channels (assuming one does in 18.04), I assume I will see it in updates as usual.  Is that statement correct?

---

