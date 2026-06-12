---
title: "System freezes periodically without any apparent reason"
date: 2021-08-25
forum: General Help
---

### Post by federgaz on 2021-08-25
Hello,
 I am searching for help with a problem that is affecting my system. Increasingly, since I updated from the previous LTS version of Ubuntu to the 20.04, my system freezes without any apparent reason from time to time.
It freezes for 15-20-30 seconds: during this period only the cursor of the mouse is working while all the programs and windows that are open are completely blocked. After this period everything goes back to normal.
It freezes even when I am running very simple programs so I do not think that the freezing is due to an overload for the CPU or the memory.
 These are the spec of my system (I got these info with Phoronix Test Suite):


PROCESSOR:          Intel Core i7-5500U @ 3.00GHz
    Core Count:       2                                        
    Thread Count:     4                                        
    Extensions:       SSE 4.2 + AVX2 + AVX + RDRAND + FSGSBASE 
    Cache Size:       4 MB                                     
    Microcode:        0x2f                                     
    Core Family:      Broadwell                                
    Scaling Driver:   intel_pstate powersave                   

  GRAPHICS:           Intel HD 5500
    Frequency:        950MHz           
    Screen:           1366x768         

  MOTHERBOARD:        LENOVO Lenovo G50-80
    BIOS Version:     B0CN96WW                               
    Chipset:          Intel Broadwell-U-OPI                  
    Audio:            Intel Broadwell-U Audio                
    Network:          Realtek RTL8111/8168/8411 + Intel 3160 

  MEMORY:             8GB

  DISK:               480GB KINGSTON SA400S3
    File-System:      ext4                          
    Mount Options:    errors=remount-ro relatime rw 
    Disk Scheduler:   MQ-DEADLINE                   
    Disk Details:     Block Size: 4096              

  OPERATING SYSTEM:   Ubuntu 20.04
    Kernel:           5.4.0-66-generic (x86_64)                                                                                   
    Desktop:          GNOME Shell 3.36.4                                                                                          
    Display Server:   X Server 1.19.6                                                                                             
    Compiler:         GCC 9.3.0                                                                                                   
    Security:         itlb_multihit: KVM: Vulnerable                                                                              
                      + l1tf: Mitigation of PTE Inversion                                                                         
                      + mds: Mitigation of Clear buffers; SMT vulnerable                                                          
                      + meltdown: Mitigation of PTI                                                                               
                      + spec_store_bypass: Mitigation of SSB disabled via prctl and seccomp                                       
                      + spectre_v1: Mitigation of usercopy/swapgs barriers and __user pointer sanitization                        
                      + spectre_v2: Mitigation of Full generic retpoline IBPB: conditional IBRS_FW STIBP: conditional RSB filling 
                      + srbds: Mitigation of Microcode                                                                            
                      + tsx_async_abort: Not affected 

Any help will be highly appreciated, thank you.

Federico

---

### Post by not-published on 2021-08-25
(1)  allot of firefox use will freeze the machine.  it happens on apple and win10 (which now uses firefox internals).  debian was warned NOT to use the memory method it did and did it anyway.  as a result:  each web page opened consumes roughly 200MB.  open and close allot of pages you have a BIG problem.  why is poor memory management.  I got IP BANNED for telling them they were wrong in the past.  Now it happens on every desktop in the world - every day - countless times - all platforms.  And the people selling memory *love* it, and hate moi.

I'm trolling of course - except very serious:  you need to EXIT FIREFOX every so many web page readings.  you need to EXIT FIREFOX before you go to bed.

(2)  swap space.  is it 2x or more your memory like it should be?

(3)  NICE.  when your deep freeze happens wait a 1/2 hr for it to finish it could be cron (or anacron) preening and checkinig your hard-drive.  sometimes the "admins" forget to use nice(1) on these regularly scheduled maintenance jobs and your PC appears to be freezing due to firefox when actually they forgot to nice(1) the jobs and if you wait 1/2 hr you PC will be running fine again.  Don't get the two confused you don't want to reboot during a cron(1) job.

(4)  check /var/log/files for evidence of error logs (or your graphical log checker)

---

