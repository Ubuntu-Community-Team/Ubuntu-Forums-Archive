---
title: "Support for amd-v"
date: 2008-03-24
forum: General Help
---

### Post by Roger D on 2008-03-24
Hi

I'm currently running Dapper, using an Athlon 3200+, on an Asus M2NPV-VM motherboard (AM2 processor socket)

One of the features that really interests me about the forthcoming release of Hardy Heron is the support for kvm virtualisation. However, in order for this to work well I understand that I need a 2.6.16 kernel, or newer - I've kept my installation up-to-date so I'm assuming this is OK - and a processor with support for AMD's hardware extensions for virtualisation (AMD-V).

I'm sure I've read somewhere that all AM2 socket processors support AMD-V, however when I run: 

egrep '^flags.*(vmx|svm)' /proc/cpuinfo

I get no response.

Am I going to have to upgrade my processor in order to run kvm with a decent performance?

Best regards

Roger D

---

### Post by pointone on 2008-03-24
There's usually an option in the BIOS for enabling AMD-V/Intel VT support that needs to be toggled.

---

### Post by Roger D on 2008-03-24
Thanks for the response. I've had a careful look through my motherboard user guide, and can't see a thing. Not looking good.

Roger D

---

### Post by Roger D on 2008-03-26
I've checked amd-v support out with AMD, and they assure me that AM2 socket processors, like the 3200+, DO support amd-v.

Roger D

---

