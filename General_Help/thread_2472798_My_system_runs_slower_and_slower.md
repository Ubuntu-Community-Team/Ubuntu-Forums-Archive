---
title: "My system runs slower and slower"
date: 2022-03-13
forum: General Help
---

### Post by wyattwhiteeagle on 2022-03-13
What is a sure-fire way to see what all exactly is causing my system to run slower and slower?

---

### Post by jimmy-frydkaer on 2022-03-13
What are the specs of the computer? what version of Ubuntu are you running

---

### Post by wyattwhiteeagle on 2022-03-13
> **jimmy-frydkaer said:**
> What are the specs of the computer? what version of Ubuntu are you running

Dell Latitude E5400
1TB Toshiba Internal HDD
4GB RAM
2GHz Intel Dual-core CPU
Intel Mobile 4 Series Chipset Integrated Graphics Controller
Intel WiFi Link 5100
Ubuntu 20.04 Focal Fossa (Minimal Install)

I use Stacer, Bleachbit and a basic package-management cleanup bash script.
Yet my system is just getting slower by the day.


```
wyatt-latitude-e5400
    description: Portable Computer
    product: Latitude E5400
    vendor: Dell Inc.
    serial: CKNVVK1
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 smp vsyscall32
    configuration: boot=normal chassis=portable uuid=44454C4C-4B00-104E-8056-C3C04F564B31
  *-core
       description: Motherboard
       product: 0D695C
       vendor: Dell Inc.
       physical id: 0
       serial: .CKNVVK1.CN7016698EG0KO.
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A18
          date: 07/24/2012
          size: 64KiB
          capacity: 1600KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          slot: Microprocessor
          size: 1787MHz
          capacity: 2001MHz
          width: 64 bits
          clock: 200MHz
          capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl cpuid aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm pti tpr_shadow vnmi flexpriority dtherm ida cpufreq
          configuration: cores=2 enabledcores=2 threads=2
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 128KiB
             capacity: 128KiB
             capabilities: internal write-back data
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 2MiB
             capacity: 2MiB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
             configuration: level=2
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: M4 70T5663QZ3-CF7
             vendor: Samsung
             physical id: 0
             serial: 97AD30D7
             slot: DIMM_A
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: M4 70T5663QZ3-CF7
             vendor: Samsung
             physical id: 1
             serial: 97AD30C8
             slot: DIMM_B
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)

        *-disk
             description: ATA Disk
             product: TOSHIBA MQ01ABD1
             vendor: Toshiba
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 2J
             serial: 16FYTXN9T
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=d2e747a6

           *-network
                description: Wireless interface
                product: WiFi Link 5100
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: wlp12s0
                version: 00
                serial: 00:22:fb:9f:2e:6a
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=5.4.0-104-generic firmware=8.83.5.1 build 33692 ip=192.168.254.75 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:25 memory:f69fe000-f69fffff

        *-display:0
             description: VGA compatible controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:f6c00000-f6ffffff memory:e0000000-efffffff ioport:efe8(size=8) memory:c0000-dffff

```

---

### Post by ajgreeny on 2022-03-13
I think the gnome desktop of Ubuntu that I assume the Ubuntu-Minimal uses is probably too resource hungry for that machine; with only a dual core and 4G ram you will probably not do as well as some of the lighter Ubuntu family of OSs such as Xubuntu, Kubuntu, Ubuntu-Mate, etc.

