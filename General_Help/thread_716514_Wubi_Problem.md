---
title: "Wubi Problem"
date: 2008-03-06
forum: General Help
---

### Post by samitharansara on 2008-03-06
I downloaded the hardy 8.04 alpha version iso. When I try to install it inside windows, wubi creates the cd image and after that the installer tries to connect wubi-installer.org. It retries 5 times to get some files, but after that the installation completes and ask me to reboot.
When I reboot the machine, Ubuntu installation gives an error..!!!

I'm accessing via a proxy server.

What is the problem associated with this scenario? Can I download the files that wubi requests through installer, separately and put those files to the relevant directory and reboot the machine? 

Thanks a lot.

Best Regards,

Samitha

---

### Post by ago on 2008-03-06
The files are used to run a checksum, but they are non essential if you already have an ISO/CD. 

The error you get at boot is probably due to something else, but I cannot help much without further info.

---

### Post by samitharansara on 2008-03-06
Thanks for the quick reply. Does the installer is machine dependent? I'm asking this because I was able to install by using same ISO in another machine, but not my one (File system NTFS, OS WinXP SP2, 15G free space, 1G Ram, 3GHz HT processor)

Thank you very much...

Samitha
:confused:

---

### Post by ago on 2008-03-07
> **samitharansara said:**
> Thanks for the quick reply. Does the installer is machine dependent? I'm asking this because I was able to install by using same ISO in another machine, but not my one (File system NTFS, OS WinXP SP2, 15G free space, 1G Ram, 3GHz HT processor)

Thank you very much...

Samitha
:confused:

No wubi is not machine dependent, but bugs are...
So if you provide as much info as possible I can try to address the issue.

---

