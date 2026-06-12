---
title: "CPU Fans not turning on (CPU heating up)"
date: 2017-06-24
forum: General Help
---

### Post by anspectrum on 2017-06-24
Hello,

My laptop HP Elitebook Folio 9480m with Ubuntu 16.04 (32-bit) is having CPU fan issue.

This laptop is dual boot and on Windows the fan works alright. In Ubuntu the fan does not work at all. I've installed ```
lm-sensors
``` and ```
fancontrol
```. But ```
sensors 
```command does not display fans status. I've also searched around on forums and found somewhat related topics but it didn't help. Please suggest what can be done.
Some output from ```
lshw
``` as below:

[HTML]sudo lshw
XX                        
    description: Notebook
    product: HP EliteBook Folio 9480m (G6A29VC#ABA)
    vendor: Hewlett-Packard
    version: A3009CD10002
    serial: CNU520BD00
    width: 32 bits
    capabilities: smbios-2.7 dmi-2.7
    configuration: boot=normal chassis=notebook family=103C_5336AN G=N sku=G6A29VC#ABA uuid=7F970F6A-BC1A-E711-80BD-20E52F03C0FF
  *-core
       description: Motherboard
       product: 22DA
       vendor: Hewlett-Packard
       physical id: 0
       version: KBC Version 92.17
       serial: PDXZ001XV6P1TR
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: c
          version: M85 Ver. 01.38
          date: 09/26/2016
          size: 64KiB
          capacity: 10176KiB
          capabilities: pci pcmcia upgrade shadowing cdboot bootselect edd int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification netboot uefi
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-4650U CPU @ 1.70GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.5.1
          serial: 0004-0651-0000-0000-0000-0000
          slot: U3E1
          size: 3272MHz
          capacity: 3700MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx pdpe1gb rdtscp constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm epb tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid xsaveopt dtherm ida arat pln pts cpufreq
          configuration: cores=2 enabledcores=2 id=0 threads=4
        *-cache:0
             description: L1 cache
             physical id: 2
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back instruction
             configuration: level=1[/HTML]

And sensors output as:

[HTML]sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +31.0°C  (crit = +128.0°C)
temp2:         +0.0°C  (crit = +128.0°C)
temp3:        +38.0°C  (crit = +128.0°C)
temp4:        +39.0°C  (crit = +128.0°C)
temp5:        +32.0°C  (crit = +128.0°C)
temp6:       +127.0°C  (crit = +128.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +46.0°C  (high = +100.0°C, crit = +100.0°C)
Core 0:         +46.0°C  (high = +100.0°C, crit = +100.0°C)
Core 1:         +44.0°C  (high = +100.0°C, crit = +100.0°C)[/HTML]

---

### Post by gsahli on 2017-06-24
run this - "sudo sensors-detect"
it will tell you which module family you need to use (modprobe or apt install first)

and I'm curious why you've installed 32-bit?

---

### Post by anspectrum on 2017-06-24
Infact, I had migrated from 12.04 to 16.04 and 12.04 was running with 32 bit. I had installed many programs in 12.04 whose settings I wanted to simply be copied to (home folder) 16.04. Installing 64-bit 16.04 had my apprehensions of breaking / messing-up with the programs settings. Secondly, I know for a fact that running 64-bit OS consumes more RAM than 32-bit with very slight performance improvement w.r.t CPU. 

I had run "sensors-detect" earlier but could not determine what to do with it. Since you mentioned, I've run it again and here is the output.
[HTML]sudo sensors-detect --auto
[sudo] password for xxxx: 
# sensors-detect revision 6284 (2015-05-31 14:00:33 +0200)
# System: Hewlett-Packard HP EliteBook Folio 9480m [A3009CD10002] (laptop)
# Board: Hewlett-Packard 22DA
# Kernel: 4.4.0-79-generic i686
# Processor: Intel(R) Core(TM) i7-4650U CPU @ 1.70GHz (6/69/1)

Running in automatic mode, default answers to all questions
are assumed.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): 
Module cpuid loaded successfully.
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
AMD Family 12h and 14h thermal sensors...                   No
AMD Family 15h thermal sensors...                           No
AMD Family 16h thermal sensors...                           No
AMD Family 15h power sensors...                             No
AMD Family 16h power sensors...                             No
Intel digital thermal sensor...                             Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No
Intel 5500/5520/X58 thermal sensor...                       No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): 
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     Yes
Found unknown chip with ID 0x1581
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): 
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): 
Found unknown SMBus adapter 8086:9c22 at 0000:00:1f.3.
Sorry, no supported PCI bus adapters found.

Next adapter: i915 gmbus ssc (i2c-0)
Do you want to scan it? (yes/NO/selectively): 

Next adapter: i915 gmbus vga (i2c-1)
Do you want to scan it? (yes/NO/selectively): 

Next adapter: i915 gmbus panel (i2c-2)
Do you want to scan it? (yes/NO/selectively): 

Next adapter: i915 gmbus dpc (i2c-3)
Do you want to scan it? (yes/NO/selectively): 

Next adapter: i915 gmbus dpb (i2c-4)
Do you want to scan it? (yes/NO/selectively): 

Next adapter: i915 gmbus dpd (i2c-5)
Do you want to scan it? (yes/NO/selectively): 

Next adapter: DPDDC-A (i2c-6)
Do you want to scan it? (yes/NO/selectively): 

Next adapter: DPDDC-B (i2c-7)
Do you want to scan it? (yes/NO/selectively): 

Next adapter: DPDDC-C (i2c-8)
Do you want to scan it? (yes/NO/selectively): 


Now follows a summary of the probes I have just done.

Driver `coretemp':
  * Chip `Intel digital thermal sensor' (confidence: 9)

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
coretemp
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)

Unloading cpuid... OK[/HTML]

---

### Post by gsahli on 2017-06-24
I guess you didn't have it added automatically?
edit /etc/modules by typing:
sudo nano /etc/modules

It's a fairly short file. You will see:
# Chip drivers
coretemp
if you did it automatically - if not, add those two lines and then write out (save) the file (w/Ctrl o) and Exit (Ctrl x).
Restart the computer.

If this doesn't help, maybe you need to install intel-microcode.

---

### Post by HermanAB on 2017-06-25
This is dangerous.  Your CPU can burn out before you found a solution. (Happened to me - $$$).

I would advise that you mount the laptop on top of a 'laptop cooler' if you want to continue experimenting, but I would quit immediately and rather try a different Linux distribution.  You may find that Fedora or Slackware runs without hassles for example.

---

### Post by anspectrum on 2017-06-25
@gsahli, That line was added automatically in /etc/modules as I can see it in there. Moreover, I had already installed intel-microcode but it didn't help either.

@HermanAB, yeah you are right :) , it is dangerous and I am already using laptop cooler. But still while yesterday watching a Youtube video at 360p for just 15 mins had it all heat up and I could notice video getting stuck up because of this. Have not tried Fedora or Slackware yet, its just that I am too comfortable with Ubuntu and too cautious to try any other distribution.

Any further suggestions please.

---

### Post by gsahli on 2017-06-25
I would be looking at - BIOS settings, adding acpi(d?), thermald, SMSC module (I didn't find it).

---

### Post by anspectrum on 2017-06-25
BIOS settings have no explicit option to control fan. Moreover based on some forums, I did install acpi and the proposed tweaking but could not get the fan running. Could you be more specific about those programs?

---

### Post by HermanAB on 2017-06-26
Otherwise, open the laptop and wire the fan to the power so it always runs.

BTW, it sounds like your laptop cooler is not sufficient, so you really are in danger of burning out something - possibly the GPU.  If I were you, I would call it quits and try another distro, unless of course you have money to burn - in which case, why not buy another laptop right now and get something that is known to work with Ubuntu?

---

### Post by gsahli on 2017-06-26
I meant I'd be investigating and experimenting with those, just like you did with fancontrol. I don't have any experience with those.

About BIOS - I was hoping that this option might be in there:
[https://www.intel.com/content/www/us/en/support/boards-and-kits/000005946.html](https://www.intel.com/content/www/us/en/support/boards-and-kits/000005946.html)

Does your laptop use UEFI? Then ubuntu should be installed in UEFI mode:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by anspectrum on 2017-06-27
I was hoping that something like [https://ubuntuforums.org/showthread.php?t=2217658](https://ubuntuforums.org/showthread.php?t=2217658) can be done to turn on the fans. This post is for 14.04 and the helper did a wonderful job in getting the problem resolved. However, he specifically mentioned that this procedure could break things. If you skim through the posts you will see that certain values and scripts were specifically written for the OP, hence my apprehensions for not giving it a try.

I am not skilled in Operating systems and their interaction with hardware and firmware (though I try) but I've faith in these forums and community as a whole as it has always been there to support and share knowledge. Can someone have a look at that and may be point out the core method about resolving this issue.

Thanks.

---

### Post by gsahli on 2017-06-27
I should have asked you directly - did you install with the UEFI install process?

---

### Post by anspectrum on 2017-06-27
In BIOS setup the boot mode that I have selected is UEFI. The other option is legacy but it is not selected. After you had suggested about UEFI, I had done some reading about it that how to check if OS is UEFI installed or not. Right now I am on a different machine and will be able to check it in a couple of hours.

I was thinking about booting the system with 64-bit Ubuntu 16.04 and see if jacking up the CPU usage triggers the fans or not. If it does I would install 64 bit. But I have my doubts that it would. What do you think that 32 bit and 64 bit OS architecture can impact hardware components control ?

---

### Post by anspectrum on 2017-06-27
Alright, I've checked it.

1) My Ubuntu installation is not UEFI. Although in BIOS menu it shows as UEFI boot.

2) I booted laptop with 64 bit (16.04) and stressed the CPU but fan did not turn on.

---

### Post by gsahli on 2017-06-27
If I were doing this, I'd use the newest 64-bit 16.04.2 and use the instructions for UEFI install. There are major changes from 16.04 to 16.04.2.
[https://help.ubuntu.com/community/Installation/FromUSBStick#Creating_an_EFI-only_image](https://help.ubuntu.com/community/Installation/FromUSBStick#Creating_an_EFI-only_image)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

But, no guarantees...

---

### Post by anspectrum on 2017-06-28
I am already running 16.04.2. As for UEFI, I am still searching how to go about it and whether it is worth the effort. Because some posts indicate of reformatting HDD which I am not liking owing to the data that I have. Moving it and then bringing it back is a pain. And secondly, as you indicated no guarantees. I was thinking that if 64-bit live version had the fan running I would have gone through the process of re-installation but now I am not that eager.

---

### Post by anspectrum on 2017-06-29
Ok. I've got the fan working.

First of all thank you for this post [https://ubuntuforums.org/showthread.php?t=2217658](https://ubuntuforums.org/showthread.php?t=2217658) and all the help by Chris-c.

As I was trying to follow this post and install acpi-call 0.0.1 and getting errors while trying to build, I thought about installing acpi-call-dkms from Ubuntu repositories. After getting it installed, I heard the sweet sound of fan. The fan seems to be spinning all the time at low speed but under load really kicks off.

So, all is well and I can bear with low constant spinning instead of not spinning at all. Hope this would be helpful for others.

---

### Post by gsahli on 2017-06-29
Great. Good work.

---

### Post by anspectrum on 2017-06-30
OMG. May be I spoke too soon. After couple of reboots the CPU fan has died again. I had not done anything special except acpi-call-dkms installation when the fan was turned on but now though everything is same. its just not spinning. Fan does work in Windows using TPFanControl utility, so we know it is working.

This is becoming really annoying. Please suggest.

---

### Post by gsahli on 2017-06-30
first thing - run "lsmod" to see if acpi-call-dkms is loaded.

---

### Post by anspectrum on 2017-06-30
yes it does. I have made sure of that by making entry in /etc/modules. Even if it does not we can always add that at run time using modprobe.

I can not think of any reason why this would happen. I have checked bash_history and there is nothing that I could miss.

---

### Post by anspectrum on 2017-06-30
yes it does. I have made sure of that by making entry in /etc/modules. Even if it does not we can always add that at run time using modprobe.

I can not think of any reason why this would happen. I have checked bash_history and there is nothing that I could miss.

---

### Post by gsahli on 2017-06-30
Time to try fancontrol again.
I'd also be using acpitail to monitor what's being registered. Confirming that there is a signal which could be used for fan control.

---

### Post by anspectrum on 2017-07-01
Strange it may sound but world is full of weird things. My CPU fan has started working again. I don't know how or why but here is what I did / found:

Last night I was installing latest kernels as I had read on some Arch Linux forums and on Launchpad to install latest kernels. After each installation I restarted the laptop and the fan kept dead. So I ended up removing all the kernels and left with [HTML]Linux OS 4.4.0-79-generic[/HTML] which I suppose is the default for this distro. Anyhow, I shutdown my laptop and today when I powered it up I could hear the sweet sound of the fan, cranking up as well under CPU load :D. I immediately "Restarted" to boot into Windows and then "Restarted" again to Ubuntu. And the fan died. So instead of restarting I "Shutdown" the laptop and turned it on again using Power button and CPU fan turned on again. I repeated it couple of times to ensure that shutting down the laptop and then turning it back on fixes the fan issue. Weird, isn't it? On Windows side I've again custom CPU fan control utility "TPFanControl" which I suspect somehow messes up to stop CPU fan from turning on upon restart, how? I've no clue.

But, I am a happy Ubuntu user now, yet again :)

---

### Post by gsahli on 2017-07-01
good news

---

