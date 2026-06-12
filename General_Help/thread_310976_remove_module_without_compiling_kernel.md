---
title: "remove module without compiling kernel"
date: 2006-12-02
forum: General Help
---

### Post by chocorem on 2006-12-02
Hi,

I would like to know if there is a way definitively NOT to load a module at startup.

I have a sony Laptop and it load the ibm_acpi, asus_acpi and some other stuff I would like not to load.

The modules are listed when I do lsmod, but I cannot find them in the modules file or the mod-utils directory.

PS the module are tagged with (M) in the kernel configuration

Thanks in advance

Regards

---

### Post by rekahsoft on 2006-12-26
```
rmmod $module_name
```module_name be obvoisly replace with the module name you would like to not load.

---

### Post by RAOF on 2006-12-26
I think that the various **/etc/modules.d/blacklist** files are what you're after.  Add your module to one of them, and they won't get loaded, ever.

---

