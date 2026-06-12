---
title: "Troubleshooting system crash with"
date: 2008-05-14
forum: General Help
---

### Post by stevenrnelson on 2008-05-14
I've had some puzzling lockups happen with my Hardy install. The system becomes completely unresponsive. There is no blinking from the caps lock and num lock keys, but neither is there a response to ctrl-alt-f# or the ctrl+alt+del. The mouse still moves, so I don't think it's a problem with the input hardware. I've tried looking around in /var/logs, but I really don't know what I'm looking for except for a glaring "ERROR" that I haven't found yet. The system locks up so tight, all I can do to remedy is to hold the power button down until it cuts the power.
Also, there doesn't seem to be any specific behavior that triggers this. I am using the ATI and Broadcom restricted drivers. The system is an Acer Ferrari with an AMD Turion. I never seemed to have this problem with 7.10.
So I guess my question is, where do I start looking for the cause of this? What logs should I be checking? What kind of tests can I do to narrow down the problem?

---

### Post by stevenrnelson on 2008-05-21
Well, it's happened again, but this time I have more information. When it crashed, I was using a virtual terminal. The system dumped a screen full of information, repeating the same message over and over about once every hundredth of a second. Here is the message, each time it printed, the only difference in each message was the time stamp:
[2595.268904] BUG: soft lockup - CPU#0 stuck for 11s![swapper:0]

I know it simply says the cpu locked up, but does anyone know what prints this error? And if so, does anyone know what to do about it? Some googling suggests something to do with the kernel and a nohz feature, but that's a little over my head.

---

