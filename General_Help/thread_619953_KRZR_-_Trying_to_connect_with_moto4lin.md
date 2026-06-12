---
title: "KRZR - Trying to connect with moto4lin"
date: 2007-11-22
forum: General Help
---

### Post by u-slayer on 2007-11-22
I am trying to connect ubuntu to my new KRZR K1M

So I installed the tools:

```
apt-get install moto4lin
modprobe cdc_acm
```

I plug in the phone and tail /var/log/messages shows this:

```

kernel: [27981.800000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/cdc-acm.c: v0.25:USB Abstract Control Model driver for USB modems and ISDN adapters
kernel: [29499.852000] usb 2-2: new full speed USB device using uhci_hcd and address 6
Nov 21 23:52:30 kronos-laptop kernel: [29500.068000] usb 2-2: configuration #1 chosen from 1 choice
```

Then I ran moto4lin


Using this [guide]("http://moto4lin.sourceforge.net/wiki/KRZR_K1"), I typed in:
```
/dev/tty/ACM0
22b8
4902
22b8
4901
```

I clicked 'switch to P2K' and 'Update list' and selected the k1m. Then I hit 'set as p2k device' which changes my p2k PID from 4901 to 2a64

I can now connect to the phone. However I get these errors
```

[info] Phone connected as P2K
[error] Unable to get phone model
[error] Unable to get drive name
[error] Unable to get file count
[error] Unable to get drive name
```

This is my command line output.
```
#moto4lin
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Form1
PhoneMan
New mode: 1
P2kProc::doConnect()
New mode: 2
doActConnect
doActConnect
P2kProc::doConnect()
doActConnect
(E_getPhoneName: E001)
(E_getDriveName: E001)
(E_fileCount: E002)
(E_getDriveName: E001)
```


I can't get any farther. Can anyone help me?:confused:

I don't have a microSD card in the phone yet. Do I need one to do this kind of stuff?

---

### Post by u-slayer on 2007-11-22
Has anyone else had any success with moto4lin or the KRZR? If you have, please tell me what you did. Thanks!:)

---

### Post by jinxed on 2007-12-19
Same problem here. I have the same phone, and I get to the same point... no luck after that.

---

### Post by timcredible on 2007-12-19
moto4lin is pretty old, you might try bitpim (it's in synaptic), but doubt you'll have much luck.  unfortunately, nobody has spent time writing cellphone access programs for linux.  depending on what you want to do, you don't have to worry about it though - verizon offers a free service that backs up/restores contacts over the air, with a microSD card you can transfer files from/to your phone from a linux pc, so there's not too much else to do.

---