Xubuntu with Xfce4 is my system of choice but you can look at them all as live systems and see what runs best and you think suits you best.
See [https://ubuntuforums.org/showthread.php?t=2415676](https://ubuntuforums.org/showthread.php?t=2415676) for a great thread a out the choice available.  They all work similarly with regard to package management and general use; it's only the look of them and the DE that differs.

---

### Post by HermanAB on 2022-03-13
Don’t guess and poke in the dark.  Run “top”, “htop” or “ntop” to see what is going on. You can also use “dig” to see whether your DNS is slow. Use google to find out what these commands are and how to use them.

---

### Post by Claus7 on 2022-03-13
Hello,

or use system monitor (under command line: gnome-system-monitor).

Regards!

---

### Post by wyattwhiteeagle on 2022-03-14
I'm now on Lubuntu

I haven't noticed it getting slower...but when Ubuntu was getting slower...it was more like a 4 to 7 days in.

Let's give it a little more time.

---

### Post by wyattwhiteeagle on 2022-03-15
> **HermanAB said:**
> Don’t guess and poke in the dark.  Run “top”, “htop” or “ntop” to see what is going on. You can also use “dig” to see whether your DNS is slow. Use google to find out what these commands are and how to use them.

ok...htop is for tasks, processes and resources...is there something better than just sitting here watching hoping to catch something in time?
the "dig" command seems just for gathering DNS information...not changing settings such as setting up a secure DNS
The info dig gave...I'm not sure what I'm looking for to see if DNS is slow.
Maybe someone who knows can help...

Google

```
wyatt@wyatt-latitudee5400:~$ dig google.com


; <<>> DiG 9.16.1-Ubuntu <<>> google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 17560
;; flags: qr rd ra; QUERY: 1, ANSWER: 6, AUTHORITY: 0, ADDITIONAL: 1


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;google.com.                    IN      A


;; ANSWER SECTION:
google.com.             266     IN      A       142.250.105.102
google.com.             266     IN      A       142.250.105.101
google.com.             266     IN      A       142.250.105.139
google.com.             266     IN      A       142.250.105.138
google.com.             266     IN      A       142.250.105.113
google.com.             266     IN      A       142.250.105.100


;; Query time: 20 msec
;; SERVER: 127.0.0.53#53(127.0.0.53)
;; WHEN: Tue Mar 15 03:41:54 EDT 2022
;; MSG SIZE  rcvd: 135


wyatt@wyatt-latitudee5400:~$
```

My router/modem
```
wyatt@wyatt-latitudee5400:~$ dig -x 192.168.254.254


; <<>> DiG 9.16.1-Ubuntu <<>> -x 192.168.254.254
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 64643
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;254.254.168.192.in-addr.arpa.  IN      PTR


;; ANSWER SECTION:
254.254.168.192.in-addr.arpa. 0 IN      PTR     _gateway.


;; Query time: 28 msec
;; SERVER: 127.0.0.53#53(127.0.0.53)
;; WHEN: Tue Mar 15 04:05:42 EDT 2022
;; MSG SIZE  rcvd: 79


wyatt@wyatt-latitudee5400:~$ 

```


My system
```
wyatt@wyatt-latitudee5400:~$ dig -x 192.168.254.75


; <<>> DiG 9.16.1-Ubuntu <<>> -x 192.168.254.75
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 8300
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 1


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;75.254.168.192.in-addr.arpa.   IN      PTR


;; ANSWER SECTION:
75.254.168.192.in-addr.arpa. 0  IN      PTR     wyatt-latitudee5400.
75.254.168.192.in-addr.arpa. 0  IN      PTR     wyatt-latitudee5400.local.


;; Query time: 32 msec
;; SERVER: 127.0.0.53#53(127.0.0.53)
;; WHEN: Tue Mar 15 03:50:10 EDT 2022
;; MSG SIZE  rcvd: 128


wyatt@wyatt-latitudee5400:~$ 
```



My system is starting to run slow again...
Here's what's going on...

I have a disk indicator light...it seems to almost constantly be running.
When I open something...doesn't matter what it is...featherpad, even the QTerminal...
it takes longer and longer for things to open.

Stacer and bleachbit seem to help less and less.

---

### Post by guiverc on 2022-03-15
> **wyattwhiteeagle said:**
> 
I have a disk indicator light...it seems to almost constantly be running.
When I open something...doesn't matter what it is...featherpad, even the QTerminal...
it takes longer and longer for things to open.

Stacer and bleachbit seem to help less and less.

Ensure you have an adequate *swap* setup for your system.

With Lubuntu it's varies on release what the defaults are, but I *rarely* use the defaults as my devices are all old & thus low-powered (*thus I really benefit from swap*).

Useful links:

 - [https://discourse.lubuntu.me/t/how-to-create-a-swapfile-in-lubuntu-20-04-20-10/1959](https://discourse.lubuntu.me/t/how-to-create-a-swapfile-in-lubuntu-20-04-20-10/1959)

- [https://discourse.lubuntu.me/t/swap-and-lubuntu-21-04-hirsute-and-up/2591](https://discourse.lubuntu.me/t/swap-and-lubuntu-21-04-hirsute-and-up/2591)

The second was written as a FAQ, the first as a *howto* for 20.04 & 20.10

**Swap really matters.** I needed RAM to *assess *a family members box so stole 4GB of RAM from a box (it had 8GB) I use primarily in QA-testing & a couple of hours in the afternoon; as it still had 4GB I never expected to notice the difference - but i SURE DID !!!   A quick command (or two) & I had a *swapfile* setup & it was back to behaving like normal (as if it had 8GB again).

Recent releases of Lubuntu default to swap being created; however it's still too small for my old boxes; thus I increase it.  On most my installs though; I don't do anything as Lubuntu will happily use whatever swap was pre-setup.


The tool I'd explore your system with is `htop` which was already suggested; it's pre-installed on a Lubuntu system too.

---

### Post by wyattwhiteeagle on 2022-03-15
Update:
I created and ran a bash script using the commands at Guiverc's first link...

Um...is the screen supposed to go black running all kinds of disk I/O errors?

> **guiverc said:**
> Ensure you have an adequate *swap* setup for your system.

With Lubuntu it's varies on release what the defaults are, but I *rarely* use the defaults as my devices are all old & thus low-powered (*thus I really benefit from swap*).

Useful links:

 - [https://discourse.lubuntu.me/t/how-to-create-a-swapfile-in-lubuntu-20-04-20-10/1959](https://discourse.lubuntu.me/t/how-to-create-a-swapfile-in-lubuntu-20-04-20-10/1959)

- [https://discourse.lubuntu.me/t/swap-and-lubuntu-21-04-hirsute-and-up/2591](https://discourse.lubuntu.me/t/swap-and-lubuntu-21-04-hirsute-and-up/2591)

The second was written as a FAQ, the first as a *howto* for 20.04 & 20.10

**Swap really matters.** I needed RAM to *assess *a family members box so stole 4GB of RAM from a box (it had 8GB) I use primarily in QA-testing & a couple of hours in the afternoon; as it still had 4GB I never expected to notice the difference - but i SURE DID !!!   A quick command (or two) & I had a *swapfile* setup & it was back to behaving like normal (as if it had 8GB again).

Recent releases of Lubuntu default to swap being created; however it's still too small for my old boxes; thus I increase it.  On most my installs though; I don't do anything as Lubuntu will happily use whatever swap was pre-setup.


The tool I'd explore your system with is `htop` which was already suggested; it's pre-installed on a Lubuntu system too.

When I installed Lubuntu, I manually partitioned the HDD.
I set up a 6GB linux-swap partition
I'm gonna delete it and create the 8gb swap
```
wyatt@wyatt-latitudee5400:~$ swapon --show
NAME      TYPE      SIZE USED PRIO
/dev/sda3 partition   6G   0B   -2
wyatt@wyatt-latitudee5400:~$ 

```

---

### Post by wyattwhiteeagle on 2022-03-16
> **HermanAB said:**
> ...Run...&#8220;htop&#8221;...to see what is going on...


> **wyattwhiteeagle said:**
> ok...htop is for tasks, processes and resources...is there something better than just sitting here watching hoping to catch something in time?


> **guiverc said:**
> ...The tool I'd explore your system with is `htop` which was already suggested; it's pre-installed on a Lubuntu system too.


Alright...
If sitting here watching htop is the ONLY way...
Can someone please at least let me know SOMEHOW what I should be paying attention to and what I'm trying to catch?

---

### Post by guiverc on 2022-03-16
Search online with how to use `htop`.

Myself; probably my most used key is F6, ie. *to alter sort criteria*; F5 can be handy too.. but I'm mostly using it to get a '*feel*' for what my system is doing... once I've got an idea as to the issue, I may then switch tools (`iotop`, `iftop` etc); though that's usually in a different terminal as `htop` is rather light so (it's just a *fancy *color version of the original `top` from 1984)

Sure other tools have a prettier displays (*I just noticed have a window open with `bpytop` yet can't recall why it was even opened*) but I like `htop` as it's light & doesn't impact the machine like `bpytop` will (*I tend to think of `bpytop` as mostly eye-candy but it shows more historical data than top/htop*)

---

### Post by VMC on 2022-03-16
```
[FONT=monospace][COLOR=#000000]systemd-analyze blame
``` Will give you boot up timing results[/COLOR]
[/FONT]

---

### Post by TheFu on 2022-03-16
When a system gets slow, that's usually cause by failing hardware.  Errors and warnings will be in the log files on the system.  Check those. Google "ubuntu log files" for where to look for what and how to search, since there will be thousands of lines of information, not errors, in the logs too.

A disk that is failing would certainly show by slowing down.  Same for a bad cable.
Slow DNS can make a system a little slow to, as performing DNS lookups happens all the time for some commands that aren't intuitively obvious about using DNS.  For example, sudo.  sudo configs can be setup to specify hostnames where different commands are allowed, so running sudo will require quick DNS lookups. If the DNS is slow or not working correctly a 30 second timeout might have to happen BEFORE the command is run. That will seem slow.

top and htop are for seeing which processes are using RAM and CPU.  There are monitoring tools which can be setup, but I don't think you'd want to do that based on prior threads.  Too complicated.

The journalctl command has lots of options for searching through all the different system logs.  I have about 5 commands that I use with it, but I'm old and typically use egrep on the logs in /var/log/ for any issues.  Last night, one of my systems locked up.  I ran
```
$ journalctl -b -1 -p err
```
to see the errors from the boot prior to the current boot. It showed that the computer hit a known kernel bug at 02:16:23am. It was a buffer overflow. 
```
invalid opcode: 0000 [#2] SMP NOPTI
```
and had an issue with memory paging (i.e. swapping). There was a stack trace in the log.  I've seen this before - perhaps 4 months ago.
When I got up this morning, the system was locked up. Mouse was working. Screen was working, but the keyboard wasn't and it wasn't answering any pings from other systems on the LAN.  BRS (big red switch) time.

---

### Post by Claus7 on 2022-03-16
Hello,

> **wyattwhiteeagle said:**
> Alright...
If sitting here watching htop is the ONLY way...
Can someone please at least let me know SOMEHOW what I should be paying attention to and what I'm trying to catch?

so, after all responses, in order to recup, since I understand that it is really annoying the fact that your system slows down, and the fact that many different factors might affect this performance:
1) either it is a failing hardware
2) either something causes your system, even from the boot stage, to have performance issues
3) either something runs in parallel and causes the system to slow down: I prefer gnome-system-monitor, since it graphically shows both the swap and actual memory along with cpu performance. htop and the like are more command line tools: it is a matter of taste. In your case I would try to see if these values change at the first stages of booting and some time later, when I actually observe problems in my performance.
4) I would add one more: have you checked how much disk space you have available (free)? I recently got rid of many gb and saw that my system rejuvenated! To give you an idea it was an hdd ~80% and reduced it to ~30%.

Hope that all these will guide you in the right direction.

Regards!

---

### Post by wyattwhiteeagle on 2022-03-16
Looks like I have my work cut out for me.

In htop, is it normal to see multiple processes of the same files with each having a different PID number?

I'm seeing 19 different instances for google and that with only 1 tab showing only the default page (google search).

---

### Post by dragonfly41 on 2022-03-16
In Stacer (which you write you have installed) open Processes panel, search chrome in search field, and you see one process per tab in Chrome browser.

---

### Post by TheFu on 2022-03-16
> **wyattwhiteeagle said:**
> Looks like I have my work cut out for me.

In htop, is it normal to see multiple processes of the same files with each having a different PID number?

I'm seeing 19 different instances for google and that with only 1 tab showing only the default page (google search).

I don't use 'google', whatever that is, but it is common for browsers to spawn different processes to provide security separation between different tabs.  Unix keeps memory in different processes separate. Memory in the same process space is a security liability. With only 1 tab open and 19 processes, I'd assume 3 are actually doing work you want and the others are for tracking. I don't know this as fact.

I don't use google commercial software as a way to avoid giving the largest internet tracking and advertising company in the world direct access to my computer. I'm always a little surprised when others choose to load software from tracking companies. Whatever works for you, do it.

If you really want htop to freak you out, press an 'h'. This will show all the threads along with all the processes. Enjoy. ;)
There are many deeper tools to look at specific processes, but without the right knowledge, they aren't all that useful.

