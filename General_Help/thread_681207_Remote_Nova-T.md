---
title: "Remote Nova-T ??"
date: 2008-01-28
forum: General Help
---

### Post by petef0_0 on 2008-01-28
Hi Guys

Bought the Nova-t 500 card recently and although I've eventually got the card working through Kaffiene, the remote doesn't show up in dmesg e.g below ?? Any ideas ?? 

pete@zeus:~$ dmesg | grep DVB
[   59.533465] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in cold state, will try to load a firmware
[   60.932918] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in cold state, will try to load a firmware
[   61.655700] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[   61.655934] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T).
[   61.769363] DVB: registering frontend 0 (DiBcom 3000MC/P)...
[   62.274854] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T).
[   62.280540] DVB: registering frontend 1 (DiBcom 3000MC/P)...
[   62.840826] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.

I know I should have a line just before the last showing the remote ?? 

Thanks in advance.

Pete

---

### Post by petef0_0 on 2008-01-29
Anyone ??

Cheers

Pete

---

