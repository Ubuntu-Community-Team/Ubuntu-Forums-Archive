---
title: "[SOLVED] [vmware] Permission denied as root/sudo"
date: 2008-06-25
forum: General Help
---

### Post by ashughes on 2008-06-25
Whenever I try to run vmware-config-tools.pl I get a Permission denied error.  I only get this error using Kubuntu 8.04 KDE4 Remix.  Kubuntu 7.10/8.04 using KDE3 and Ubuntu 7.10/8.04 can run vmware-config-tools with no problems.

I usually run this tool using sudo, but even if I run as root I get Permission Denied.  If I chmod 777 the tool, I get permission denied when the tool tries to turn off some of the vmware services.

This is a completely new install of Kubuntu.  After 1st login, I installed build-essential then rebooted and installed vmware-tools.

Anyone run into this or have any ideas on how I might fix this?

As much as I dislike KDE4, I need it for testing purposes.  Any help here would be greatly appreciated.

Thanks

---

### Post by kuja on 2008-06-25
Well, after you chmod 777'd it, it executed that, but some of the things it tried to do didn't behave, right? Maybe there are other things that you need to "chmod +x" to make it work properly? I'd check the vmware-config-tools.pl file to see what it references and chmod +x anything it references to see

---

### Post by ashughes on 2008-06-25
Well, the point is that I shouldn't have to chmod +x anything.  It should just work like it does on all other versions of Ubuntu I have tried (as listed in my original post).

As mentioned above, I am also getting Permission Denied errors when the script tries to shut down some of the vmware services prior to configuration.  I should not be getting these errors as sudo/root afaik.

Any more ideas?

---

### Post by ashughes on 2008-06-25
I did an ls -l on my vmware-tools-install directory and I get the following:

lrwxrwxrwx vmware-install.pl -> ./bin/vmware-uninstall-tools.pl

If I run ./vmware-install.pl, I get Permission Denied.
If I run sudo ./vmware-install.pl, I get Command Not Found

This is really weird.  KDE4 is definitely not winning me over.

---

### Post by ashughes on 2008-06-25
Ok, looks like I have it resolved.  Ark was not extracting the archive properly.  I had to extract using terminal.

I definitely would not be using KDE4 if I didn't have to use it for testing purposes.

Cheers.

---

