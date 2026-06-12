---
title: "I do not  know  how to Add this thing video=vesafb:off vga=normal'"
date: 2017-04-07
forum: General Help
---

### Post by 243750496 on 2017-04-07
In your logs I see see vesafb warnings and it needs to be disabled.

 ```
NVRM: Your system is not currently configured to drive a VGA console
4æœˆ 01 07:55:58 ATC kernel: NVRM: on the primary VGA device. The NVIDIA Linux graphics driver
4æœˆ 01 07:55:58 ATC kernel: NVRM: requires the use of a text-mode VGA console. Use of other console
4æœˆ 01 07:55:58 ATC kernel: NVRM: drivers including, but not limited to, vesafb, may result in
4æœˆ 01 07:55:58 ATC kernel: NVRM: corruption and stability problems, and is not supported.
```

To disable it, ```
Add 'video=vesafb:off vga=normal'
```  on the kernel command line in the bootloader configuration file.

Then reboot.



Let me know if this helps or not and if not describe the problem and generate and attach new logs.

System Ubuntu Budgie 17.04 with ryzen 1800X and Titian X Pascal  tring  to solve the  problem that  enable 2way SLI causes black screen and can doing  nothing 

Motherboard [https://www.ebay.com/itm/232274935746](https://www.ebay.com/itm/232274935746)

Q1:Why the  NVIDIA official said the  motherboard is  not  in the  official list?
[http://www.geforce.com/hardware/technology/sli/motherboards](http://www.geforce.com/hardware/technology/sli/motherboards)
Only am3+ show  up 
Q2:does  it  means the  official  support  not followed  titly but  will support  inthe future 
Q3:does it  mean it  will  not  support  am4 motherboard under Linux With SLI  only Windows can  use  the  sli function?
Q4:how to add  the command ```
'video=vesafb:off vga=normal 
```as the official said (How to do and  where  to put  it )
[ATTACH]274474[/ATTACH]

---

### Post by plucky on 2017-04-08
> To disable it,
Code:

Add 'video=vesafb: off vga=normal'

on the kernel command line in the bootloader configuration file.
Q4:how to add the command 

Edit the file /etc/default/grub and add the commands to the line```
GRUB_CMDLINE_LINUX="video=vesafb:off vga=normal"
``` between the "quote marks" for example.
Then run ```
sudo update-grub
``` from a terminal to add the line to the boot configuration file.

Good Luck

---

