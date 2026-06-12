---
title: "Reading the contents of a DVD -R etc."
date: 2018-03-13
forum: General Help
---

### Post by anon_private on 2018-03-13
Hello,

I have downloaded the iso file of  kubuntu 16.04.4 and used k3b to burn the image to a DVD -R.

I simulated the burning before the actual burning. Does the simulation use the hard drive since the DVD was empty at this stage. IF the hard drive is used is there some 'cleaning up' that I need to do?

Before I test the OS, is there a method to read the contents of the DVD?

At present, I am using kubuntu ver 14.04.

A couple of other points:

I downloaded the 32 bit iso files because I only have 4 GB of RAM and my system is old.

I was wondering what is the difference between the 32 bit and 64 bit OS's?

Thanks

---

### Post by lisati on 2018-03-13
I'm not familiar with using k3b, but would expect that it would clean up after itself, deleting temporary files, when you close it.  If you are doing a "simulated" burn, nothing should get written to the DVD-R - to view what would have been written to the DVD-R, chances are you would have to locate where any temporary files are written, and take a look there.

As for the difference between 32-bit and 64-bit, there is a thread about it [here]("https://ubuntuforums.org/showthread.php?t=1979347"). It's a few years old, but many of the observations made will still hold true.

---

### Post by anon_private on 2018-03-13
I simulated the burn, then burned the DVD. I was wondering how I could read the  files that have been written to the DVD?

---

### Post by yancek on 2018-03-13
Put the DVD you burned in the drive.  If you are using a newer version of KDE, you should have a device notifier in the taskbar area with a pop-up message with several options including open in File Manager.  Click that to open and see the files.  If this doesn't happen, create a mount point and mount the DVD.

> sudo mkdir /media/user/cdrom
sudo mount -t iso9660 /dev/sr0 /media/user/cdrom  

Replace 'user' with your actual user name.  You should be able to then navigate to the directories/files on the DVD.
Not sure why you want to do this, the directories/files on the DVD will be very different from an installed system.

---

### Post by monkeybrain20122 on 2018-03-13
It seems that you are making life unnecessarily complicated. First of all if you have a usb drive, just make a liveusb, I am sure there is something in kubuntu 14.04 similar to the startup disk creator in Ubuntu (or maybe it is in Kubuntu) Who still burns dvd in 2018? :) 

Secondly if you want to see what is in the iso, just mount it with 
```
sudo mount -o loop  /path/to/iso /mnt
```

Thirdly 4Gs of ram are plenty.

---

### Post by anon_private on 2018-03-14
> **monkeybrain20122 said:**
> It seems that you are making life unnecessarily complicated. First of all if you have a usb drive, just make a liveusb, I am sure there is something in kubuntu 14.04 similar to the startup disk creator in Ubuntu (or maybe it is in Kubuntu) Who still burns dvd in 2018? :) 

Secondly if you want to see what is in the iso, just mount it with 
```
sudo mount -o loop  /path/to/iso /mnt
```

Thirdly 4Gs of ram are plenty.


If I followed your advice I would be making life unnecessarily complicated. I have made a live DVD
Who burns DVD's. Well I do for a start

---

### Post by anon_private on 2018-03-14
> **yancek said:**
> Put the DVD you burned in the drive.  If you are using a newer version of KDE, you should have a device notifier in the taskbar area with a pop-up message with several options including open in File Manager.  Click that to open and see the files.  If this doesn't happen, create a mount point and mount the DVD.

  

Replace 'user' with your actual user name.  You should be able to then navigate to the directories/files on the DVD.
Not sure why you want to do this, the directories/files on the DVD will be very different from an installed system.

That worked. I put the DVD in the drive and File Manager appeared as an option.

I was just curious to see what was on the disk. It helps me learn.

I noticed the md5 file and expected to see the md5 for the iso file burned. But, I was surprised to see lots of md5's

I will now test the live DVD and see how it performs on my older machine. I expect it to be slower than I am used to because it is a live DVD, but I want to ensure that otherwise it works well before considering an install to replace 14.05

Regards

---

### Post by mastablasta on 2018-03-14
the md5 file has all available images. you select the line (hash) from your image and then compare it to the downloaded image. to see if the burn was done succesfully you can test the disk after booting it. it's one of the options in the menu. another way would be to create an ISO image from the newly created DVD drive and then compare it to the md5 hash.

