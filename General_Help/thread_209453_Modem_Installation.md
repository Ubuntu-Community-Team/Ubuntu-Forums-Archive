---
title: "Modem Installation"
date: 2006-07-05
forum: General Help
---

### Post by cai23 on 2006-07-05
hi!
need help, Im trying to install a D-Link Software Modem Card - DMF-562IS(model) in ubuntu 5.10. I just cant make it get internet connections. I've already installed modem driver which is "hsfmodem 7.47.00.01" . 

below is the current configuration:

Current parameters: ("hsfconfig --info")
Config for modem unit 0: /dev/ttySHSF0
        Device instance: 0-PCI-14f1:2f00-14f1:2003
        HW revision    : Basic2 2.18 Standard DAA 3VoltsIA
        HW profile name: hsfpcibasic2hsfi
        Registration ID: EC99-6E8D-6BBE
        License key    : FREE
        License status : FREE (max 14.4kbps data only)

The /dev/modem alias (symlink) points to ttySHSF0

---

### Post by cai23 on 2006-07-05
I tried to scan my modem through "sudo wvdialconf /etc/wvdial.conf," 
below is the result, hope it help...


Scanning your serial ports for a modem.

Port Scan<*1>: Scanning ttySHSF0 first, /dev/modem is a link to it.
ttySHSF0<*1>: ATQ0 V1 E1 -- OK
ttySHSF0<*1>: ATQ0 V1 E1 Z -- OK
ttySHSF0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttySHSF0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttySHSF0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttySHSF0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttySHSF0<*1>: Modem Identifier: ATI -- 56000
ttySHSF0<*1>: Speed 4800: AT -- OK
ttySHSF0<*1>: Speed 9600: AT -- OK
ttySHSF0<*1>: Speed 19200: AT -- OK
ttySHSF0<*1>: Speed 38400: AT -- OK
ttySHSF0<*1>: Speed 57600: AT -- OK
ttySHSF0<*1>: Speed 115200: AT -- OK
ttySHSF0<*1>: Speed 230400: AT -- OK
ttySHSF0<*1>: Speed 460800: AT -- OK
ttySHSF0<*1>: Max speed is 460800; that should be safe.
ttySHSF0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
Port Scan<*1>: S1   S2   S3   S4   S5   S6   S7   S8
Port Scan<*1>: S9   S10  S11  S12  S13  S14  S15  S16
Port Scan<*1>: S17  S18  S19  S20  S21  S22  S23  S24
Port Scan<*1>: S25  S26  S27  S28  S29  S30  S31  S32
Port Scan<*1>: S33  S34  S35  S36  S37  S38  S39  S40
Port Scan<*1>: S41  S42  S43  S44  S45  S46  S47  S48
Port Scan<*1>: S49  S50  S51  S52  S53  SHSF1 SHSF2 SHSF3
Port Scan<*1>: SHSF4 SHSF5 SHSF6 SHSF7

Found a modem on /dev/ttySHSF0, using link /dev/modem in config.
Modem configuration written to /etc/wvdial.conf.
ttySHSF0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

---

