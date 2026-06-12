---
title: "backlight and acpi settings for laptop"
date: 2013-02-13
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2013-02-13
i know there is a acpi thing you can set in grub as a kernel boot option
is there one of those things that will make the backlight keys update /sys/class/backlight/acpi_video0/brightness
i used to have a /sys/class/backlight/acpi_video0/actual_brightness but that disappeared after a bios update

i think if i can get the hardware to update /sys/class/backlight/acpi_video0/brightness when the brightness changes my backlight will behave properly, or is this a bios issue?
laptop in signature

---

### Post by matt_symes on 2013-02-13
Hi
 
To see if you have a broken dsdt try echoing a value into the sysfs file.
 
```
echo X | sudo tee /sys/class/backlight/acpi_video0/brightness
```
 
You can get the value for X in the command above from 0 to max_brightness that should also be in the directory /sys/class/backlight/acpi_video0/.
 
```
cat /sys/class/backlight/acpi_video0/max_brightness
```
 
If you can change the brightness that way then maybe you can remoap the keys.
 
The kernel parameter is
 
```
acpi_backlight=vendor
```
 
Kind regards

---

### Post by pqwoerituytrueiwoq on 2013-02-13
do i change vendor to say asus for example or is it "vendor" 

i can control the brightness from those files

after the bios update, the backlight got more annoying, now it changes on wake form suspend and when i login to max
max used to be 10 now it is 100, still has 10 levels though

edit:
acpi_backlight=vendor made things worse now the only levels are 0 and 100, brightness keys no longer work

---

### Post by pqwoerituytrueiwoq on 2013-02-13
any idea what is changing the brightness after login it changes after my startup scripts run, this is a new behavior after the bios update

---

### Post by matt_symes on 2013-02-13
> **pqwoerituytrueiwoq said:**
> do i change vendor to say asus for example or is it "vendor" 
 
It's the word vendor but i don't think you need it as... 
 
> i can control the brightness from those files
 
backlight control is not necessarily broken on your PC.
 
> 
after the bios update, the backlight got more annoying, now it changes on wake form suspend and when i login to max
max used to be 10 now it is 100, still has 10 levels though

 
That's not a real problem then.
 
>  
edit:
acpi_backlight=vendor made things worse now the only levels are 0 and 100, brightness keys no longer work
 
Remove it then :)
 
> **pqwoerituytrueiwoq said:**
> any idea what is changing the brightness after login it changes after my startup scripts run, this is a new behavior after the bios update
 
Is it getting brighter or darker after resume ?
 
What do your startup scripts do ?
 
Are there any ACPI/DSDT errors in the log files ?
 
Have you looked at remapping the brightness keys ?
 
Kind regards

---

### Post by pqwoerituytrueiwoq on 2013-02-13
I tried to detect what key code before for the brightness keys are and they don't show up, i used xev, so i made a different key combo for brightness keys

i have lightdm lower the brightness to what it was shutdown at when it sets up the greeter
when a user logs in the brightness goes to 100%
i tried to counter this with a startup script using lightdm and the session startup scripts they all run before the brightness changes to 100%

