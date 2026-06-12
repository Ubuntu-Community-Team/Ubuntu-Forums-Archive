---
title: "live cd works, wubi install failed, but worked on desktop"
date: 2008-05-28
forum: General Help
---

### Post by spankinlisa on 2008-05-28
hi, i booted with the livecd in the tray, and it let me try it out, it worked great. worked faster than vista even off of a cd. so then i tried wubi install on my old desktop, worked fantastic. but i am having no luck with the wubi install on my laptop.

i'm getting stuck at initramfs and getting the error that i am attaching a picture of. also, when i type cat /casper.log it says something like ntfspread something and at the bottom, mount /dev/sda2 on /isodevice success: failed. tells me to run chkdsk /f and reboot to windows twice, i tried that. no luck.

i haven't done anything technical to it since i got it

---

### Post by ago on 2008-05-28
run chkdsk /r within the same partition where you installed wubi

---

### Post by spankinlisa on 2008-05-28
ok, i did that. didn't help me at all. i think i read that the a part of sda refers to disk, and the # refers to partition, is that right? is it possible it is trying to mount the toshiba system volume where they store that special stuff?

also, i see as its trying to boot it says something about not turning fan on, [acpi] something yada yada, and yes i tried booting with the acpi workarounds, i tried all the options that come up under the esc menu. will that mean my fan isn't going to work under ubuntu, if i can ever get it going?

sorry by the way, i am running Toshiba Satellite A205 window$ vi$ta ultimate $p1, centrino core2duo 1.7g, 2gb ram, 200gb hdd (gave 30gb to wubi)

---

### Post by ago on 2008-05-28
Can you post the exact error messages you see in casper.log?

As well as the content of 

cat /proc/partitions
cat /proc/mounts

---

### Post by spankinlisa on 2008-05-28
here you go, the first screen is some error message that is coming up shortly before i get dumped at the busybox prompt, i don't think i mentioned that before

---

### Post by ago on 2008-05-28
Your filesystem needs to be cleaned up. If chkdsk does not cut it, you might have to try with other tools.

---

### Post by spankinlisa on 2008-05-28
ok. should i go ahead and uninstall wubi before i try to clean up my file system

disk defrag says i don't need to defrag, also when it analyzes it says checking disc 1 of 2, then 2 of 2

---

### Post by spankinlisa on 2008-05-30
i uninstalled wubi, ran chkdsk again, rebooted to windows twice, shut down. started up, ran disk defrag, rebooted, shut down. started up, installed wubi, rebooted, same thing.

so i just shrunk my c partition with vista's included tool and installed ubuntu off the livecd to that contiguous space. case closed, thank you for your help ago

---

### Post by abn91c on 2008-05-30
do you have any USB peripherals attached to the computer? if so diconnect them before you try again

---

### Post by spankinlisa on 2008-05-30
just my microsoft mouse. i tried disconnecting it and i still got the same errors. i just gave up on wubi finally and installed ubuntu normally, but i was hoping that i could get wubi to work, so i could uninstall it easy when i inevitably screw up the linux os =)

---