### Post by wildmanne39 on 2021-08-25
>  (2) swap space. is it 2x or more your memory like it should be?
This does not apply to modern computers with enough memory, the OP has 8 gigs of ram, so essentially you only need swap to hibernate your computer, I use to still set 2 gigs of swap though more out of habit then anything else, but since ubuntu uses swap files now I do not mess with it at all.

---

### Post by federgaz on 2021-08-26
1) Thanks for the suggestion, I will pay more attention to the utilization of firefox from now on. If this is true it means that simply switching to another web browser will fix the issue?
2) Here is my swap and ram utilization[COLOR=#4E9A06][B]:

federico@lenovoFN-G50[/B][/COLOR]:[COLOR=#3465A4]**~**[/COLOR]$ swapon -s Filename				Type		Size	Used	Priority
/dev/sda2                              	partition	4095996	0	-2

[COLOR=#4E9A06]**federico@lenovoFN-G50**[/COLOR]:[COLOR=#3465A4]**~**[/COLOR]$ free -m
              total        used        free      shared  buff/cache   available
Mem:           7882        1464        3884         459        2533        5657
Swap:          3999           0        3999
3)ok

4) Here is the check of the logs:

11:30:25 gdm-session-wor: gkr-pam: unable to locate daemon control file
11:30:02 systemd: Failed to start Postfix Mail Transport Agent (instance -).
11:29:25 kernel: Bluetooth: hci0: unexpected event for opcode 0xfc2f
11:29:25 kernel: ACPI Error: Aborting method \_SB.PCI0.GFX0._DSM due to previous error (AE_NOT_FOUND) (20190816/psparse-529)
11:29:24 systemd-udevd: /etc/udev/rules.d/60-brother-libsane-type1-inst.rules:14 Invalid key 'SYSFS'
11:29:23 kernel: ACPI Error: Aborting method \_SB.PCI0.GFX0._DSM due to previous error (AE_NOT_FOUND) (20190816/psparse-529)
11:29:23 kernel: DMAR: Failed to find handle for ACPI object \_SB.PCI0.SDHC
11:29:23 kernel: ACPI Error: Aborting method \_SB.PCI0.GFX0._DSM due to previous error (AE_NOT_FOUND) (20190816/psparse-529)

---

### Post by HermanAB on 2021-08-26
If PAM fails to work, nothing will work:
“11:30:25 gdm-session-wor: gkr-pam: unable to locate daemon control file“

Is your HD full/broken/corrupted???

---

### Post by federgaz on 2021-08-26
> **HermanAB said:**
> If PAM fails to work, nothing will work:
&#8220;11:30:25 gdm-session-wor: gkr-pam: unable to locate daemon control file&#8220;

Is your HD full/broken/corrupted???

Hi Herman
No, my HD is not full nor broken, but I might have some problems with it. In fact now on the logs file appears this:

19:56:04 pulseaudio:   hw_ptr       : 1375824
**19:56:04 kernel: blk_update_request: I/O error, dev sda, sector 103623168 op 0x0: (READ) flags 0x80700 phys_seg 11 prio class 0**
19:22:56 systemd: Failed to start Refresh fwupd metadata and update motd.
13:13:24 kernel: iwlwifi 0000:03:00.0: No beacon heard and the time event is over already...
11:30:25 gdm-session-wor: gkr-pam: unable to locate daemon control file
11:30:02 systemd: Failed to start Postfix Mail Transport Agent (instance -).
11:29:25 kernel: Bluetooth: hci0: unexpected event for opcode 0xfc2f
11:29:25 kernel: ACPI Error: Aborting method \_SB.PCI0.GFX0._DSM due to previous error (AE_NOT_FOUND) (20190816/psparse-529)
11:29:24 systemd-udevd: /etc/udev/rules.d/60-brother-libsane-type1-inst.rules:14 Invalid key 'SYSFS'
11:29:23 kernel: ACPI Error: Aborting method \_SB.PCI0.GFX0._DSM due to previous error (AE_NOT_FOUND) (20190816/psparse-529)
11:29:23 kernel: DMAR: Failed to find handle for ACPI object \_SB.PCI0.SDHC
11:29:23 kernel: ACPI Error: Aborting method \_SB.PCI0.GFX0._DSM due to previous error (AE_NOT_FOUND) (20190816/psparse-529)

---

### Post by federgaz on 2021-09-02
Any suggestion on what this means?

---

