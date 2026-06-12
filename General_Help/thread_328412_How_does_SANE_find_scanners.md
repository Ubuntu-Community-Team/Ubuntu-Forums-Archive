---
title: "How does SANE find scanners?"
date: 2006-12-30
forum: General Help
---

### Post by moshuptrail on 2006-12-30
Suddenly sane cannot find my scanner.  It was working fine a month ago.
I'm not sure how sane figures out what scanners are attached locally.  Does anyone know?

The command : scanimage -L
returns a message about nothing found.  But I know I've got a scanner on a usb port.  It works fine from Windows.

---

### Post by tagra123 on 2006-12-30
> **moshuptrail said:**
> Suddenly sane cannot find my scanner.  It was working fine a month ago.
I'm not sure how sane figures out what scanners are attached locally.  Does anyone know?

The command : scanimage -L
returns a message about nothing found.  But I know I've got a scanner on a usb port.  It works fine from Windows.



try 

sudo xsane

it should find the scanner.

There are post here that tell how to get rid of the sudo command first.

---

### Post by moshuptrail on 2006-12-30
Interesting output. I found a way to make it spill a lot of info.  For my scanner, an OfficeJet V40 multi-function printer, I think it needs the hplip backend.  But it's not getting it.

```
export SANE_DEBUG_DLL=128
[sanei_debug] Setting debug level of dll to 128.
[dll] sane_init: SANE dll backend version 1.0.11 from sane-backends 1.0.17
[dll] sane_init/read_dlld: processing /etc/sane.d/dll.d ...
[dll] sane_init/read_dlld: considering /etc/sane.d/dll.d/hplip
[dll] sane_init/read_config: reading dll.d/hplip
[dll] add_backend: adding backend `hpaio'
[dll] sane_init/read_dlld: done.
[dll] sane_init/read_config: reading dll.conf
[dll] add_backend: adding backend `net'
[dll] add_backend: adding backend `abaton'
[dll] add_backend: adding backend `agfafocus'
[dll] add_backend: adding backend `apple'
[dll] add_backend: adding backend `avision'
[dll] add_backend: adding backend `artec'
[dll] add_backend: adding backend `artec_eplus48u'
[dll] add_backend: adding backend `as6e'
[dll] add_backend: adding backend `bh'
[dll] add_backend: adding backend `canon'
[dll] add_backend: adding backend `canon630u'
[dll] add_backend: adding backend `coolscan'
[dll] add_backend: adding backend `coolscan2'
[dll] add_backend: adding backend `dmc'
[dll] add_backend: adding backend `epson'
[dll] add_backend: adding backend `fujitsu'
[dll] add_backend: adding backend `genesys'
[dll] add_backend: adding backend `gt68xx'
[dll] add_backend: adding backend `hp'
[dll] add_backend: adding backend `hpsj5s'
[dll] add_backend: adding backend `hp4200'
[dll] add_backend: adding backend `hp5400'
[dll] add_backend: adding backend `ibm'
[dll] add_backend: adding backend `leo'
[dll] add_backend: adding backend `lexmark'
[dll] add_backend: adding backend `ma1509'
[dll] add_backend: adding backend `matsushita'
[dll] add_backend: adding backend `microtek'
[dll] add_backend: adding backend `microtek2'
[dll] add_backend: adding backend `mustek'
[dll] add_backend: adding backend `mustek_usb'
[dll] add_backend: adding backend `mustek_usb2'
[dll] add_backend: adding backend `nec'
[dll] add_backend: adding backend `niash'
[dll] add_backend: adding backend `pie'
[dll] add_backend: adding backend `plustek'
[dll] add_backend: adding backend `qcam'
[dll] add_backend: adding backend `ricoh'
[dll] add_backend: adding backend `s9036'
[dll] add_backend: adding backend `sceptre'
[dll] add_backend: adding backend `sharp'
[dll] add_backend: adding backend `sm3600'
[dll] add_backend: adding backend `sm3840'
[dll] add_backend: adding backend `snapscan'
[dll] add_backend: adding backend `sp15c'
[dll] add_backend: adding backend `tamarack'
[dll] add_backend: adding backend `teco1'
[dll] add_backend: adding backend `teco2'
[dll] add_backend: adding backend `teco3'
[dll] add_backend: adding backend `u12'
[dll] add_backend: adding backend `umax'
[dll] add_backend: adding backend `umax1220u'
[dll] add_backend: adding backend `v4l'
[dll] add_backend: adding backend `hpaio'
[dll] add_backend: `hpaio' is already there
[dll] sane_get_devices
[dll] load: searching backend `hpaio' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-hpaio.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-hpaio.so.1'
[dll] init: initializing backend `hpaio'
[dll] load: searching backend `v4l' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-v4l.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-v4l.so.1'
[dll] init: initializing backend `v4l'
[dll] init: backend `v4l' is version 1.0.4
[dll] load: searching backend `umax1220u' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-umax1220u.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-umax1220u.so.1'
[dll] init: initializing backend `umax1220u'
[dll] init: backend `umax1220u' is version 1.0.1
[dll] load: searching backend `umax' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-umax.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-umax.so.1'
[dll] init: initializing backend `umax'
[dll] init: backend `umax' is version 1.0.44
[dll] load: searching backend `u12' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-u12.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-u12.so.1'
[dll] init: initializing backend `u12'
[dll] init: backend `u12' is version 1.0.0
[dll] load: searching backend `teco3' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-teco3.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-teco3.so.1'
[dll] init: initializing backend `teco3'
[dll] init: backend `teco3' is version 1.0.1
[dll] load: searching backend `teco2' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-teco2.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-teco2.so.1'
[dll] init: initializing backend `teco2'
[dll] init: backend `teco2' is version 1.0.9
[dll] load: searching backend `teco1' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-teco1.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-teco1.so.1'
[dll] init: initializing backend `teco1'
[dll] init: backend `teco1' is version 1.0.10
[dll] load: searching backend `tamarack' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-tamarack.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-tamarack.so.1'
[dll] init: initializing backend `tamarack'
[dll] init: backend `tamarack' is version 1.0.0
[dll] load: searching backend `sp15c' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-sp15c.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-sp15c.so.1'
[dll] init: initializing backend `sp15c'
[dll] init: backend `sp15c' is version 1.0.0
[dll] load: searching backend `snapscan' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-snapscan.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-snapscan.so.1'
[dll] init: initializing backend `snapscan'
[dll] init: backend `snapscan' is version 1.4.50
[dll] load: searching backend `sm3840' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-sm3840.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-sm3840.so.1'
[dll] init: initializing backend `sm3840'
[dll] init: backend `sm3840' is version 1.0.0
[dll] load: searching backend `sm3600' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-sm3600.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-sm3600.so.1'
[dll] init: initializing backend `sm3600'
[dll] init: backend `sm3600' is version 1.0.6
[dll] load: searching backend `sharp' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-sharp.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-sharp.so.1'
[dll] init: initializing backend `sharp'
[dll] init: backend `sharp' is version 1.0.0
[dll] load: searching backend `sceptre' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-sceptre.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-sceptre.so.1'
[dll] init: initializing backend `sceptre'
[dll] init: backend `sceptre' is version 1.0.10
[dll] load: searching backend `s9036' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-s9036.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-s9036.so.1'
[dll] init: initializing backend `s9036'
[dll] init: backend `s9036' is version 1.0.0
[dll] load: searching backend `ricoh' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-ricoh.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-ricoh.so.1'
[dll] init: initializing backend `ricoh'
[dll] init: backend `ricoh' is version 1.0.0
[dll] load: searching backend `qcam' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-qcam.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-qcam.so.1'
[dll] init: initializing backend `qcam'
[dll] init: backend `qcam' is version 1.0.0
[dll] load: searching backend `plustek' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-plustek.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-plustek.so.1'
[dll] init: initializing backend `plustek'
[dll] init: backend `plustek' is version 1.0.0
[dll] load: searching backend `pie' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-pie.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-pie.so.1'
[dll] init: initializing backend `pie'
[dll] init: backend `pie' is version 1.0.9
[dll] load: searching backend `niash' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-niash.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-niash.so.1'
[dll] init: initializing backend `niash'
[dll] init: backend `niash' is version 1.0.1
[dll] load: searching backend `nec' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-nec.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-nec.so.1'
[dll] init: initializing backend `nec'
[dll] init: backend `nec' is version 1.0.0
[dll] load: searching backend `mustek_usb2' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-mustek_usb2.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-mustek_usb2.so.1'
[dll] init: initializing backend `mustek_usb2'
[dll] init: backend `mustek_usb2' is version 1.0.10
[dll] load: searching backend `mustek_usb' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-mustek_usb.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-mustek_usb.so.1'
[dll] init: initializing backend `mustek_usb'
[dll] init: backend `mustek_usb' is version 1.0.18
[dll] load: searching backend `mustek' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-mustek.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-mustek.so.1'
[dll] init: initializing backend `mustek'
[dll] init: backend `mustek' is version 1.0.138
[dll] load: searching backend `microtek2' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-microtek2.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-microtek2.so.1'
[dll] init: initializing backend `microtek2'
[dll] init: backend `microtek2' is version 1.0.0
[dll] load: searching backend `microtek' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-microtek.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-microtek.so.1'
[dll] init: initializing backend `microtek'
[dll] init: backend `microtek' is version 1.0.0
[dll] load: searching backend `matsushita' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-matsushita.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-matsushita.so.1'
[dll] init: initializing backend `matsushita'
[dll] init: backend `matsushita' is version 1.0.7
[dll] load: searching backend `ma1509' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-ma1509.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-ma1509.so.1'
[dll] init: initializing backend `ma1509'
[dll] init: backend `ma1509' is version 1.0.3
[dll] load: searching backend `lexmark' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-lexmark.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-lexmark.so.1'
[dll] init: initializing backend `lexmark'
[dll] init: backend `lexmark' is version 1.0.0
[dll] load: searching backend `leo' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-leo.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-leo.so.1'
[dll] init: initializing backend `leo'
[dll] init: backend `leo' is version 1.0.11
[dll] load: searching backend `ibm' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-ibm.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-ibm.so.1'
[dll] init: initializing backend `ibm'
[dll] init: backend `ibm' is version 1.0.0
[dll] load: searching backend `hp5400' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-hp5400.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-hp5400.so.1'
[dll] init: initializing backend `hp5400'
[dll] init: backend `hp5400' is version 1.0.3
[dll] load: searching backend `hp4200' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-hp4200.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-hp4200.so.1'
[dll] init: initializing backend `hp4200'
[dll] init: backend `hp4200' is version 1.0.0
[dll] load: searching backend `hpsj5s' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-hpsj5s.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-hpsj5s.so.1'
[dll] init: initializing backend `hpsj5s'
[dll] init: backend `hpsj5s' is version 1.0.3
[dll] load: searching backend `hp' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-hp.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-hp.so.1'
[dll] init: initializing backend `hp'
[dll] init: backend `hp' is version 1.0.8
[dll] load: searching backend `gt68xx' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-gt68xx.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-gt68xx.so.1'
[dll] init: initializing backend `gt68xx'
[dll] init: backend `gt68xx' is version 1.0.79
[dll] load: searching backend `genesys' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-genesys.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-genesys.so.1'
[dll] init: initializing backend `genesys'
[dll] init: backend `genesys' is version 1.0.8
[dll] load: searching backend `fujitsu' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-fujitsu.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-fujitsu.so.1'
[dll] init: initializing backend `fujitsu'
[dll] init: backend `fujitsu' is version 1.0.0
[dll] load: searching backend `epson' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-epson.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-epson.so.1'
[dll] init: initializing backend `epson'
[dll] init: backend `epson' is version 1.0.245
[dll] load: searching backend `dmc' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-dmc.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-dmc.so.1'
[dll] init: initializing backend `dmc'
[dll] init: backend `dmc' is version 1.0.0
[dll] load: searching backend `coolscan2' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-coolscan2.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-coolscan2.so.1'
[dll] init: initializing backend `coolscan2'
[dll] init: backend `coolscan2' is version 1.0.0
[dll] load: searching backend `coolscan' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-coolscan.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-coolscan.so.1'
[dll] init: initializing backend `coolscan'
[dll] init: backend `coolscan' is version 1.0.0
[dll] load: searching backend `canon630u' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-canon630u.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-canon630u.so.1'
[dll] init: initializing backend `canon630u'
[dll] init: backend `canon630u' is version 1.0.1
[dll] load: searching backend `canon' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-canon.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-canon.so.1'
[dll] init: initializing backend `canon'
[dll] init: backend `canon' is version 1.0.0
[dll] load: searching backend `bh' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-bh.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-bh.so.1'
[dll] init: initializing backend `bh'
[dll] init: backend `bh' is version 1.0.4
[dll] load: searching backend `as6e' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-as6e.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-as6e.so.1'
[dll] init: initializing backend `as6e'
[dll] load: searching backend `artec_eplus48u' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-artec_eplus48u.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-artec_eplus48u.so.1'
[dll] init: initializing backend `artec_eplus48u'
[dll] init: backend `artec_eplus48u' is version 1.0.0
[dll] load: searching backend `artec' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-artec.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-artec.so.1'
[dll] init: initializing backend `artec'
[dll] init: backend `artec' is version 1.0.0
[dll] load: searching backend `avision' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-avision.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-avision.so.1'
[dll] init: initializing backend `avision'
[dll] init: backend `avision' is version 1.0.182
[dll] load: searching backend `apple' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-apple.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-apple.so.1'
[dll] init: initializing backend `apple'
[dll] init: backend `apple' is version 1.0.0
[dll] load: searching backend `agfafocus' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-agfafocus.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-agfafocus.so.1'
[dll] init: initializing backend `agfafocus'
[dll] init: backend `agfafocus' is version 1.0.0
[dll] load: searching backend `abaton' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-abaton.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-abaton.so.1'
[dll] init: initializing backend `abaton'
[dll] init: backend `abaton' is version 1.0.0
[dll] load: searching backend `net' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-net.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-net.so.1'
[dll] init: initializing backend `net'
[dll] init: backend `net' is version 1.0.17
[dll] sane_get_devices: found 0 devices
[dll] sane_exit: exiting
[dll] sane_exit: calling backend `v4l's exit function
[dll] sane_exit: calling backend `umax1220u's exit function
[dll] sane_exit: calling backend `umax's exit function
[dll] sane_exit: calling backend `u12's exit function
[dll] sane_exit: calling backend `teco3's exit function
[dll] sane_exit: calling backend `teco2's exit function
[dll] sane_exit: calling backend `teco1's exit function
[dll] sane_exit: calling backend `tamarack's exit function
[dll] sane_exit: calling backend `sp15c's exit function
[dll] sane_exit: calling backend `snapscan's exit function
[dll] sane_exit: calling backend `sm3840's exit function
[dll] sane_exit: calling backend `sm3600's exit function
[dll] sane_exit: calling backend `sharp's exit function
[dll] sane_exit: calling backend `sceptre's exit function
[dll] sane_exit: calling backend `s9036's exit function
[dll] sane_exit: calling backend `ricoh's exit function
[dll] sane_exit: calling backend `qcam's exit function
[dll] sane_exit: calling backend `plustek's exit function
[dll] sane_exit: calling backend `pie's exit function
[dll] sane_exit: calling backend `niash's exit function
[dll] sane_exit: calling backend `nec's exit function
[dll] sane_exit: calling backend `mustek_usb2's exit function
[dll] sane_exit: calling backend `mustek_usb's exit function
[dll] sane_exit: calling backend `mustek's exit function
[dll] sane_exit: calling backend `microtek2's exit function
[dll] sane_exit: calling backend `microtek's exit function
[dll] sane_exit: calling backend `matsushita's exit function
[dll] sane_exit: calling backend `ma1509's exit function
[dll] sane_exit: calling backend `lexmark's exit function
[dll] sane_exit: calling backend `leo's exit function
[dll] sane_exit: calling backend `ibm's exit function
[dll] sane_exit: calling backend `hp5400's exit function
[dll] sane_exit: calling backend `hp4200's exit function
[dll] sane_exit: calling backend `hpsj5s's exit function
[dll] sane_exit: calling backend `hp's exit function
[dll] sane_exit: calling backend `gt68xx's exit function
[dll] sane_exit: calling backend `genesys's exit function
[dll] sane_exit: calling backend `fujitsu's exit function
[dll] sane_exit: calling backend `epson's exit function
[dll] sane_exit: calling backend `dmc's exit function
[dll] sane_exit: calling backend `coolscan2's exit function
[dll] sane_exit: calling backend `coolscan's exit function
[dll] sane_exit: calling backend `canon630u's exit function
[dll] sane_exit: calling backend `canon's exit function
[dll] sane_exit: calling backend `bh's exit function
[dll] sane_exit: calling backend `artec_eplus48u's exit function
[dll] sane_exit: calling backend `artec's exit function
[dll] sane_exit: calling backend `avision's exit function
[dll] sane_exit: calling backend `apple's exit function
[dll] sane_exit: calling backend `agfafocus's exit function
[dll] sane_exit: calling backend `abaton's exit function
[dll] sane_exit: calling backend `net's exit function
[dll] sane_exit: finished
```

---

### Post by moshuptrail on 2006-12-30
Here's an interesting diagnostic I found...

```

$ cat /proc/bus/usb/devices
<snip>
T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=03f0 ProdID=0f11 Rev= 1.00
S:  Manufacturer=Hewlett-Packard
S:  Product=OfficeJet V40
S:  SerialNumber=MY16QB30YRWN
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  2mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=07(print) Sub=01 Prot=03 Driver=usblp
E:  Ad=01(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:  If#= 0 Alt= 1 #EPs= 2 Cls=07(print) Sub=01 Prot=02 Driver=usblp
E:  Ad=01(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
I:  If#= 0 Alt= 2 #EPs= 1 Cls=07(print) Sub=01 Prot=01 Driver=usblp
E:  Ad=01(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
<snip>

```

Which shows the vendor ID and the product ID of the printer/scanner.  So why can't scanimage find it?

---

