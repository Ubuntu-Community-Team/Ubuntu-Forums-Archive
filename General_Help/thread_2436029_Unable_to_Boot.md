---
title: "Unable to Boot"
date: 2020-01-30
forum: General Help
---

### Post by physics2014 on 2020-01-30
Hi everybody, I am a relatively new linux user and it is the first time posting here on the forum. I am unable to boot my computer and the only thing that boots is the Lenovo Help Center to reset to Factory settings my pc. I have been using Ubuntu LTS 18.04 without any problem for an year or so but after I decided to delete the Windows Partition using the OS-Uninstaller tool the system doesn't boot anymore. The only way I can boot it is thanks to a USB-Drive with Linux Mint on it. Thanks to this I can also access all my previous files and it allows me to check that the Ubuntu partition is still alive even though it doesn't boot.
I, following, some infos found on the forum used the Boot Repair tool but I am unable to interpret the results. Can someone help me?


Edit: I can also post the report coming from the Boot Repair Tool if necessary.
Edit2: [http://paste.ubuntu.com/p/TSW7zhzGZx/](http://paste.ubuntu.com/p/TSW7zhzGZx/)  This is the report coming from Boot Repair

---

### Post by CelticWarrior on 2020-01-30
Please post the Boot Repair report. Without it we can only give general advice like:

[LIST]
[*]"OS uninstaller" is an aberration that shouldn't exist. OSes do not need to be "uninstalled" in any way, shape or form.
[*]If you intended to remove Windows all you had to do was delete or reuse the Windows system partition.
[*]The stupid tool you used (read first point) very likely deleted the ESP (EFI System Partition) from where both OSes booted.
[/LIST]

---

### Post by physics2014 on 2020-01-30
Yeah I unknowingly came to the same conclusion. I am going to post the report at the second edit. Thanks

---

