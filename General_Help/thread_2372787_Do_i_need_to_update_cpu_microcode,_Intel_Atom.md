---
title: "Do i need to update cpu microcode, Intel Atom"
date: 2017-09-28
forum: General Help
---

### Post by charitosha on 2017-09-28
Greetings,

I have an old netbook HP mini 210 that has Intel Atom N455; OS is Ubuntu 12.04 lts

Plenty of times the cpu is at 100% and i am wondering if by updating the cpu microcode the cpu load decreases.

by the below:
```
haris@Mini-210:~$ dmesg | grep 'microcode'
[ 2056.383615] microcode: CPU0 sig=0x106ca, pf=0x4, revision=0x107
[ 2056.389562] microcode: CPU1 sig=0x106ca, pf=0x4, revision=0x107
[ 2056.401499] microcode: Microcode Update Driver: v2.00 &lt;tigran@aivazian.fsnet.co.uk&gt;, Peter Oruba
```
i conclude that the version i have is v2

By searching intel site i got the following update: Update of 7/7/17 (version: 20170707) from the below link:
>[https://downloadcenter.intel.com/product/42503/Intel-Atom-Processor-N450-512K-Cache-1-66-GHz-](https://downloadcenter.intel.com/product/42503/Intel-Atom-Processor-N450-512K-Cache-1-66-GHz-)
or
([https://downloadcenter.intel.com/download/26925/Linux-Processor-Microcode-Data-File?product=42503](https://downloadcenter.intel.com/download/26925/Linux-Processor-Microcode-Data-File?product=42503))

is it up to date?
how can i tell?

---

### Post by ajgreeny on 2017-09-28
12.04 is now end-of-life and not supported any more so you will get no further updates to any software so we can not help you with that.

For that machine I suggest you try Lubuntu 16.04.

---

### Post by mastablasta on 2017-09-29
it very likley won't reduce system load. different desktop will do that as suggested.

microcode might resolve other issues. you don't have to do the update, but it is beneficial. however using latest Lubuntu for example the code might already be in kernel.

---

### Post by charitosha on 2017-10-02
I had it coming with the update (or more correctly upgrade, however i am not ready to leave this version - 12.04- yet.)
I will install Lubuntu (or LXLE, not sure yet) in the near future, however i still would like to keep the current OS.

I would like to proceed with the update, however since this procedure is unknown to me, i need your advice/support.

I downloaded the microcode folder from the intel site and got the below:

Basically what was downloaded is the following:
    Releasenote //text file
    microcode.dat //able to open with text editor; file has tons of hexadicimals
    intel-ucode folder  //including lots of binary files, able to open with text editor

Releasenote states that it is possible to install the microcode with 2 ways:
    using micricode.dat
    using intel-ucode folder

To update the microcode.dat to the system, one need:
1. Ensure the existence of /dev/cpu/microcode
> 
/dev/cpu/microcode is present. 
file type :character device (inode/chardevice) //unable to open
SIze : 0 bytes //how come?
Volume: unknown

2. Write microcode.dat to the file, e.g.
  dd if=microcode.dat of=/dev/cpu/microcode bs=1M
> since i cannot open /dev/cpu/microcode how should i copy something to it?
via terminal?



To update the intel-ucode package to the system, one need:
1. Ensure the existence of /sys/devices/system/cpu/microcode/reload
> 
i do not have the exact path as described above but as below:
    /sys/devices/system/cpu/cpu0/microcode
    /sys/devices/system/cpu/cpu1/microcode
    in both cases reload file is present however it is of unknown type


2. Copy intel-ucode directory to /lib/firmware, overwrite the files in
/lib/firmware/intel-ucode/
> 
/lib/firmware/intel-ucode not present; only /lib/firmware/intel

3. Write the reload interface to 1 to reload the microcode files, e.g.
  echo 1 > /sys/devices/system/cpu/microcode/reload
> 
how to open the reload file?


By logic i understand that it is possible to solve something with more than one way,however what is the difference between the two?
and basically how should i proceed? what should i look for?

---

### Post by oldos2er on 2017-10-02
Once you upgrade to a supported version, install the package intel-microcode.

---

### Post by mastablasta on 2017-10-03
if microcode is supported by your version it should be in additional drivers section. if it is not, it can mean two things. it is either not supported or your repositories moved to archive.

i think you have two options 
1. you can upgrade to 14.04, then change desktop to Xubuntu (or just XFCE)/Lubuntu (or just LXDE). this is how you would perform the upgrade now: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
2. you can create free disk space and then perform an install, where you select to put the new Lubuntu to that emptied free disk space. will then have dual boot.

---

### Post by charitosha on 2017-10-03
Ok, so indeed i checked in the synaptic package manager i did found some available updates, namely: intel-microcode & microcode.ctl
Regarding CPU usage I have to say that although 100% pikes are present they are not constant as previously (even possible to say that the load usage has actually decreased)
I regularly update via update manager. How come this this has never been updated automatically and it needed to be done manually??
Are there any other "low level" updates that are possible to increase at least a bit the overall performance of a machine?

---

### Post by oldos2er on 2017-10-03
Support for 12.04 ended last April, so no more updates until you install a supported version. While you can do EOL upgrades I'd imagine it would be a pain in the neck.

---

### Post by mastablasta on 2017-10-04
> **charitosha said:**
>  How come this this has never been updated automatically and it needed to be done manually??


because support for the version was dropped. suggest you update to 14.04 LTS which is supported until 2019 and replace the desktop with something lighter.

there should be no good reason not to upgrade this far up ahead. you can also dualboot (keep the old one and install the newer version next to it)

---

