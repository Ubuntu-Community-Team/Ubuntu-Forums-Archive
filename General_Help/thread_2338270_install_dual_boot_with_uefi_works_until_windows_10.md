---
title: "install dual boot with uefi works until windows 10 restarted"
date: 2016-09-26
forum: General Help
---

### Post by d.coli on 2016-09-26
I've been using Ubuntu for years, but rarely peek under the hood. Lately I was humming along on my Dell XPS 15 with Ubuntu 16.04, and with Windows 10 hibernated and largely untouched. Worked in Ubuntu using Remmina to access my work servers for a few days. When I had to get back into Windows for a full-screen photo slideshow I was prompted to do a Windows Update, which I did and restarted. The next time I attempted to boot into Linux I got a kernal panic and something about could not sync, and maybe something about mounting the filesystem? (I don't remember exactly what it said.) 

Is anyone familiar with this? I installed from a USB key with uefi support, but I think when I installed it the only way I could get it to work was in legacy boot mode in the bios (or whatever the uefi system settings are called). Perhaps Windows "fixed" the boot and overwrote something about the Linux boot when it restarted? Any way I can fix this without reinstalling Linux and losing my personal Linux files and Remmina profiles?

Thanks in advance.

---

### Post by oldfred on 2016-09-26
May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

