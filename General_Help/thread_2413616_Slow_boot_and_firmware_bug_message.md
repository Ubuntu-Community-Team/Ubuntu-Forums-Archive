---
title: "Slow boot and firmware bug message"
date: 2019-02-27
forum: General Help
---

### Post by caterhamfan on 2019-02-27
Hello,

On booting into Ubuntu 18.04 I am faced with slow boot times and a firmware bug message (see attached image). I recently upgraded from 16.04 and the problem was also occurring in that version as well.

Any ideas what this could be?

[ATTACH=CONFIG]282657[/ATTACH][ATTACH=CONFIG]282658[/ATTACH]

Thank you,

---

### Post by caterhamfan on 2019-03-04
Anyone able to help with this?

Thank you,

---

### Post by oldfred on 2019-03-04
What brand/model system?
What video card/chip?

Have you updated UEFI from vendor?
       Almost all systems need that, anyway, for mitigation of Meltdown and Spectre CPU vulnerabilities from cpu speculative execution and caching.  
    
Not sure TPM is issue unless it just is that UEFI is not updated.

 UEFI secure boot doesn't have anything to do with a TPM.
[https://www.ibm.com/developerworks/community/blogs/smartersecurity/entry/uefi_secure_boot_and_the_tpm20?lang=en](https://www.ibm.com/developerworks/community/blogs/smartersecurity/entry/uefi_secure_boot_and_the_tpm20?lang=en)
Microsoft has announced that from January 1, 2015 all computers will have to be equipped with a TPM 2.0 module in order to pass Windows 8.1 hardware certification.
[https://en.wikipedia.org/wiki/Trusted_Platform_Module](https://en.wikipedia.org/wiki/Trusted_Platform_Module)
Re: certificate to verify signature of Ubuntu kernel 
[http://ubuntuforums.org/showthread.php?t=2259248](http://ubuntuforums.org/showthread.php?t=2259248)
Older computer without TPM
GRUB_CMDLINE_LINUX_DEFAULT="tpm_tis.force=1"

---