---

### Post by wyattwhiteeagle on 2022-03-16
> **dragonfly41 said:**
> In Stacer (which you write you have installed) open Processes panel, search chrome in search field, and you see one process per tab in Chrome browser.

In stacer, under processes, I searched chrome...it shows 13 processes for only 1 tab in google

---

### Post by wyattwhiteeagle on 2022-03-16
> **VMC said:**
> ```
[FONT=monospace][COLOR=#000000]systemd-analyze blame[/COLOR][/FONT]
```[FONT=monospace][COLOR=#000000] Will give you boot up timing results[/COLOR]
[/FONT]

```
11.359s networkd-dispatcher.service                                              
10.134s NetworkManager-wait-online.service                                       
 7.024s udisks2.service                                                          
 6.194s dev-sda2.device                                                          
 5.578s accounts-daemon.service                                                  
 5.415s NetworkManager.service                                                   
 5.028s gpu-manager.service                                                      
 4.872s polkit.service                                                           
 4.065s apparmor.service                                                         
 3.847s thermald.service                                                         
 3.816s avahi-daemon.service                                                     
 3.771s dundee.service                                                           
 3.728s ofono.service                                                            
 3.670s wpa_supplicant.service                                                   
 3.661s systemd-logind.service                                                   
 3.536s systemd-resolved.service                                                 
 3.438s apport.service                                                           
 3.379s ModemManager.service                                                     
 3.107s rsyslog.service                                                          
 1.877s systemd-backlight@backlight:acpi_video0.service                          
 1.773s grub-common.service                                                      
 1.650s upower.service                                                           
 1.602s e2scrub_reap.service                                                     
 1.434s systemd-modules-load.service                                             
 1.323s pppd-dns.service                                                         
 1.039s systemd-rfkill.service                                                   
  968ms systemd-sysctl.service                                                   
  852ms systemd-tmpfiles-setup.service                                           
  783ms keyboard-setup.service                                                   
  717ms systemd-udevd.service                                                    
  647ms grub-initrd-fallback.service                                             
  576ms systemd-journald.service                                                 
  561ms user@1000.service                                                        
  525ms systemd-udev-trigger.service                                             
  524ms systemd-timesyncd.service                                                
  442ms systemd-tmpfiles-setup-dev.service                                       
  393ms systemd-sysusers.service                                                 
  368ms ufw.service                                                              
  324ms systemd-random-seed.service                                              
  289ms dev-disk-by\x2duuid-2f96bade\x2d55e4\x2d456d\x2db5e1\x2df08a2eb41923.swap
  286ms lvm2-monitor.service                                                     
  254ms setvtrgb.service                                                         
  235ms sddm.service                                                             
  228ms dev-hugepages.mount                                                      
  226ms dev-mqueue.mount                                                         
  225ms blk-availability.service                                                 
  224ms sys-kernel-debug.mount                                                   
  223ms sys-kernel-tracing.mount                                                 
  209ms kmod-static-nodes.service                                                
  178ms alsa-restore.service                                                     
  166ms systemd-backlight@backlight:intel_backlight.service                      
  163ms systemd-remount-fs.service                                               
  163ms console-setup.service                                                    
  131ms systemd-update-utmp.service                                              
  104ms systemd-user-sessions.service                                            
   89ms rtkit-daemon.service                                                     
   78ms kerneloops.service                                                       
   63ms systemd-journal-flush.service                                            
   31ms user-runtime-dir@1000.service                                            
   24ms plymouth-quit.service                                                    
   23ms plymouth-start.service                                                   
   17ms plymouth-read-write.service                                              
   12ms systemd-update-utmp-runlevel.service                                     
   11ms sys-fs-fuse-connections.mount                                            
    9ms sys-kernel-config.mount                                                  



```

---

### Post by wyattwhiteeagle on 2022-03-16
> **TheFu said:**
> I don't use 'google', whatever that is, but it is common for browsers to spawn different processes to provide security separation between different tabs.  Unix keeps memory in different processes separate. Memory in the same process space is a security liability. With only 1 tab open and 19 processes, I'd assume 3 are actually doing work you want and the others are for tracking. I don't know this as fact.

I don't use google commercial software as a way to avoid giving the largest internet tracking and advertising company in the world direct access to my computer. I'm always a little surprised when others choose to load software from tracking companies. Whatever works for you, do it.

If you really want htop to freak you out, press an 'h'. This will show all the threads along with all the processes. Enjoy. ;)
There are many deeper tools to look at specific processes, but without the right knowledge, they aren't all that useful.