with this new bios [FONT=Courier New]xbacklight -get[/FONT] changes the brightness (changes it form 90 and 91), its set function works fine, and i have my [backlightx](http://pastebin.com/HzzHrS2g) script that i made to replace it, it just does not let me set it from lightdm's greeter setup while xbacklight does

```
~$ cat /etc/lightdm/lightdm.conf 
[SeatDefaults]
greeter-session=lightdm-gtk-greeter
user-session=xubuntu
#display-setup-script=sh -c "numlockx on;if [ -f /var/log/xbacklight ];then xbacklight -set $(cat /var/log/xbacklight);fi"
greeter-setup-script=sh -c "/usr/bin/numlockx on;if [ -f /var/log/backlightx ];then xbacklight -set $(cat /var/log/backlightx);fi;ogg123 /usr/share/sounds/ubuntu/stereo/system-ready.ogg &"
session-setup-script=sh -c "/usr/local/bin/xfce-login-script &"
session-cleanup-script=sh -c "backlightx --get current > /var/log/backlightx;/usr/local/bin/xfce-logout-script"
```when exiting suspend brightness goes to 100%

```
~$ dmesg | egrep -i "backlight|acpi"
[    0.000000] BIOS-e820: [mem 0x00000000bae35000-0x00000000bafe7fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000baffd000-0x00000000baffffff] ACPI data
[    0.000000] ACPI: RSDP 00000000000f0430 00024 (v02 _ASUS_)
[    0.000000] ACPI: XSDT 00000000baffee18 00074 (v01 _ASUS_ Notebook 06222004 MSFT 00010013)
[    0.000000] ACPI: FACP 00000000baf9ad98 000F4 (v04 _ASUS_ Notebook 06222004 MSFT 00010013)
[    0.000000] ACPI Warning: 32/64 FACS address mismatch in FADT - two FACS tables! (20121018/tbfadt-394)
[    0.000000] ACPI BIOS Bug: Warning: 32/64X FACS address mismatch in FADT - 0xBAFE4E40/0x00000000BAFE4D40, using 32 (20121018/tbfadt-521)
[    0.000000] ACPI: DSDT 00000000baf88018 116ED (v01 _ASUS_ Notebook 00000000 INTL 20091112)
[    0.000000] ACPI: FACS 00000000bafe4e40 00040
[    0.000000] ACPI: APIC 00000000baffdf18 000CC (v02 _ASUS_ Notebook 06222004 MSFT 00010013)
[    0.000000] ACPI: DBGP 00000000baffff18 00034 (v01 _ASUS_ Notebook 06222004 MSFT 00010013)
[    0.000000] ACPI: ECDT 00000000bafe4b18 000C1 (v01 _ASUS_ Notebook 06222004 AMI. 00000003)
[    0.000000] ACPI: SLIC 00000000baf9be18 00176 (v01 _ASUS_ Notebook 06222004 ASUS 00000001)
[    0.000000] ACPI: HPET 00000000bafe5d18 00038 (v01 _ASUS_ Notebook 06222004 AMI. 00000003)
[    0.000000] ACPI: MCFG 00000000bafe5c98 0003C (v01 _ASUS_ Notebook 06222004 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000baf87818 00787 (v01  PmRef  Cpu0Ist 00003000 INTL 20091112)
[    0.000000] ACPI: SSDT 00000000baf86018 00996 (v01  PmRef    CpuPm 00003000 INTL 20091112)
[    0.000000] ACPI: ASF! 00000000bafe4a18 000A0 (v32 INTEL       HCG 00000001 TFSM 000F4240)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x04] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x05] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x06] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x09] lapic_id[0x08] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0a] lapic_id[0x09] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0b] lapic_id[0x0a] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0c] lapic_id[0x0b] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0d] lapic_id[0x0c] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0e] lapic_id[0x0d] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0f] lapic_id[0x0e] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x10] lapic_id[0x0f] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.006196] ACPI: Core revision 20121018
[    0.121455] PM: Registering ACPI NVS region [mem 0xbae35000-0xbafe7fff] (1781760 bytes)
[    0.122429] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.122434] ACPI: bus type pci registered
[    0.132006] ACPI: Added _OSI(Module Device)
[    0.132009] ACPI: Added _OSI(Processor Device)
[    0.132012] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.132014] ACPI: Added _OSI(Processor Aggregator Device)
[    0.134268] ACPI: EC: EC description table is found, configuring boot EC
[    0.134274] ACPI: EC: Look up EC in DSDT
[    0.136665] ACPI: Executed 1 blocks of module-level executable AML code
[    0.139808] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.140392] ACPI: SSDT 00000000badca798 0073F (v01  PmRef  Cpu0Cst 00003001 INTL 20091112)
[    0.140965] ACPI: Dynamic OEM Table Load:
[    0.140969] ACPI: SSDT           (null) 0073F (v01  PmRef  Cpu0Cst 00003001 INTL 20091112)
[    0.141226] ACPI: SSDT 00000000badcba98 00303 (v01  PmRef    ApIst 00003000 INTL 20091112)
[    0.141820] ACPI: Dynamic OEM Table Load:
[    0.141823] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20091112)
[    0.141938] ACPI: SSDT 00000000badc9d98 00119 (v01  PmRef    ApCst 00003000 INTL 20091112)
[    0.142498] ACPI: Dynamic OEM Table Load:
[    0.142501] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20091112)
[    0.142737] ACPI: Interpreter enabled
[    0.142743] ACPI: (supports S0 S3 S4 S5)
[    0.142764] ACPI: Using IOAPIC for interrupt routing
[    0.148040] ACPI: EC: GPE = 0x1b, I/O: command/status = 0x66, data = 0x62
[    0.148192] ACPI: No dock devices found.
[    0.148197] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.148398] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.148402] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.148860] pci_root PNP0A08:00: Requesting ACPI _OSC control (0x1d)
[    0.149139] pci_root PNP0A08:00: ACPI _OSC control (0x1d) granted
[    0.175202] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.175235] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.175267] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.175299] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.178814] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12)
[    0.178859] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 12)
[    0.178901] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 12)
[    0.178943] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 12)
[    0.178985] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 12) *0, disabled.
[    0.179035] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 12) *0, disabled.
[    0.179078] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 10 12)
[    0.179122] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 12)
[    0.179372] ACPI: bus type scsi registered
[    0.179428] ACPI: bus type usb registered
[    0.179559] PCI: Using ACPI for IRQ routing
[    0.189127] pnp: PnP ACPI init
[    0.189140] ACPI: bus type pnp registered
[    0.189212] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.189231] pnp 00:01: Plug and Play ACPI device, IDs INT0800 (active)
[    0.189332] pnp 00:02: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.189361] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.189430] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.189451] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.189490] system 00:06: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.189522] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.189570] pnp 00:08: Plug and Play ACPI device, IDs SYN0a17 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f0e PNP0f0b PNP0f12 (active)
[    0.189600] pnp 00:09: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.189852] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.189921] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.190047] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.190069] pnp: PnP ACPI: found 13 devices
[    0.190071] ACPI: ACPI bus type pnp unregistered
[    0.736481] ACPI: AC Adapter [AC0] (on-line)
[    0.752314] ACPI: Lid Switch [LID]
[    0.752353] ACPI: Sleep Button [SLPB]
[    0.752385] ACPI: Power Button [PWRF]
[    0.752445] ACPI: Requesting acpi_cpufreq
[    0.756199] ACPI: Thermal Zone [THRM] (47 C)
[    0.756254] ACPI: Battery Slot [BAT0] (battery absent)
[    1.209605] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.209769] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[    1.209780] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.213034] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.213151] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[    1.213159] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.213263] ata2.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[    1.213269] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.223508] ata2.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[    1.223520] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    8.408364] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \GPIS 1 (20121018/utaddress-251)
[    8.408371] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 2 (20121018/utaddress-251)
[    8.408375] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.408379] ACPI Warning: 0x0000000000000540-0x000000000000054f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[    8.408381] ACPI Warning: 0x0000000000000540-0x000000000000054f SystemIO conflicts with Region \GP01 2 (20121018/utaddress-251)
[    8.408384] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.408385] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[    8.408388] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GP01 2 (20121018/utaddress-251)
[    8.408391] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.408392] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[    8.408395] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GP01 2 (20121018/utaddress-251)
[    8.408397] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.729132] asus_wmi: Backlight controlled by ACPI video driver
[   10.121266] acpi device:44: registered as cooling_device2
[   10.121546] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[  913.127071] xhci_hcd 0000:03:00.0: System wakeup enabled by ACPI
[  913.143080] ehci-pci 0000:00:1d.0: System wakeup enabled by ACPI
[  913.158973] ehci-pci 0000:00:1a.0: System wakeup enabled by ACPI
[  913.191423] ACPI: Preparing to enter system sleep state S3
[  913.519909] ACPI: Low-level resume complete
[  913.534750] ACPI: Waking up from system sleep state S3
[  913.667804] ehci-pci 0000:00:1a.0: System wakeup disabled by ACPI
[  913.699780] ehci-pci 0000:00:1d.0: System wakeup disabled by ACPI
[  913.747825] xhci_hcd 0000:03:00.0: System wakeup disabled by ACPI
[  914.107520] ata2.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[  914.107528] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[  914.124624] ata2.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[  914.124631] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[  917.172206] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[  917.302585] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[  917.302592] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[  917.334049] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[  917.334214] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[  917.334220] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[  917.378180] video LNXVIDEO:01: Restoring backlight state
[ 1170.122332] xhci_hcd 0000:03:00.0: System wakeup enabled by ACPI
[ 1170.138339] ehci-pci 0000:00:1d.0: System wakeup enabled by ACPI
[ 1170.154414] ehci-pci 0000:00:1a.0: System wakeup enabled by ACPI
[ 1170.186681] ACPI: Preparing to enter system sleep state S3
[ 1170.424630] ACPI: Low-level resume complete
[ 1170.439478] ACPI: Waking up from system sleep state S3
[ 1170.575110] ehci-pci 0000:00:1a.0: System wakeup disabled by ACPI
[ 1170.607087] ehci-pci 0000:00:1d.0: System wakeup disabled by ACPI
[ 1170.655131] xhci_hcd 0000:03:00.0: System wakeup disabled by ACPI
[ 1171.007720] ata2.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[ 1171.007727] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[ 1171.022832] ata2.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[ 1171.022839] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[ 1174.031546] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[ 1174.159504] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[ 1174.159511] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[ 1174.190829] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[ 1174.190990] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[ 1174.190996] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[ 1174.235090] video LNXVIDEO:01: Restoring backlight state

```i should be able to work around the wakeup brightness if i know where to put a script save the brightness on enter suspend and one to apply the old brightness i logged on wakeup (suggestions?)

---

### Post by pqwoerituytrueiwoq on 2013-02-15
seems the 3.6.11 kernel can control the backlight with software properly, but the Fn keys do nothing now and i can't downgrade the BIOS :(

i have attached a complete test of the 3.6.11, 3.7.8 and 3.8 rc6 kernels control of the backlight under the 210 bios

---

