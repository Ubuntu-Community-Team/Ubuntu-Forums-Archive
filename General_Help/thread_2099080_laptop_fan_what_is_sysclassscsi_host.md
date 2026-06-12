---
title: "laptop fan: what is /sys/class/scsi_host ?"
date: 2012-12-28
forum: General Help
---

### Post by rpm13 on 2012-12-28
I have a new Dell Inspiron 5520 on which Ive put Ubuntu 12.10

The fan goes like mad -- more so when I connect an external projector

I read somewhere that
```

echo "min_power" | sudo tee /sys/class/scsi_host/host*/link_power_management_policy

```
reduces the fan.

I tried it and it does.

But I am not sure its a good idea.
If its reducing the heating then its good
If its reducing the fan without reducing the heating its BAD

---

### Post by rnerwein on 2012-12-28
> **rpm13 said:**
> I have a new Dell Inspiron 5520 on which Ive put Ubuntu 12.10

The fan goes like mad -- more so when I connect an external projector

I read somewhere that
```

echo "min_power" | sudo tee /sys/class/scsi_host/host*/link_power_management_policy

```reduces the fan.

I tried it and it does.

But I am not sure its a good idea.
If its reducing the heating then its good
If its reducing the fan without reducing the heating its BAD
hi
watch the temperatur using sensors to figure out if it works correct.
by the side why the "tee" command.
just: sudo echo min_power > //sys/class/scsi_host/host*/link_power_management_polycy
but i can't guarantee that this file is only for the fan !?
cheers

---