I believe the google processes issue is due to chrome web browser being so "resource-hungry".
I'm gonna reset google's settings to default and see if that clears out some of the processes.

I am in search of a lighter web browser.

---

### Post by wyattwhiteeagle on 2022-03-16
> **Claus7 said:**
> Hello,



so, after all responses, in order to recup, since I understand that it is really annoying the fact that your system slows down, and the fact that many different factors might affect this performance:
1) either it is a failing hardware
2) either something causes your system, even from the boot stage, to have performance issues
3) either something runs in parallel and causes the system to slow down: I prefer gnome-system-monitor, since it graphically shows both the swap and actual memory along with cpu performance. htop and the like are more command line tools: it is a matter of taste. In your case I would try to see if these values change at the first stages of booting and some time later, when I actually observe problems in my performance.
4) I would add one more: have you checked how much disk space you have available (free)? I recently got rid of many gb and saw that my system rejuvenated! To give you an idea it was an hdd ~80% and reduced it to ~30%.

Hope that all these will guide you in the right direction.

Regards!

I plan to assess these after resetting google's settings back to default.

---

### Post by dragonfly41 on 2022-03-16
There are some Chrome extensions I use to reduce demands on resources (if you have many tabs as I do).
OneTab
Session Buddy
Open the Tab Sidebar
Group Your Tabs

Regarding lean browsers there is Brave and Pale Moon.

---

### Post by TheFu on 2022-03-16
Looking at the system-analyze output - I see lots of stuff that Canonical loads for convenience which aren't needed.
Do you actually use pppd-dns.service in 2022?  That seems really odd, if so.
ModemManager?
There's no need for udisks2 or avahi, though I suppose it is a convenience for some GUI stuff.
I didn't look to hard at everything.

As always, convenience adds overhead.

But did you look at the system logs?  That's likely where the issue will be seen and nowhere else.

>  I am in search of a lighter web browser. 
There are lots of lighter browsers, usually at the risk of slight incompatibilities.
I use **lynx** and **dillo** for many websites when I just want the information and not all the dancing gerbils or hamster dances. They have liabilities, so they aren't great, general purpose browsers. Still, if you just want the data, they are very light and don't look ahead and pre-download 50 links like Chrome does, in the name of speed.

Browsers that support addons or plugins often get blamed for poorly written addons.  Whenever there is an issue that is traced back to a browser, step 1 is to run it in 'safe-mode', which disables all addons.  Think I have 4 addons for Firefox - NoScript, AdBlock Origin, Wallabagger, and TreeStyleTab.  TreeStyleTab is by far the most important for productivity. It puts tabs on the side, not the top. We all have wide-screen monitors, but for some reason programmers insist on putting tabs in the limited vertical space. It also supports 'pinning' tabs to a tiny button, which allows commonly used URLs to be at my fingertip, using hardly any screen space.  Alas, TreeStyleTab has a history of buggy code and usually needs to be restarted manually a few times a week. According to Firefox dev and memory tracing tools, it doesn't use much memory at all.

I'm fighting with Firefox now on something like this. TV schedule data has been off by 1 hour for some external websites AND my LAN TV schedule jellyfin media server in my normal FF profile. Under a different account running on the same machine, the issue happens too.  
OTOH, Firefox running on a different OS (same version of Firefox) doesn't have this issue.  Chromium always shows the correct time on all accounts and both OS installs.  It is purely a display issue. Recordings are happening at the correct times, for the correct duration, on the correct channels. 
[https://time.gov/](https://time.gov/) shows the wrong time - says I'm in a different timezone.  The system clock shows the correct time and timezone.  I'm at a loss.

1 hour difference. Driving me nuts, even though everything is working.

---

### Post by wyattwhiteeagle on 2022-03-16
> **TheFu said:**
> Looking at the system-analyze output - I see lots of stuff that Canonical loads for convenience which aren't needed.
...

pppd-dns.servic
...udisks2
...avahi...
I didn't look to hard at everything.

As always, convenience adds overhead.

I'm not sure if I use those or not.
I did notice some old stuff that I believed isn't needed anymore as well.
I just aren't sure how to disable or purge those.

> **TheFu said:**
> But did you look at the system logs?  That's likely where the issue will be seen and nowhere else.

Nope, haven't had the chance to check them yet.
I'll get to it though, I promise.

> **TheFu said:**
> There are lots of lighter browsers, usually at the risk of slight incompatibilities.
I use **lynx** and **dillo** for many websites when I just want the information and not all the dancing gerbils or hamster dances. They have liabilities, so they aren't great, general purpose browsers. Still, if you just want the data, they are very light and don't look ahead and pre-download 50 links like Chrome does, in the name of speed.

I just noticed lynx and dillo in a wikipedia page.
I believe it was the graphical interface's or the install procedure's that caused me to skip over them.

I believe, at least for the moment, my web browser choices are limited to Brave or Otter.

---

### Post by wyattwhiteeagle on 2022-03-16
> **TheFu said:**
> top and htop are for seeing which processes are using RAM and CPU.  There are monitoring tools which can be setup, but I don't think you'd want to do that based on prior threads.  Too complicated.

Um, if there are things which can narrow down the time spent looking as well as a more direct approach to finding solutions...
I'd rather at least try instead of just believing that setting something up is too complicated.

May I please have the list of monitoring tools you mention so I can look into them?

I've considered creating a script that gathers information about what error's the system may be experiencing and creating a file which reflect's that information (maybe System_Errors.txt) and having it put into a location where I can easily find and use that file.
Not knowing all the locations where error infrormation might show up is the main reason I haven't created this script.

---

### Post by wyattwhiteeagle on 2022-03-16
> **Claus7 said:**
> Hello,

...
4) I would add one more: have you checked how much disk space you have available (free)? I recently got rid of many gb and saw that my system rejuvenated! To give you an idea it was an hdd ~80% and reduced it to ~30%...

Isn't there a simple terminal code that shows that information?

---

### Post by #&amp;thj^% on 2022-03-16
> **wyattwhiteeagle said:**
> Isn't there a simple terminal code that shows that information?

See if this meets your needs.```
df -i
```
or to show gigs available```
df -h
```:

---

### Post by wyattwhiteeagle on 2022-03-16
> **1fallen said:**
> See if this meets your needs.```
df -i
```
or to show gigs available```
df -h
```:

Thank you...

```
wyatt@wyatt-latitudee5400:~$ df -hFilesystem      Size  Used Avail Use% Mounted on
udev            1.9G     0  1.9G   0% /dev
tmpfs           389M  6.3M  382M   2% /run
/dev/sda2       910G   37G  826G   5% /
tmpfs           1.9G   13M  1.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           1.9G     0  1.9G   0% /sys/fs/cgroup
tmpfs           389M   12K  389M   1% /run/user/1000
wyatt@wyatt-latitudee5400:~$ 
```

I believe it shows the important part.../dev/sda2

What it doesn't show is the info for other partitions on the same drive.

/dev/sda1...FAT32........866mb...4kb used
/dev/sda3...linuxswap...6gb.......0 used
[FONT=Verdana]/dev/sda2      60604416 592680 60011736    1% /[/FONT]

