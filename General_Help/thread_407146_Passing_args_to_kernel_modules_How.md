---
title: "Passing args to kernel modules: How?"
date: 2007-04-11
forum: General Help
---

### Post by medicdave on 2007-04-11
I'm running Dapper and trying to figure out how to pass an argument to one of my kernel modules when it is initially loaded. The argument enables the LED output on my Intel PRO wireless adapter.

The following works to enable the LED:

```
# sudo rmmod ipw2200
# sudo modprobe ipw2200 led=1
```

However, I would rather have the `led` argument passed to the module automatically when it is loaded at boot. Does anyone know how to do this? I tried adding a line to /etc/modules:

```
ipw2200 led=1
```

but this didn't work.

Thanks in advance,
medicDave

---

### Post by medicdave on 2007-04-12
Can anyone tell me what code is used to autoload modules at boot? I would be happy to check the documentation for this daemon, if I knew what it was!

Thanks,
Dave

---

### Post by fanatik on 2007-04-12
take a look at:
/etc/modprobe.d/options

All you should need to add is the following:

options ipw2200 led=1

ie all you missed off was the word options.
Try it, and let us know if it worked.

Regards,
James.

---

### Post by medicdave on 2007-04-12
Thanks fanatik- this is what I needed to know!

I originally found the module argument in the Gentoo forums, and the modules there are configured using /etc/modules.d - guess I just needed the Debian/Ubuntu analogue to this!

Thanks again,
Dave

---

### Post by medicdave on 2007-04-12
PS - Will try this out tonight once I get home!

---

### Post by medicdave on 2007-04-12
This works perfectly - thanks again for your assistance!

---

