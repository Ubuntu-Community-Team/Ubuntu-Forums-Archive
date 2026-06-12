---
title: "error: attempt to read or write outside of disk 'hd0'"
date: 2020-01-29
forum: General Help
---

### Post by Raymond Day on 2020-01-29
I have a old Toshiba SG30 and got a ribbin cable to plug in a video card on it. So it still has it's top board on it.

With a USB CD I booted a network install Ubuntu. Took about a hour to install and then booted to this grub rescue screen.

[https://photos.app.goo.gl/NzQ6VrfoCtNqFoVw6]("https://photos.app.goo.gl/NzQ6VrfoCtNqFoVw6")

Had to install the 32 bit version.

I can type like ls and other things on the "grub rescue> _"

So what can I type to fix this?

-Raymond Day

---

### Post by Raymond Day on 2020-01-31
Installed this on another system about the same type of mother board. Put it in the SG30 and still get the the grub menu. They were both 32 bit CPU's and via chip set. So I thought it boot in the SG30.

There must be some commands to type in the grub menu to fix this?

-Raymond Day

---

### Post by guiverc on 2020-01-31
I would boot a 'live' system and `fsck` (file system check) your drive. I haven't seen that error in some time, but as far as I recall it was because of a logical error in the fs which results in invalid values being read (thus the attempt to read non-existent blocks on the drive).

---

### Post by Raymond Day on 2020-01-31
It is a brand new WD blue 500GB SATA laptop type drive. It should be good.

Right now it's installing again but this time a manual partition and put a 2 GB swap at the start and used the rest of the drive and set the boot on that. [Seen a YouTube video]("https://youtu.be/SwKfb5k5neA") do that so maybe this will work. Will post back. If it does not I will boot a live CD and run 'fsck'.

Thank you.

-Raymond Day

---

### Post by Raymond Day on 2020-01-31
It still did not boot and I put the drive in another Ubuntu server and ran the fsck and it looks like it come back all clean real fast.

```
Disk /dev/sdn: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xa1f155e8

Device     Boot   Start       End   Sectors   Size Id Type
/dev/sdn1          2048   3905535   3903488   1.9G 82 Linux swap / Solaris
/dev/sdn2  *    3905536 976771071 972865536 463.9G 83 Linux
root@myserver:~# fsck /dev/sdn2
fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
Ubuntu: clean, 136398/30408704 files, 3236511/121608192 blocks
root@myserver:~#

```

What could be wrong?

-Raymond Day

---

### Post by CelticWarrior on 2020-01-31
The [Toshiba Magnia SG30]("https://www.cnet.com/reviews/toshiba-magnia-sg30-review/") is indeed very old and really under-powered by today's standards. Not even the current and still supported Lubuntu releases will run there acceptably. You should be looking at something like [Antix]("https://antixlinux.com/"), a suggestion from a moderator of this forum who's an expert in old hardware.

However, even with Antix there will be dragons!
I suspect that due to it being a very special type of device, that it has the same limitations older desktops had: Boot files must be within the first X GBs (don't really remember) of the beginning of the drive. (Note: Regular desktops and notebooks of the same vintage no longer had this limitation but just go back a few years and you'll find many BIOS with this "problem"). So, here's my suggestion:

Use manual partitioning.
Now, first of all, understand that the location of the swap partition (that you not need at all depending on the release but assume you do need it for safety) has nothing to do with it, and typically it goes at the end of the drive, not at the beginning (again, not the issue here).
Then, the workaround for the problem I'm assuming it's the issue here, is to **create a /boot partition (~500MB) at the beginning of the drive**. Position and size of all the other partitions is not relevant. This assures all the boot files (kernels and stuff) are kept within boundaries whereas with the default root partition including /boot the files can and are scattered all over the drive.

---

### Post by Raymond Day on 2020-02-01
The Antix I downloaded one that would fit on a CD but it would not boot. antiX-19.1-runit-sid_x64-core.iso Well it's a 64 bit one need a 32 bit one. Or maybe a old Linux will work then can upgrade it to the full one?

I got a screen on this SG30 used a ribbon cable to VGA video card. So I can see the screen. F10 press it to boot from the CD.

-Raymond Day

---

### Post by CelticWarrior on 2020-02-02
If you need 32bit you download the "386" ISO.

---

### Post by oldfred on 2020-02-02
CelticWarrior has the correct suggestion.

Very old BIOS have had limits on where boot files had to be on the drive. Over the years that got to be larger and last time it was 128GB. New UEFI based systems do not seem to have any limit, but some of the boot needs to be in the first 2TiB of a drive.

If your original drive was 120GB or less that also confirms the issue.

As an alternative to separate /boot would be a smaller / (root) partition and then large /home partition. That also would keep all the boot files inside the first 128GB of a drive.

---

### Post by Raymond Day on 2020-02-02
I installed the Toshiba Magnia Astaro v8 Install CD it took a long time I thought it was locked up but the CD open and it had a clock on it's LCD display.

Got a ribbon cable to a VGA card. I log in to it with root and no password.

I did a ifconfig and and it's eth0 is set to 192.168.0.1 how do I change it. I set it to what should work with "ifconfig eth0 192.168.86.5 netmask 255.255.255.0"

Can only ping it's IP. I got the Ethernet plug in one of it's 7 ports when I plug it in the 1 port I could get get a ping from it.

How can I set a IP and get it to save it?

-Raymond Day

---

### Post by Raymond Day on 2020-02-03
I had to put a https to port 4444 and that worked and I set the same IP I did with ifconfig and rebooted it and that worked. It now has the IP I set it too.

-Raymond Day

---

### Post by Raymond Day on 2020-12-25
Hi it's been a long time and I got Ubuntu to work on it. But it's only 32 bit so can't update it to Ubuntu 20. Just **Ubuntu Linux 18.04.4** to get it to boot I had start with I think Ubuntu 15 and pick use LVM and then it booted.

With the top off the fans stay slow so don't hear them. I put a pico power supply it it so that don't make heat with the old power supply.

It works good. I am thinking of installing Debian on it. Because it still supports 32 bit.

Was thinking can you just replace the CPU with a 64 bit one. It has some Celeron CPU in it now.

**lshw** CPU part shows this:

```
     *-cpu
          description: CPU
          product: Intel(R) Celeron(TM) CPU                1200MHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.11.4
          slot: Socket-1
          size: 1200MHz
          capacity: 3GHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pse36 mmx fxsr sse cpuid pti
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: Internal Cache
             size: 32KiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: Internal Cache
             size: 256KiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
             configuration: level=2
```

I did not like how the fan's were loud but now with the top off it can not hear them eless get real close to it. That's the only thing that gets a little hot is the CPU so if can replace it with a 64 bit one and under clock it to the same speed the one is now it my be better.

-Raymond Day

---