---

### Post by guiverc on 2022-03-16
> **wyattwhiteeagle said:**
> 
I am in search of a lighter web browser.

Lubuntu for a time provided `[falkon]("https://packages.ubuntu.com/focal/falkon")` as it's web browser; as it was lighter than the default `firefox`.   It maybe worth a try.

I forget which release/cycle(s) we were using/testing it (*maybe cosmic & disco* *as I recall testing with 1GB devices*), it's *lighter *and* faster* if I recall correctly *however* not being a full-featured browser, there were sites that it didn't deal well with.

We (*Lubuntu*) opted instead to replace it with `firefox`, which is heavier yes, but also has the advantage in that that package is managed by main Ubuntu so it's less work for us.  It's my understanding `falkon` has improved too, but I not really a large user of it.

Personally I still use `lynx` on occasion, esp. if all I want to **read** is a text article & don't care about any pictures; but I'm generally using a powerful browser to grab the link (ie. browse the web) and using `lynx` on web sites I find annoying.

Be careful with addons when you have limited RAM; as they all require RAM to operate meaning you've less RAM for your actual accessed pages.. Use only what you really need to, and weigh the cost of the addon with what it'll require to use it.

---

### Post by #&amp;thj^% on 2022-03-16
> **wyattwhiteeagle said:**
> 

What it doesn't show is the info for other partitions on the same drive.

/dev/sda1...FAT32........866mb...4kb used
/dev/sda3...linuxswap...6gb.......0 used
[FONT=Verdana]/dev/sda2      60604416 592680 60011736    1% /[/FONT]
I'm not sure why?
try then:
```
df -hT
```
Example:
```
Filesystem     Type      Size  Used Avail Use% Mounted on
dev            devtmpfs  3.6G     0  3.6G   0% /dev
run            tmpfs     3.6G  2.0M  3.6G   1% /run
/dev/sdb2      ext4      234G   44G  178G  20% /
tmpfs          tmpfs     3.6G     0  3.6G   0% /dev/shm
tmpfs          tmpfs     3.6G   55M  3.6G   2% /tmp
/dev/sdb1      vfat      511M  296K  511M   1% /boot/efi
/dev/sda3      ext4      429G   71G  336G  18% /media/data
tmpfs          tmpfs     732M  100K  732M   1% /run/user/1000
/dev/sdc1      fuseblk   1.9T  1.7T  205G  90% /run/media/me/My_Passport_2T

```

---

### Post by Claus7 on 2022-03-16
Hello,

oh! this thread has grown considerably since the last time I saw it! 

Concerning the disk usage I do not think that you have any issue, since your usage is ~5%. Instead of using the terminal, which is really fine, I would go with Disks. From flashback is under Applications->Accessories->Disks, yet you could get the same info.

Even from your boot analysis it doesn't seem to me that there is any problem from there either.

How much memory do you have available? Taking a look back on the thread I did not see any information about the ram consumption of your system.

Regards!

---

### Post by wyattwhiteeagle on 2022-03-17
> **Claus7 said:**
> Hello,

...

How much memory do you have available? Taking a look back on the thread I did not see any information about the ram consumption of your system.

With only Stacer open
RAM...3.8gb usable...375mb used

Along with everything, it's beginning to seem like startup delays, application hangs, and unrequested searches.

---

### Post by Claus7 on 2022-03-17
Hello,

keep a backup of your files just in case the disk is failing. I might miss something here yet, just 375mb used? Usable I guess is the total? I think its too low a value even just only for the operating system. I would think more or less ~ 1GB. I tried stacer and I get ~ the value you reporting for stacer alone, not stacer+os.

Regards!

---

### Post by wyattwhiteeagle on 2022-03-18
> **Claus7 said:**
> Hello,

keep a backup of your files just in case the disk is failing. I might miss something here yet, just 375mb used? Usable I guess is the total? I think its too low a value even just only for the operating system. I would think more or less ~ 1GB. I tried stacer and I get ~ the value you reporting for stacer alone, not stacer+os.

Regards!
I apologize for not understanding what you meant.

I had to switch back to Ubuntu minimal.
Lubuntu seemed lofty, and it crashed and wouldnt boot back up.
That happened after installing Otter Browser.

It seems like people are using gaming systems which gamers usually feel like there's never enough RAM, Processor, and Graphics.
I'm no gamer...why would I use a gaming system?

right now, I click Settings>About and for memory...here are the stats...

I know for sure I have 2...2gb RAM cards...totalling 4gb RAM but 3.8gb is available.
the other 0.2gb...I have no idea why it isn't usable.
and at the time...Stacer was reporting that only 375mb...MegaBytes...was being used.
Technical calculations are...1024mb is equal to 1gb.
My system has 3891.2 MegaBytes available RAM, and was using only 375 MegaBytes.
That means my whole system with only stacer open was using only a portion of only 1gb RAM.

How people are getting that my system doesn't have enough RAM to just simply run an Operating System is beyond me.

I believe the system has enough available RAM but only if I use a swap of at least 8gb.
(double the total RAM)
Gparted is showing that I have a 73.29gb linux-swap partition on /dev/sda, which is 1000gb.
I plan to create an 8gb swapfile to go along with it.

I haven't purged anything from Ubuntu minimal.
Right now, Stacer is reporting that 756mb of 3.8gb is being used.
System Monitor is reporting that 1.2gb (30.5%) of 3.8gb is being used with 973mb cache'd.

Now, if that isn't including the OS...then someone is gonna need to let me know how to get the reports you are wanting to see.

---