if your CPU is 64 bit then use the 64bit version. although both versions will work in that case, the 32 bit is slowly losing support with applications as well as available OS for 32bit. manufacturing of 32 bit processors for PC mostly ended at the start of this milenium, Except for some Atom CPUs which were made later on in 2010 or so. with 4 GB RAM at disposal you should even start to feel the difference in speed in some cases.

---

### Post by anon_private on 2018-03-14
> **mastablasta said:**
> the md5 file has all available images. you select the line (hash) from your image and then compare it to the downloaded image. to see if the burn was done succesfully you can test the disk after booting it. it's one of the options in the menu. another way would be to create an ISO image from the newly created DVD drive and then compare it to the md5 hash.

if your CPU is 64 bit then use the 64bit version. although both versions will work in that case, the 32 bit is slowly losing support with applications as well as available OS for 32bit. manufacturing of 32 bit processors for PC mostly ended at the start of this milenium, Except for some Atom CPUs which were made later on in 2010 or so. with 4 GB RAM at disposal you should even start to feel the difference in speed in some cases.

I am not sure if my CPU supports 64 bit.

What I do know is that when I bought my pc it had Windows Vista 32 bit installed, and later I installed kubuntu 32 bit. I have kept to the 32 bit tradition because it works.

I will look up the method of testing the DVD disk.

I assume that support for both 32 and 64 bit are as stated on the download site and will be the same for both versions

Regards

---

### Post by anon_private on 2018-03-14
> **mastablasta said:**
> the md5 file has all available images. you select the line (hash) from your image and then compare it to the downloaded image. to see if the burn was done succesfully you can test the disk after booting it. it's one of the options in the menu. another way would be to create an ISO image from the newly created DVD drive and then compare it to the md5 hash.

if your CPU is 64 bit then use the 64bit version. although both versions will work in that case, the 32 bit is slowly losing support with applications as well as available OS for 32bit. manufacturing of 32 bit processors for PC mostly ended at the start of this milenium, Except for some Atom CPUs which were made later on in 2010 or so. with 4 GB RAM at disposal you should even start to feel the difference in speed in some cases.

I have looked up what I think are the characteristics of my CPU

Physical Address Extensions: 32 bit
Instruction Set: 64 bit

It looks like my processor is designed for a 32 bit system, but has some 64 bit capability.

The burned DVD supports 32 bit

Regards

---

### Post by oldos2er on 2018-03-14
Can you please post the output of ```
cat /proc/cpuinfo
```?

---

### Post by anon_private on 2018-03-14
> **oldos2er said:**
> Can you please post the output of ```
cat /proc/cpuinfo
```?

```
andrew@andrew-Dell-DM061:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 6
model name      : Intel(R) Pentium(R) D CPU 2.80GHz
stepping        : 5
microcode       : 0x7
cpu MHz         : 2793.111
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
apicid          : 0
initial apicid  : 0
fdiv_bug        : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 6
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni dtes64 monitor ds_cpl est cid cx16 xtpr pdcm lahf_lm retpoline
bugs            : cpu_meltdown spectre_v1 spectre_v2
bogomips        : 5586.22
clflush size    : 64
cache_alignment : 128
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 6
model name      : Intel(R) Pentium(R) D CPU 2.80GHz
stepping        : 5
microcode       : 0x7
cpu MHz         : 2793.111
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
apicid          : 1
initial apicid  : 1
fdiv_bug        : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 6
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni dtes64 monitor ds_cpl est cid cx16 xtpr pdcm lahf_lm retpoline
bugs            : cpu_meltdown spectre_v1 spectre_v2
bogomips        : 5586.22
clflush size    : 64
cache_alignment : 128
address sizes   : 36 bits physical, 48 bits virtual
power management:

andrew@andrew-Dell-DM061:~$ 

```

I had a look at this folder in Dolphin.

According to Dolphin this file has 0 B, as do many files in this folder
What type of file is it?

---

### Post by anon_private on 2018-03-14
> **yancek said:**
> Put the DVD you burned in the drive.  If you are using a newer version of KDE, you should have a device notifier in the taskbar area with a pop-up message with several options including open in File Manager.  Click that to open and see the files.  If this doesn't happen, create a mount point and mount the DVD.

  

