---
title: "HAL mount options"
date: 2008-05-23
forum: General Help
---

### Post by n-alexander on 2008-05-23
I want to add utf8 option for NTFS in HAL config files. Where do I look for the files?

Thanks,
Alex

---

### Post by nick_h on 2008-05-23
There is a configuration file called /etc/hal/fdi/policy/preferences.fdi
There are also some fdi files under the directory /usr/share/hal/fdi

You may also want to read the [HAL Specification](http://people.freedesktop.org/~david/hal-spec/hal-spec.html).

---

### Post by NT4usB on 2008-05-23
Great link nick_h. I've been struggling with hot swapping external SATA disks. From the looks of this, simply restarting the HAL daemon might solve it!

---

### Post by n-alexander on 2008-05-24
> **nick_h said:**
> There is a configuration file called /etc/hal/fdi/policy/preferences.fdi
There are also some fdi files under the directory /usr/share/hal/fdi

You may also want to read the [HAL Specification](http://people.freedesktop.org/~david/hal-spec/hal-spec.html).

thanks

---

### Post by n-alexander on 2008-07-17
> **nick_h said:**
> There is a configuration file called /etc/hal/fdi/policy/preferences.fdi
There are also some fdi files under the directory /usr/share/hal/fdi

You may also want to read the [HAL Specification](http://people.freedesktop.org/~david/hal-spec/hal-spec.html).

in /usr/share/hal/fdi/policy/10osvendor/20-storage-methods.fdi:

```
      <!-- allow these mount options for ntfs -->
      <match key="volume.fstype" string="ntfs">
	<match key="/org/freedesktop/Hal/devices/computer:system.kernel.name" string="Linux">
	  <append key="volume.mount.valid_options" type="strlist">uid=</append>
	  <append key="volume.mount.valid_options" type="strlist">gid=</append>
	  <append key="volume.mount.valid_options" type="strlist">umask=</append>
	  <append key="volume.mount.valid_options" type="strlist">locale=</append>
	  <append key="volume.mount.valid_options" type="strlist">utf8</append>
	</match>
```

Which looks like it should be UTF8 already. Still, if I let HAL mount an NTFS disk, no UTF8 support. If I mount manually with utf8 option from fstab - everything's fine. WHy??

---

