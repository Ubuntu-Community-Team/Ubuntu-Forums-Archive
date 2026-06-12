---
title: "Kaffeine 8.1 crash"
date: 2006-08-31
forum: General Help
---

### Post by tagbre on 2006-08-31
I can't start it, here's the output:

Main: XInitThreads()
[INFO] If Kaffeine hangs here run 'configure --with-xinit-workaround' and recompile/reinstall.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
/dev/dvb/adapter0/frontend0 : : No such file or directory
kaffeine: No DVB device found.
kio (KSycoca): Trying to open ksycoca from /var/tmp/kdecache-tom/ksycoca
kio (KTrader): KServiceTypeProfile::offers serviceType=audio/x-mp3 genericServiceType=Application
kio (KTrader): KServiceTypeProfile::offers serviceType=audio/x-mp3 genericServiceType=KParts/ReadOnlyPart
kio (KTrader): query for audio/x-mp3 : returning 1 offers
kio (KTrader): KServiceTypeProfile::offers serviceType=audio/x-mp3 genericServiceType=Application
kio (KTrader): KServiceTypeProfile::offers serviceType=audio/x-mp3 genericServiceType=KParts/ReadOnlyPart
kio (KTrader): query for audio/x-mp3 : returning 1 offers
kaffeine: WizardDialog: got from hdparm:
/dev/dvd:
 using_dma    =  1 (on)
kaffeine:
/dev/dvb/adapter0/frontend0 : : No such file or directory
KCrash: crashing... crashRecursionCounter = 2
KCrash: Application Name = kaffeine path = <unknown> pid = 6746
ERROR: Communication problem with kaffeine, it probably crashed.
tom@tom-desktop:~$

---

