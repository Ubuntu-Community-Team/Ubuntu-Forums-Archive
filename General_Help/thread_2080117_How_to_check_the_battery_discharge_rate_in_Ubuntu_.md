---
title: "How to check the battery discharge rate in Ubuntu 12.10"
date: 2012-11-03
forum: General Help
---

### Post by ksprasad on 2012-11-03
Hi,

I have a Dell xps with Ubuntu 12.10 on which I have installed bumblebee 3.0.
I want to check the discharge rate of my battery.

In Ubuntu 12.04, I was able to check it using below command.
```
watch grep rate /proc/acpi/battery/BAT0/state
```

But in Ubuntu 12.10, there is no battery directory inside /proc/acpi/ 

Can somebody please let me know how to see the discharge rate of my battery?

Thanks in advance :)

Regards,
ksprasad

---

### Post by Bliepo32 on 2012-11-03
I believe clicking the battery icon in the upper bar should work, but if it doesn't, you could try using powertop. You can run it from the terminal by typing powertop. Off course you'll need to install it first. It will also gives you options to save some more power as an added bonus.

---

### Post by ksprasad on 2012-11-03
Hi,

Yes, powertop works well. Looks like a good tool. Thanks a lot :)

Regards,
ksprasad

---

