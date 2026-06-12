---
title: "Getting coil whine with new kernel"
date: 2013-03-16
forum: General Help
---

### Post by MasterZ on 2013-03-16
Hi, 

I've got my PC since about 1 year now. 
It does a high pitched noise, which I found out to be 'coil whine' ([Coil noise]("http://en.wikipedia.org/wiki/Coil_noise")) coming from the motherboard. 
It does that when in the UEFI bios but it used to stop whenever I booted an OS (ubuntu 12.04 or Win7). 


Now I upgraded from 12.04 to 12.10 and I'm getting the noise in Ubuntu all the time. 
It comes from the motherboard, somewhere around the CPU; it gets stronger when the CPU is under load. 
I still don't get any noise in Win7. 

Before my Ubuntu upgrade, I was running with Kernel Linux 3.2.0-31-generic. 
I know that this kernel was bad at power management and that patches have solved this in newer kernels. I suspect that the new power management scheme is causing the noise. 


I first tried to disable CPU power management in the BIOS (disable C-States, C3, C6) but it doesn't help. 
I then tried the 'cpupower' utility and changed my CPU governor to conservative, powersave and performance but that doesn't change anything either. 

I found a temporary workaround that works by adding "acpi=off" to the grub startup line. Then there's no noise anymore. 
However that seems a bit overkill and I'd like to know if there could be another way around my issue. 

Can you guys help me ?
Thx.

---

### Post by dino99 on 2013-03-16
i first think about hardware guaranty indeed, as that hardware seems to be recent. So if it does not work as it might, then ask for the guaranty to be applied.

how are the temperatures ?
what /var/log/dmesg says about warnings/errors ?
google around your model , especially on the hardware forum where you buy it.

---

### Post by MasterZ on 2013-03-16
The temperatures are OK between 25-40°C

I've got some Errors related to ACPI in dmesg, but it does not seem that bad:
```
[    0.515961] pnp: PnP ACPI: found 12 devices
[    0.515961] ACPI: ACPI bus type pnp unregistered
[    0.582115] ACPI: Power Button [PWRB]
[    0.582137] ACPI: Power Button [PWRF]
[    0.582182] ACPI: Fan [FAN0] (off)
[    0.582197] ACPI: Fan [FAN1] (off)
[    0.582211] ACPI: Fan [FAN2] (off)
[    0.582225] ACPI: Fan [FAN3] (off)
[    0.582239] ACPI: Fan [FAN4] (off)
[    0.582274] ACPI: Requesting acpi_cpufreq
[    0.584418] ACPI: Thermal Zone [TZ00] (28 C)
[    0.584512] ACPI: Thermal Zone [TZ01] (30 C)
[    0.929158] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20120320/psargs-359)
[    0.929166] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT1._GTF] (Node ffff8804084737d0), AE_NOT_FOUND (20120320/psparse-536)
[    0.930520] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20120320/psargs-359)
[    0.930528] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT3._GTF] (Node ffff8804084738c0), AE_NOT_FOUND (20120320/psparse-536)
[    0.931238] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20120320/psargs-359)
[    0.931246] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT1._GTF] (Node ffff8804084737d0), AE_NOT_FOUND (20120320/psparse-536)
[    0.934355] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20120320/psargs-359)
[    0.934363] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT3._GTF] (Node ffff8804084738c0), AE_NOT_FOUND (20120320/psparse-536)
[    2.929815] ACPI Warning: 0x0000000000000460-0x000000000000047f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
[    2.929820] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    2.929823] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
[    2.929825] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    2.929827] ACPI Warning: 0x0000000000000500-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20120320/utaddress-251)
[    2.929829] ACPI Warning: 0x0000000000000500-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.LPCB.GPBX 2 (20120320/utaddress-251)
[    2.929831] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver

```


I thought about warranty but this would imply to send the MB back to vendor and it would mean I'm without a PC for several weeks. 
As I need it for work, I'd then need to get another Motherboard before returning that one, and this would be a bit dull. 

Also I'm not even sure they would replace it. 
I don't know if there's an official policy about coil noise at ASUS; and as it work under windows I fear that they would test it under windows, then return it back (charging me for it) because "no issue found".


I was kind of hoping there was a way to tweak/disable the Kernel CPU power management without completely getting rid of ACPI (so it still manages my SDD and other peripherals).

---