### Post by wyattwhiteeagle on 2022-03-18
[https://discourse.lubuntu.me/t/swap-and-lubuntu-21-04-hirsute-and-up/2591](https://discourse.lubuntu.me/t/swap-and-lubuntu-21-04-hirsute-and-up/2591)


> Q: Can I use swap partition & swapfile?


Yes you can.


The How-to guide says make sure there are no other "swap" lines in /etc/fstab.
You don't even give a hint of how to setup a swapfile when using a swap partition.

How can I set up a swapfile without deleting the swap partition?
> **guiverc said:**
> Ensure you have an adequate *swap* setup for your system.

With Lubuntu it's varies on release what the defaults are, but I *rarely* use the defaults as my devices are all old & thus low-powered (*thus I really benefit from swap*).

Useful links:

 - [https://discourse.lubuntu.me/t/how-to-create-a-swapfile-in-lubuntu-20-04-20-10/1959](https://discourse.lubuntu.me/t/how-to-create-a-swapfile-in-lubuntu-20-04-20-10/1959)

- [https://discourse.lubuntu.me/t/swap-and-lubuntu-21-04-hirsute-and-up/2591](https://discourse.lubuntu.me/t/swap-and-lubuntu-21-04-hirsute-and-up/2591)

The second was written as a FAQ, the first as a *howto* for 20.04 & 20.10

**Swap really matters.** I needed RAM to *assess *a family members box so stole 4GB of RAM from a box (it had 8GB) I use primarily in QA-testing & a couple of hours in the afternoon; as it still had 4GB I never expected to notice the difference - but i SURE DID !!!   A quick command (or two) & I had a *swapfile* setup & it was back to behaving like normal (as if it had 8GB again).

Recent releases of Lubuntu default to swap being created; however it's still too small for my old boxes; thus I increase it.  On most my installs though; I don't do anything as Lubuntu will happily use whatever swap was pre-setup.


The tool I'd explore your system with is `htop` which was already suggested; it's pre-installed on a Lubuntu system too.

---

### Post by Impavidus on 2022-03-18
You don't need a gaming machine to run Ubuntu (or a light flavour, at least). I'm on an 11 year old laptop with an Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz, 320GB spinning hard drive, integrated graphics and 8GiB RAM. That's the only part I've upgraded. It's somewhat low-powered by today's standards, but has absolutely no difficulty running Xubuntu, so Lubuntu should work too. Your computer appears to be a bit weaker though. My memory usage right now, running only Firefox with 3 tabs:```
$ free -h
               total        used        free      shared  buff/cache   available
Mem:           7,7Gi       1,1Gi       5,3Gi       215Mi       1,3Gi       6,2Gi
Swap:          8,5Gi          0B       8,5Gi
```Note that the total memory is slightly less than the installed 8GiB. That's because some of it is reserved for graphics.

The rule that swap should be twice your RAM was a good rule – 15 years ago, when your average computer had 1–2GiB of RAM. There's no real need to make swap larger than about 4GB. My swap is larger, because that was the default when I first installed Ubuntu on this laptop and I never bothered to change it. I never see any swap in use.

You mentioned somewhere that your computer slows down after some days or a week. Did you reboot during that time? If not, it may begin using swap, but you shouldn't really notice. Otherwise, I can imagine you may have very special hardware, requiring special settings or drivers to work correctly, or your hardware may be broken, or you need about a week to turn your system into a mess manually. You mentioned somewhere you use bleachbit to keep your computer clean. Applying too much bleach can destroy everything.

---

### Post by wyattwhiteeagle on 2022-03-18
> **Impavidus said:**
> You don't need a gaming machine to run Ubuntu (or a light flavour, at least). I'm on an 11 year old laptop with an Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz, 320GB spinning hard drive, integrated graphics and 8GiB RAM. That's the only part I've upgraded. It's somewhat low-powered by today's standards, but has absolutely no difficulty running Xubuntu, so Lubuntu should work too. Your computer appears to be a bit weaker though. My memory usage right now, running only Firefox with 3 tabs:```
$ free -h
               total        used        free      shared  buff/cache   available
Mem:           7,7Gi       1,1Gi       5,3Gi       215Mi       1,3Gi       6,2Gi
Swap:          8,5Gi          0B       8,5Gi
```Note that the total memory is slightly less than the installed 8GiB. That's because some of it is reserved for graphics.

The rule that swap should be twice your RAM was a good rule &#8211; 15 years ago, when your average computer had 1&#8211;2GiB of RAM. There's no real need to make swap larger than about 4GB. My swap is larger, because that was the default when I first installed Ubuntu on this laptop and I never bothered to change it. I never see any swap in use.

You mentioned somewhere that your computer slows down after some days or a week. Did you reboot during that time? If not, it may begin using swap, but you shouldn't really notice. Otherwise, I can imagine you may have very special hardware, requiring special settings or drivers to work correctly, or your hardware may be broken, or you need about a week to turn your system into a mess manually. You mentioned somewhere you use bleachbit to keep your computer clean. Applying too much bleach can destroy everything.

here's mine...
```
wyatt@wyatt-Latitude-E5400:~$ free -h
                    total        used        free      shared  buff/cache   available
Mem:          3.8Gi       913Mi       1.7Gi       171Mi       1.2Gi       2.5Gi
Swap:          73Gi          0B        73Gi
wyatt@wyatt-Latitude-E5400:~$
```

That's with default Brave browser with 2 tabs open
and 1 gedit open

I see 3.8G total...913M used...1.7G free...2.5G available

Lets see with nothing open...
```
wyatt@wyatt-Latitude-E5400:~$ free -h
                   total        used        free      shared  buff/cache   available
Mem:          3.8Gi       624Mi       2.1Gi        99Mi       1.1Gi       2.9Gi
Swap:          73Gi          0B        73Gi
wyatt@wyatt-Latitude-E5400:~$ 
```

---

### Post by dragonfly41 on 2022-03-18
Some thoughts.

Although I use Stacer, and recommend it for dashboard ease of use, in a limited system with low RAM I suggest that you close Stacer down after use.
It is an Electron (Node.js) app which consumes the equivalent of a Chrome tab.

I recollect that you have Wine installed and a messaging app which is used by some (but not you as you pointed out) for gaming. If you shut that down is there an impact on performance?

I also throw in hardware acceleration to look at but that is just a germ of an idea. I remember that this option can affect performance. 

I have found that adding a second RAM card (raise from 4GB to 8 GB) is the easiest way of removing bottlenecks but your budget is limited, I remember.

Do you experience slow performance running "Try Ubuntu" in a Live USB?

---

### Post by wyattwhiteeagle on 2022-03-18
> **dragonfly41 said:**
> Some thoughts.

Although I use Stacer, and recommend it for dashboard ease of use, in a limited system with low RAM I suggest that you close Stacer down after use.
It is an Electron (Node.js) app which consumes the equivalent of a Chrome tab.

I recollect that you have Wine installed and a messaging app which is used by some (but not you as you pointed out) for gaming. If you shut that down is there an impact on performance?

I also throw in hardware acceleration to look at but that is just a germ of an idea. I remember that this option can affect performance. 

I have found that adding a second RAM card (raise from 4GB to 8 GB) is the easiest way of removing bottlenecks but your budget is limited, I remember.

Do you experience slow performance running "Try Ubuntu" in a Live USB?

Stacer.
When I'm done using stacer, I don't click continue when I close stacer.
I click on Quit.
Clicking Continue leaves it running in the background.
It would be silly of me to knowingly leave things running in the background then come here claiming to have issue's.

About Wine-staging and IMVU
You misunderstood what I had said.
There are over 200,000 people in the world who use IMVU.
15% to 20% of those people are using Linux-based.
I'm the only one that uses my system...nobody else.
IMVU needs Wine or PlayOnLinux.
Some features used by IMVU works ONLY in Wine-staging...not POL...not Wine...not Wine-devel...ONLY in Wine-staging.
I use those features.

IMVU,Inc doesn't tell people they can run IMVU on Linux.
Why...because IMVU wants only Windows users, MacOS users and Iphone users to be using IMVU.
They don't support their own product being used on Linux and Linux-based.
I tried calling their support line.
As soon as they learned I was using Ubuntu...they told me they don't support it on linux-based and hung up.

Now, for other reader's who don't quite know why this is brought up here...
There are certain files that IMVU uses that are placed on the system.
These files just keep adding up causing performance issues.
IMVU,Inc doesn't want you to delete these specific files.

In another thread here on the forums...there is a link to a webpage about IMVU cache.
It tells how to empty the IMVU cache.
But the specific files they dont want you to clear out aren't in that cache...
they are in other cache's under different locations which are not included in the cache that imvu guides the user to clear out.
those files are log files, chkn files, and pickle files.
Only someone who actually uses IMVU knows about the these specific files.

The virtual goods product files (there could be thousands upon thousands of these on the system...I keep mine cleared out)
These files are included in IMVU's guide for clearing their cache.
chkn files are not included in that guide and they arent included in that cache.
They are used ONLY for creating products to sell in IMVU's "Shop"
The user creates these products.
Once the product passes IMVU's "peer review" and is available in the shop...
the user no longer needs these chkn files

At this link...it states the following...
[https://help.imvu.com/s/article/How-to-clear-the-IMVU-cache?language=en_US](https://help.imvu.com/s/article/How-to-clear-the-IMVU-cache?language=en_US)
> ...move these files to the trash bin: 


_buddyState.pickle
productAuth.pickle
localstorage.pickle
productInfoCache.db 
HttpCache
PixmapCache


chkn files are not included...
IMVU, Inc wants the chkn files to stay on the computer.
They add up causing performance issue's.
The user doesnt need these files to stay on the system.


The only other person that lives with me is my fiance...she has her own computer.
She don't need mine unless I'm working on hers. which isn't very often.

Most laptops have only 2 RAM slots.
I am using 2...2gb RAM cards.
Not 1...4gb RAM card.
I have no more available RAM slots.
To add more RAM means I need to buy 2 4gb RAM cards.
Speaking of...which specs do I need to be paying attention to when buying those RAM cards...see below...

Wow
I'm surprised that someone would even consider running a LiveUSB without restarting (restarting results in loss of everything done by the user) for a week or two just to see if it begins having performance issue's.



```
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 4GiB

        *-bank:0
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: M4 70T5663QZ3-CF7
             vendor: Samsung
             physical id: 0
             serial: 97AD30D7
             slot: DIMM_A
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)

        *-bank:1
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: M4 70T5663QZ3-CF7
             vendor: Samsung
             physical id: 1
             serial: 97AD30C8
             slot: DIMM_B
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)

```

---

### Post by Claus7 on 2022-03-18
Hello,

I'm sorry if I miss something, yet irrespective of the operating system you have 4GB of ram. I do not consider this value too much for today's standards. Having used such a system I was always careful with the number of open tabs in my browser. I knew that if I overdid it then it was game over: the system rebooted. 

I cannot think of something else than what is already mentioned. I would advice you to check the memory the way you did every time you observe slowing downs. For sure you can use your system, but you will have to limit the amount of processes you open at the same time to avoid bottlenecks.

Regards!

---

### Post by dragonfly41 on 2022-03-18
I take a passing interest in your plight only because you appear to be strapped for cash.

Now I have been in this situation myself scrabbling around to try to put together cannibalised parts (HDD's, RAM cards etc.) to build a working system. I have a bunch of discarded PC's laptops .. even old Iomega jazz drives from which one day I hope to scrape archives. But that's another story .. how to access Xircom 32 bit Cardbus (which I'm looking at as I write this)  from Ubuntu?

But I digress.

================

Regarding hardware acceleration referring here:

[https://ubuntuforums.org/showthread.php?t=2007084&highlight=hardware+acceleration](https://ubuntuforums.org/showthread.php?t=2007084&highlight=hardware+acceleration)

run this:

lspci | grep &#8220;VGA compatible controller&#8221;

================

Given the limited finances, one approach I put forward is to install Ubuntu on a Raspberry Pi and use your existing PC as a backup. But just looking I see that Raspberry Pi are in short supply.

[https://ubuntu.com/tutorials/how-to-install-ubuntu-desktop-on-raspberry-pi-4#1-overview](https://ubuntu.com/tutorials/how-to-install-ubuntu-desktop-on-raspberry-pi-4#1-overview)

[https://www.youtube.com/watch?v=ZWBe2E1Sgi0](https://www.youtube.com/watch?v=ZWBe2E1Sgi0)

[https://www.raspberrypi.com/products/raspberry-pi-4-model-b/](https://www.raspberrypi.com/products/raspberry-pi-4-model-b/)

[https://www.raspberrypi.com/products/raspberry-pi-4-model-b/?variant=raspberry-pi-4-model-b-8gb](https://www.raspberrypi.com/products/raspberry-pi-4-model-b/?variant=raspberry-pi-4-model-b-8gb)


================

> 
I have no more available RAM slots.
To add more RAM means I need to buy 2 4gb RAM cards.
Speaking of...which specs do I need to be paying attention to when buying those RAM cards...see below...


One reference site I use is Crucial. I buy RAM and SSD from Crucial.

[https://uk.crucial.com/articles/about-memory/computer-terminology-a-glossary-of-memory-terms](https://uk.crucial.com/articles/about-memory/computer-terminology-a-glossary-of-memory-terms)

[https://www.crucial.com/products/memory](https://www.crucial.com/products/memory)


================

> 
Wow
I'm surprised that someone would even consider running a LiveUSB without restarting (restarting results in loss of everything done by the user) for a week or two just to see if it begins having performance issue's.


I do not suggest running for a week or two. An hour or two should be enough of a session to see any impact on performance. And you are aware that you can create a persistent LiveUSB for such testing?

Here is an HDR video to test your graphics.

[https://www.youtube.com/watch?v=LXb3EKWsInQ](https://www.youtube.com/watch?v=LXb3EKWsInQ)

================

Alternatives to IMVU (avoiding use of Wine??)

[https://phreesite.com/games-like-imvu-alternatives/](https://phreesite.com/games-like-imvu-alternatives/)


[https://lyncconf.com/games-like-imvu/](https://lyncconf.com/games-like-imvu/)


[https://forum.unity.com/threads/released-imvu-api-for-unity.385484/](https://forum.unity.com/threads/released-imvu-api-for-unity.385484/)

But if you wish to use IMVU you can create avatars in Blender which does work on Ubuntu .. and is free. Bypassing Wine. Blender is worth trying in Ubuntu.

[https://www.katsbits.com/tutorials/imvu/getting-started.php](https://www.katsbits.com/tutorials/imvu/getting-started.php)

But graphics apps do require RAM. 4 GB is marginal but you can try Blender running only.


================

**[P.S.]** As an alternative to testing in LiveUSB mode you might just create a second desktop user which starts afresh with no configuration baggage. Does that test user session run smoother?

---

### Post by wyattwhiteeagle on 2022-03-18
Now that I;ve had to re-install for the 5th time this week,
I beliewe I know the root of some of my problems

I have no idea what all this system went through before I got it.
I can only guess that it went through a lot of stuff.

I have a feeling this isn't the manufacturer's original build.
I believe...based on the hardware info...that this system went to crap and the tech took it apart and sold the customer a new system and put this systems parts on the shelves to sell as parts.
When a more poor person needed a system the tech just threw parts together without checking the compatibility of the parts.

I believe minor hardware incompatibilities is only part of my problems.
I'm hoping my old laptop which is newer hardware than the one i'm on right now...
I'm hoping that the better hardware allows me to have better result's in pursuing the other problems

So I'm gonna clean up my old laptop.
It is newer hardware
8gb RAM
better CPU and a better graphics processor
I know what all that system has been through.

I'll let ya'll know when I'm back on.

---

### Post by wyattwhiteeagle on 2022-03-19
Well folks...
I couldn't revive the newer hardware.
That system is too far gone.
Water got spilled on the keyboard and touchpad.
I was hoping it dried out and was ok...

So I'm stuck with this one until I can get a new one.

I haven't purged or installed anything.

I know all of the flavour's have their downfalls, but I think I need to choose the one that works best on this system and learn to live with it by learning the proper ways to maintain it's stability and performance.

I already tried Lubuntu, but I don't believe I gave Xubuntu a real chance.

I'll let ya'll know when Xubuntu is installed.

---

### Post by dragonfly41 on 2022-03-19
I learned the hard way that it is not easy to repair broken laptops. They are throwaways. I have several.
Instead I invested in a modular desktop tower PC (Dell 3268 some years back).
This gives the breathing space to recycle old drives, add StarTech external dual docking bay with SSD's (as I write now, I am on Ubuntu 20.04 running on an _external SSD(s) and HDD's_).  A duff keyboard (as you have) can be replaced.

I would hunt around for an old tower PC perhaps found in a local charity shop or PC recycling centre used by local authorities who are clearing out. [Then refer to the forum which focuses on recycling old gear.]("https://ubuntuforums.org/showthread.php?t=2130640")

---

### Post by wyattwhiteeagle on 2022-03-19
> **dragonfly41 said:**
> I learned the hard way that it is not easy to repair broken laptops. They are throwaways. I have several.
Instead I invested in a modular desktop tower PC (Dell 3268 some years back).
This gives the breathing space to recycle old drives, add StarTech external dual docking bay with SSD's (as I write now, I am on Ubuntu 20.04 running on an _external SSD(s) and HDD's_).  A duff keyboard (as you have) can be replaced.

I would hunt around for an old tower PC perhaps found in a local charity shop or PC recycling centre used by local authorities who are clearing out. [Then refer to the forum which focuses on recycling old gear.]("https://ubuntuforums.org/showthread.php?t=2130640")

Water on the keyboard and touchpad...the water had gotten to the mainboard and caused all kinds of connections in the circuits and fried that laptop.
It isn't just a duffed up keyboard...its a duffed up laptop.
I kept what I could use later and trashed the rest.

So I'm stuck with this one until I get a new one...maybe in about 6 months

How do I keep the screen from locking up on me every time I walk away from the system?
I thought I had disabled the feature.

---

### Post by dragonfly41 on 2022-03-19
[https://linuxconfig.org/disable-turn-off-lock-screen-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/disable-turn-off-lock-screen-on-ubuntu-20-04-focal-fossa-linux)

---

### Post by wyattwhiteeagle on 2022-03-19
> **dragonfly41 said:**
> [https://linuxconfig.org/disable-turn-off-lock-screen-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/disable-turn-off-lock-screen-on-ubuntu-20-04-focal-fossa-linux)

Um...man, you must be confused.
Don't worry...it's my fault for switching 'buntu flavours so frequently.

I'm running Xubuntu.
The images at that link look's like Ubuntu (Vanilla)
And the instructions don't match my Xubuntu.

---

### Post by dragonfly41 on 2022-03-20
[COLOR=#000000]> The images at that link look's like Ubuntu (Vanilla)

[/COLOR]Regardless, (although I am not on Xubuntu to verify), surely Step 1 applies? Dig deeper.

[COLOR=#808080][FONT=&quot][I]Open up the top right menu and click on the gear wheel ( settings ) icon

[/I][/FONT][/COLOR]

---

### Post by wyattwhiteeagle on 2022-03-20
> **dragonfly41 said:**
> [COLOR=#000000]

[/COLOR]Regardless, (although I am not on Xubuntu to verify), surely Step 1 applies? Dig deeper.

[COLOR=#808080][FONT=&amp][I]Open up the top right menu and click on the gear wheel ( settings ) icon

[/I][/FONT][/COLOR]

Yes, the general rules do apply.
Except in Xubuntu, the settings I'm looking for aren't under the menu's in the top right.
They seemed to be under the Xubuntu "Start" menu under "Settings" somewhere.

I'm not sure how I did it, but the screen isn't locking on me anymore.
Now I don't have to punch in my password every time I come back to the laptop.

Xubuntu does seem to be more stable on my laptop than the other's I've tried.

Now to continue with the reasons I started this thread...

Until next time
Wyatt

---

### Post by dragonfly41 on 2022-03-20
Some parallel advice here.

[https://ubuntuforums.org/showthread.php?t=2472960](https://ubuntuforums.org/showthread.php?t=2472960)

Xubuntu + internal SSD + 4GB (as you have now) might swing it.

Cost: replacing your internal HDD with SSD. Or attach external SSD via USB (as I do).
Then you can dual boot between internal HDD and external SSD.

---

### Post by wyattwhiteeagle on 2022-03-20
> **dragonfly41 said:**
> Some parallel advice here.

[https://ubuntuforums.org/showthread.php?t=2472960](https://ubuntuforums.org/showthread.php?t=2472960)

Xubuntu + internal SSD + 4GB (as you have now) might swing it.

Cost: replacing your internal HDD with SSD. Or attach external SSD via USB (as I do).
Then you can dual boot between internal HDD and external SSD.

Thank you for that.
Switching from HDD to SSD does seem logical, especially in my situation.
Considering switching within the next 12 months.

Due to limited finances, I have deleted the default 2gb swapfile and created a 8gb swapfile.
Just doing that has shown great improvement.

It isn't showing overall improvement...I'm working on that.

Working on...
> System log sizes and how frequently they rotate.
App's running in the background which doesn't need to.
(I know some app's need to run in the background to preserve functionality)
Unneeded app's and services loading up at boot.
Purging apps and packages I don't use.

After I take care of all that...
I plan to look more into which app's on my system actually "phone home".
Seem's that has an effect on performance also.

---

### Post by wyattwhiteeagle on 2022-03-20
> **TheFu said:**
> ...pppd-dns.service...ModemManager...udisks2 or avahi...

It looks like the vender presets are over-ruling my changes.
I disabled at least those but they are still loading up.
Do I need to remove, purge and block the respective app's, program's and/or packages?

---

### Post by wyattwhiteeagle on 2022-03-22
Um...I think I got it...

If there are no wire's going from my laptop to my router...then I dont use a modem.
Also, my laptop connect's through wifi...not a modem

Thus I can disable or remove it safely

> ModemManager - If you have a cable Internet and you do not plan to use a modem, disable it.

Is a modern router considered a modem?
Do I understand it wrong?
How would I check to see if I have a modem or a router?

I'm thinking my router is a modem and I don't use a cable to connect to the internet

---

### Post by wyattwhiteeagle on 2022-03-28
> **dragonfly41 said:**
> There are some Chrome extensions I use to reduce demands on resources (if you have many tabs as I do).
OneTab
Session Buddy
Open the Tab Sidebar
Group Your Tabs

May I please have the links to these Chrome extensions?

I've search the Chrome browser extension's and none of these appear.

---

