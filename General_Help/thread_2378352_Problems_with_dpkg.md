---
title: "Problems with dpkg"
date: 2017-11-22
forum: General Help
---

### Post by Nigel_Pain on 2017-11-22
I've had problems updating Libreoffice on Ubuntu 14.04.05. When apt-get install is run it returns the following message for libreoffice-common:

```
Unpacking libreoffice-common (1:4.2.8-0ubuntu5.2) ...
dpkg: error processing archive /var/cache/apt/archives/libreoffice-common_1%3a4.2.8-0ubuntu5.2_all.deb (--unpack):
 unable to open '/usr/lib/libreoffice/share/gallery/sg36.sdg.dpkg-new': Operation not permitted

```

This stops the other Libreoffice packages from being configured because of their dependency on libreoffice-common. I've tried running apt-get clean libreoffice-common but this makes no difference.

A similar thing happened on another machine with the perl-base package, despite other machines updating OK from the same repository mirror.

Is there any way to find out what's going wrong with dpkg?

Thanks.

---

### Post by DuckHook on 2017-11-22
You don't seem to be alone. This launchpad bug report is likely a similar item: [https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1691693](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1691693)
If possible, please add your confirmation to the bug report, but note that yours is on Trusty.

[LIST=1]
[*]Have you tried purging LibreOffice altogether, then reinstalling?
[*]Try changing to a different mirror.
[*]Consider moving to Xenial. You could try LibreOffice out on a LiveUSB first.
[/LIST]

---

### Post by Nigel_Pain on 2017-11-23
thanks for your response. I've added my two-penn'orth to the bug report.
1. I tried that and got exactly the same problem.
2. Not an option, unfortunately. Sat behind a firewall and proxy. Only our internal mirror server is able to get through, and only to gb.archive.ubuntu.com.
3. Xenial's on the list, but we have half a dozen or so machines, all fairly recently upgraded to Trusty, so it's not a priority at the moment. I've not come across LiveUSB before but our machines are VMs in a large VMware infrastructure so not sure it's an option.

---

