---
title: "What happened to the ISO images prior to version 20.04.2?"
date: 2021-07-04
forum: General Help
---

### Post by ccj88 on 2021-07-04
Hello everyone:

From some time to this part (I can't precise how much) ONLY the latest "LTS" 20.04.2 version of Ubuntu and its respective flavors can be downloaded. All traces of version 20.04.1 or 20.04, which may be preferable for many users due to hardware, support and kernel issues, have disappeared from all mirrors.

Can anyone tell me what has happened? I have searched and found no answers anywhere.

Thanks,

César

---

### Post by deadflowr on 2021-07-04
Here:
[https://old-releases.ubuntu.com/releases/focal/]("https://old-releases.ubuntu.com/releases/focal/")
Scroll down until you find the ISO you want.
20.04 and 20.04.1 are considered old releases now, so the images were moved to the old-releases archives.

---

### Post by mikewhatever on 2021-07-04
Here you go: [http://old-releases.ubuntu.com/releases/focal/](http://old-releases.ubuntu.com/releases/focal/).

Whatever happened, one can't expect ISOs hosted forever. Sooner or later, they are removed.

---

### Post by Impavidus on 2021-07-04
The reason why you may want the 20.04 or 20.04.1 image is that you may want the older 5.4 kernel, supported until April 2025, instead of the HWE kernel, which will give you 5.8 or soon 5.11 and will require upgrades until you get the same kernel as 22.04. If so, make sure you don't get the HWE kernel metapackage. Standard Ubuntu installs the HWE metapackage even when you install from the 20.04 or 20.04.1 livedisk. That will install the 5.8 kernel the first time you install any upgrades, so make sure you install the regular kernel metapackage and remove the HWE kernel metapackage before running the first upgrades. This may not apply to all flavours.

---

### Post by grahammechanical on 2021-07-04
You should read about the BootHole security vulnerability. It and several other security vulnerabilities in the Grub boot loader have been fixed. But the boot loader in existing Ubuntu ISO images could not be replaced. So, those ISO images should not be used.

[https://ubuntu.com/blog/mitigating-boothole-theres-a-hole-in-the-boot-cve-2020-10713-and-related-vulnerabilities](https://ubuntu.com/blog/mitigating-boothole-theres-a-hole-in-the-boot-cve-2020-10713-and-related-vulnerabilities)

> As mentioned earlier, these shim and GRUB2 binaries are also used on the  various installation media to ensure they can be booted when UEFI  Secure Boot is enabled. These old install media would then always be  trusted, even though they contain this vulnerable version of GRUB2 and  hence could be used to bypass UEFI Secure Boot on any system.

Regards

---