Replace 'user' with your actual user name.  You should be able to then navigate to the directories/files on the DVD.
Not sure why you want to do this, the directories/files on the DVD will be very different from an installed system.

Having used the DVD -R to make a Live kubuntu DVD there is likely to be much free space of the DVD. To my knowledge, k3b did not finalise the disk - I saw no message to this effect. Can I use the remaining space. If so, how?

Regards

---

### Post by mörgæs on 2018-03-14
The **lm** (long mode) flag indicates that you can run a 64 bit operative system. If you use a lot of memory then you might notice a difference but for light usage I expect that the experience will be the same. 

The rumours of my death have been greatly exaggerated, said the 32 bit software package. If you haven't noticed any applications missing... well, then they are all there.

---

### Post by anon_private on 2018-03-14
> **mörgæs said:**
> The **lm** (long mode) flag indicates that you can run a 64 bit operative system. If you use a lot of memory then you might notice a difference but for light usage I expect that the experience will be the same. 

The rumours of my death have been greatly exaggerated, said the 32 bit software package. If you haven't noticed any applications missing... well, then they are all there.

Looking at free -h. I am using a lot of my RAM, and this is typical; however, there is a couple of hundred or so M free.

I have 4 GB of RAM

I wonder which OS is best for me (32 vs 64). I have a llve DVD -R (32 bit)

---

### Post by oldos2er on 2018-03-14
With a 64 bit CPU and 4GB RAM, I would go with a 64 bit OS, but the choice is yours.

---

### Post by monkeybrain20122 on 2018-03-14
> **oldos2er said:**
> With a 64 bit CPU and 4GB RAM, I would go with a 64 bit OS, but the choice is yours.

And I would make a liveusb instead of burning DVDs like it is year 2003. ;)

---

### Post by anon_private on 2018-03-14
> **oldos2er said:**
> With a 64 bit CPU and 4GB RAM, I would go with a 64 bit OS, but the choice is yours.

Why would you choose the 64 bit option?

---

### Post by anon_private on 2018-03-14
> **monkeybrain20122 said:**
> And I would make a liveusb instead of burning DVDs like it is year 2003. ;)

I will make live DVD's

---

### Post by oldos2er on 2018-03-14
> **anon_private said:**
> Why would you choose the 64 bit option?

To make full use of my hardware.

---

### Post by anon_private on 2018-03-14
> **oldos2er said:**
> To make full use of my hardware.

I am looking for reasons to take your advice

---

### Post by anon_private on 2018-03-14
On another point, I have considerable space left on the DVD -R that I used to make the live DVD using k3b. I don't think that k3b finalised the disk, at least, I didn't notice this action. Is it possible for me to utilise this remaining space. If so, how would I do this?

---

### Post by mastablasta on 2018-03-15
if the disk is not finalised, you can use the rest of the disk for data storage.

---

### Post by anon_private on 2018-03-15
I have created a live DVD using k3b and would like to use the remaining space.

I would like to create a folder and store files. How would I do this?

I am assuming that k3b did not finalise the disk. It could have finalised the disk automatically!

Regards.

---

### Post by anon_private on 2018-03-15
> **mörgæs said:**
> The **lm** (long mode) flag indicates that you can run a 64 bit operative system. If you use a lot of memory then you might notice a difference but for light usage I expect that the experience will be the same. 

The rumours of my death have been greatly exaggerated, said the 32 bit software package. If you haven't noticed any applications missing... well, then they are all there.


The lm flag is of importance.

Are there other flags present that I should understand?

Is there an index of the flags that give their meaning and significance?

Regards

---

### Post by mörgæs on 2018-03-15
> **anon_private said:**
> The lm flag is of importance.

Are there other flags present that I should understand?


No. Ubuntu is Linux for human beings and one should be able to just install and run the system without detailed hardware knowledge.


> **anon_private said:**
> 
Is there an index of the flags that give their meaning and significance?


Most likely but I haven't looked for it.


Anyway, the difference between 32 and 64 bit is minimal. If speed is the problem then better to try a lighter distro like Lubuntu.

---

