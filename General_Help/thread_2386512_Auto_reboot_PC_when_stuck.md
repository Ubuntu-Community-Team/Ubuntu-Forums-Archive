---
title: "Auto reboot PC when stuck"
date: 2018-03-06
forum: General Help
---

### Post by bizhat on 2018-03-06
My PC some stop working (display get distorted, won't respond to mouse/keyboard) with following error in syslog

```

Mar  7 07:56:28 hon-pc-01 dbus[988]: [system] Activating via systemd: service name='org.bluez' unit='dbus-org.bluez.service'
Mar  7 07:56:53 hon-pc-01 kernel: [  390.306117] perf interrupt took too long (2688 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
Mar  7 07:57:54 hon-pc-01 kernel: [  450.843492] NVRM: GPU at PCI:0000:03:00: GPU-e1c069dd-4adf-9be1-da0a-87c4a72ed9fa
Mar  7 07:57:54 hon-pc-01 kernel: [  450.843497] NVRM: Xid (PCI:0000:03:00): 62, 1504(1758) 04000aab a5a5a5a5
Mar  7 07:57:58 hon-pc-01 kernel: [  454.839942] NVRM: Xid (PCI:0000:03:00): 31, Ch 00000020, engmask 00000101, intr 10000000
Mar  7 07:57:58 hon-pc-01 kernel: [  455.344306] NVRM: Xid (PCI:0000:03:00): 13, Graphics Exception: Shader Program Header 1 Error
Mar  7 07:57:58 hon-pc-01 kernel: [  455.344314] NVRM: Xid (PCI:0000:03:00): 13, Graphics Exception: Shader Program Header 2 Error
Mar  7 07:57:58 hon-pc-01 kernel: [  455.344318] NVRM: Xid (PCI:0000:03:00): 13, Graphics Exception: Shader Program Header 3 Error
Mar  7 07:57:58 hon-pc-01 kernel: [  455.344322] NVRM: Xid (PCI:0000:03:00): 13, Graphics Exception: Shader Program Header 4 Error
Mar  7 07:57:58 hon-pc-01 kernel: [  455.344326] NVRM: Xid (PCI:0000:03:00): 13, Graphics Exception: Shader Program Header 5 Error
Mar  7 07:57:58 hon-pc-01 kernel: [  455.344330] NVRM: Xid (PCI:0000:03:00): 13, Graphics Exception: Shader Program Header 6 Error
Mar  7 07:57:58 hon-pc-01 kernel: [  455.344334] NVRM: Xid (PCI:0000:03:00): 13, Graphics Exception: Shader Program Header 7 Error
Mar  7 07:57:58 hon-pc-01 kernel: [  455.344338] NVRM: Xid (PCI:0000:03:00): 13, Graphics Exception: Shader Program Header 8 Error
Mar  7 07:57:58 hon-pc-01 kernel: [  455.344342] NVRM: Xid (PCI:0000:03:00): 13, Graphics Exception: Shader Program Header 9 Error
Mar  7 07:57:58 hon-pc-01 kernel: [  455.344346] NVRM: Xid (PCI:0000:03:00): 13, Graphics Exception: Shader Program Header 10 Error
Mar  7 07:57:58 hon-pc-01 kernel: [  455.344350] NVRM: Xid (PCI:0000:03:00): 13, Graphics Exception: Shader Program Header 11 Error
Mar  7 07:57:58 hon-pc-01 kernel: [  455.344354] NVRM: Xid (PCI:0000:03:00): 13, Graphics Exception: Shader Program Header 12 Error
Mar  7 07:57:58 hon-pc-01 kernel: [  455.344359] NVRM: Xid (PCI:0000:03:00): 13, Graphics Exception: Shader Program Header 13 Error
Mar  7 07:57:58 hon-pc-01 kernel: [  455.344363] NVRM: Xid (PCI:0000:03:00): 13, Graphics Exception: Shader Program Header 14_ERR
Mar  7 07:57:58 hon-pc-01 kernel: [  455.344367] NVRM: Xid (PCI:0000:03:00): 13, Graphics Exception: Shader Program Header 15_ERR
Mar  7 07:57:58 hon-pc-01 kernel: [  455.344371] NVRM: Xid (PCI:0000:03:00): 13, Graphics Exception: Shader Program Header 16 Error
Mar  7 07:57:58 hon-pc-01 kernel: [  455.344375] NVRM: Xid (PCI:0000:03:00): 13, Graphics Exception: Shader Program Header 17 Error
Mar  7 07:57:58 hon-pc-01 kernel: [  455.344379] NVRM: Xid (PCI:0000:03:00): 13, Graphics Exception: Shader Program Header 18 Error
Mar  7 07:57:58 hon-pc-01 kernel: [  455.344383] NVRM: Xid (PCI:0000:03:00): 13, Graphics Exception: Shader Program Header 19 Error
Mar  7 07:57:58 hon-pc-01 kernel: [  455.344387] NVRM: Xid (PCI:0000:03:00): 13, Graphics Exception: Shader Program Header 20 Error
Mar  7 07:57:58 hon-pc-01 kernel: [  455.344391] NVRM: Xid (PCI:0000:03:00): 13, Graphics Exception: Shader Program Header 21 Error
Mar  7 07:57:58 hon-pc-01 kernel: [  455.344398] NVRM: Xid (PCI:0000:03:00): 13, Graphics Exception: ESR 0x405840=0xbf3ffffe
Mar  7 07:57:58 hon-pc-01 kernel: [  455.344409] NVRM: Xid (PCI:0000:03:00): 13, Graphics MME Exception Type:  MAX_INSTR_LIMIT
Mar  7 07:57:58 hon-pc-01 kernel: [  455.344418] NVRM: Xid (PCI:0000:03:00): 13, Graphics Exception: ESR 0x404490=0x80000010
Mar  7 07:57:58 hon-pc-01 kernel: [  455.344459] NVRM: Xid (PCI:0000:03:00): 13, Graphics Exception: ChID 0008, Class 0000b097, Offset 00000000, Data 00000000
Mar  7 07:58:03 hon-pc-01 kernel: [  459.851215] NVRM: Xid (PCI:0000:03:00): 56, CMDre 00000001 00000094 00010066 00000004 0000000e
Mar  7 07:58:03 hon-pc-01 kernel: [  459.851244] NVRM: Xid (PCI:0000:03:00): 56, CMDre 00000001 000000c0 00010062 00000004 00000004
Mar  7 07:58:07 hon-pc-01 kernel: [  463.851544] NVRM: Xid (PCI:0000:03:00): 38, 0010 00000000 00000000 00000000 00000000 00000000
Mar  7 07:58:12 hon-pc-01 anacron[962]: Job `cron.daily' terminated
Mar  7 07:58:12 hon-pc-01 anacron[962]: Normal exit (1 job run)
Mar  7 07:58:19 hon-pc-01 kernel: [  475.863043] NVRM: Xid (PCI:0000:03:00): 31, Ch 0000000a, engmask 00000101, intr 10000000
Mar  7 07:58:52 hon-pc-01 kernel: [  508.877227] nvidia-modeset: WARNING: GPU:0: Lost display notification (0:0x00000000); continuing.

```

Since i don't have display and keyboard reboot won't work, i have to  power off PC and power on.

Is there any software that i can install to monitor syslog and reboot PC when this happens ?

---

### Post by yetimon_64 on 2018-03-07
I have never heard of such software but a keyboard combination exists for when this happens. You can safely force the system down and reboot using a keyboard combination even though the keyboard may not seem to be responding. The alt/print-screen "magic" key combination usually will still work when the keyboard seems frozen.

To use the combination, with your right hand (thumb and little finger) hold down the right "alt" key and the "print screen" key and keep these two keys held down through the whole procedure. With your left hand **press and hold down for three seconds** each the following keys in succession (notes beside the letter will give you an idea what they are doing) ...

"R" ... **r**eset/release the keyboard.
"S"  ... **s**ynchronize any outstanding data to disk.
"E" ... **e**xit any current running process.
"I" ... k**i**ll forcibly any process that fails to exit.
"S"  ... **s**ynchronize any outstanding data to disk.
"U" ... **u**nmount all filesystems
"B" ... re**b**oot the system.

Remember to hold each key for a count of 3 before moving to the next. There is a mnemonic to help in remembering the above key combination, it is ...
> **R**aising **S**kinny **E**lephants **I**s **S**o **U**tterly **B**oring.

After holding the final "B" key down for a few seconds the screen should go black and a reboot should happen. Using the above combination will help prevent any system data corruption from a hard reboot. 

Some people drop the first "S" key in the above combination, I am in the habit of using it as a result of learning the above mnemonic when I first started using Linux. So you may sometimes see it mentioned as "REISUB" however both have exactly the same effect overall.

Regards, yeti.

---

