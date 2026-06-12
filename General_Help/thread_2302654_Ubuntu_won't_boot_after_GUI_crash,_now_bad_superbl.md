---
title: "Ubuntu won't boot after GUI crash, now bad superblocks?"
date: 2015-11-12
forum: General Help
---

### Post by david462 on 2015-11-12
Hello there,

I'm experiencing some serious problems with Ubuntu 14.10 for a while.
Everything was working fine for over a year, after which my system just started crashing out of nowhere, by what was caused by some GUI problem; the taskbar was disappearing, after which every program would freeze.
Rebooting would then give me the error 'ACPI PCC probe failed', sometimes combined with the boot process stopping at the GRUB commandline, or at a prompt which seems to be call 'iniframs'. In the last case I would see some errors like "Target filesystem doesn't have requested /sbin/init. No init found. Try passing init=bootarg".

I reinstalled the whole system using a LiveDisk, after which the problem was gone for a few months, but returned exactly the same last week.
This morning I booted from LiveDisk again, now running BootRepair, which suggested me to share a link whith some logs on this forum.
The logs: [http://paste.ubuntu.com/13237424/](http://paste.ubuntu.com/13237424/)

I really hope there is someone who can help me, since this makes my desktop totally useless, even reinstalling the OS doesn't help.

---

### Post by howefield on 2015-11-12
To clarify, what version did you reinstall with ?

---

### Post by david462 on 2015-11-12
First I was running 15.04, after the reinstall 14.10.

It all started with the freezing GUI, followed by the 'ACPI PCC probe failed' message. After some googling this gave me the idea this could be caused by a conflict with the nVidea-driver (please correct me if I'm wrong). Then, the GRUB error started to show (and also the initramfs error, if I'm right), after which i thought and downgrading to a previous version might be a good idea. Sadly, a few months the exact same problems occurred again.

---

### Post by ajgreeny on 2015-11-12
Interesting as , in spite of a re-install you do not have a grub.cfg file on /dev/sdc, which is essential for grub, which is on sdc to boot the OS, and boot-repair failed to do anything.

Did you check the md5sum of the iso file you used to create the install USB/DVD medium?

I note that you also do not have a disk /dev/sda, which in itself may not be a problem, but seems unexpected when you have started again.

You could also try running a filesystem check on the root partition of the installed OS, as there seem to be some problems there, so boot to live OS again and run command ```
sudo e2fsck /dev/sdc1
``` and see what output you get.

---

### Post by david462 on 2015-11-12
I didn't check the md5um before installing for any of the two installations, but my wild guess is that the ISO was ok, since the OS ran good for a few months before starting to show errors. That also indicates GRUB was running fine, am I right?

The e2fsck command returned this output:
***
ubuntu@ubuntu:~$ sudo e2fsck /dev/sdc1
e2fsck 1.42.9 (4-Feb-2014)
/dev/sdc1: recovering journal
e2fsck: Attempt to read block from filesystem resulted in short read while trying to re-open /dev/sdc1

/dev/sdc1: ********** WARNING: Filesystem still has errors **********
***

---

### Post by ajgreeny on 2015-11-13
Sorry, but I'm no expert in these things so I don't know enough about the fsck output to be able to help with that "short read" error;  I'll do some searching and see if I can help you out a bit more.

---

### Post by david462 on 2015-11-13
I posted the same question on the AskUbuntu StackExchange, a guy over there just suggested me to buy a new disk, this one is most certainly broken: [http://askubuntu.com/questions/697492/ubuntu-wont-boot-after-gui-crash-now-bad-superblocks](http://askubuntu.com/questions/697492/ubuntu-wont-boot-after-gui-crash-now-bad-superblocks)

Guess it might be true, it can explain why the same problems occurred after the reinstall, and a bad disk might also explain the sudden freezing of the system.

I'll wait for other ideas in both threads for the weekend, if no-one can make a miracle happen I'll buy a new disk.

Thanks for your answers!

---

### Post by yancek on 2015-11-13
Frequent freezing of a system regardless of the activity is a classic sign of overheating.  The other problems you mention are not so it may be the drive.
14.10 isn't supported any longer.  I would suggest that you use 14.04 unless something doesn't work for you on that release as it will be supported until April, 2019 and you can directly upgrade to 16.04 in April if you want.

---

