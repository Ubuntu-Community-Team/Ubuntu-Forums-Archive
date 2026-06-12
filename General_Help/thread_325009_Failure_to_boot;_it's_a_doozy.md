---
title: "Failure to boot; it's a doozy"
date: 2006-12-24
forum: General Help
---

### Post by touchlikefire on 2006-12-24
I'm currently unable to boot into Ubuntu.

Yesterday I was compiling from source QT and surfing the internet as I waited, when I closed firefox and the system hung and the PC let out a continuous beep.  I wiggled the mouse for a second, tried **CTRL+ALT+Backspace** and **CTRL+ALT+F1**, neither of which worked.  So I hard reset the PC, and during the boot process where the screen displays the Ubuntu logo with progress bar, it hung at one bar.

After some trouble shooting, I've concluded:
[LIST=1]
[*]RAM is not corrupt
[*]HDDs are not corrupt
[*]Partitions are not corrupt
[*]grub is not corrupt
[*]the specific error is "**missing files needed to boot**", which occurs while it is trying to process 'initial scripts'.
[/LIST]

I'm running custom kernel 2.16.19, however 2.16.19 (recovery) didn't work, nor did the previous kernel, 2.16.17-generic or it's recovery option.  All hang at the same place, and when using the recovery mode, I'm able to obtain the aforementioned error, but the boot process will go no further.

I know all HDDs and partitions are intact because I'm able to mount them via the live CD, and everything seems* to be there (*I gave a once over my home folder as well as /usr and the root folder).

I'm still a bit of an amatuer with linux and I have no idea how to proceed.  I know that the OS is 'missing files needed to boot', but since **grub is present** and **menu.lst** is correct, I don't know what those files could be.

Please assist me or point me in the right direction; I miss my Ubuntu and was beginning to enjoy life windows-free.

---

### Post by ~LoKe on 2006-12-24
Perhaps try mounting the partition with a Live CD, doing a chroot and apt-get update && apt-get upgrade?

---

### Post by touchlikefire on 2006-12-24
When I boot in recovery mode it runs through a list of initial hardware checks and then says:
```
 Begin:     Running /scripts/local-premount...
Done.
     Running /scripts/local-bottom...
Done.
     Running /scripts/init-bottom...
Done.
*Reading files needed to boot...
```
And then it hangs.

Thoughts?

---

### Post by kvonb on 2006-12-24
I suggest booting from the Ubuntu CD, then you need to run "fsck" on ALL partitions, sorry I don't know the exact commands and I'm too lazy to look them up for you (it's waay too hot here today, 33degrees, or 90 for those on the old British system).

Regards, KEv :)

---

### Post by touchlikefire on 2006-12-25
kvonb, that last line was pretty funny to me--first, because I thought it *was* in Fahrenheit, and that you were playing some kind of joke, and second, because here in wintry Michigan, US, it *is* 33 degrees F (or 0 C).

Anywho, I'll try your suggestion, as well as Loke's, once I reboot.

Meanwhile, here's s'more info.  Booting regular (no 'recovery') from **GRUB **and then pressing **ALT + F1** (so that I can see what's going on) yields the following:
```
root (hd0,0) {...}
kernel /vmlinuz-2.16.19-custom {...}
[Linux-bzImage, setup=0x1C00, size=0x197971]
initrd /initrd.img-2.16.19 {...}
[Linux-initrd@0x1faad000, 0x542711 bytes]
boot
Uncompressing linux...OK, booting the kernel.
[17.222433] intel_rng: FWH not detected
```
*Note **{...}** designates irrelevant text that has been omitted

---

### Post by kvonb on 2006-12-25
Thankfully the sea breeze came in a few hours ago, those damned desert winds are a killer!

Sorry, I'm not much help, it's nearly time for Christmas dinner :).

The long beep makes me wonder if it is a mainboard problem, maybe go into the BIOS and check your settings, and also look on the mainboard for popped capacitors while you are at it.

Other than that, sorry........food calls :mrgreen:

PS I would still boot from the Ubuntu CD and run fsck on your partitions, just to make sure there are no errors.

---

