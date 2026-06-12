---
title: "Thinkpad 450S Video Driver"
date: 2016-09-15
forum: General Help
---

### Post by makitso on 2016-09-15
Currently on 16.04 and having just a lot of video issues with Libreoffice.  However, there is a strange thing;  On 16.04, a lspci shows the following for the video driver with a clean install.

Intel Corporation Broadwell-U Integrated Graphics (rev 09)

This driver gives cell corruption in Libreoffice calc.

However, if I load up xubuntu 16.10, the lspci shows it using Intel Corporation HD Graphics 5500 (rev 09) as the video driver.  And, the libreoffice calc problem no longer exists.

Questions:

Why the difference?
Is there a way to install the HD Graphics driver on 16.04?

---

### Post by cariboo on 2016-09-15
You'll probably get help quicker here.

---

### Post by Bucky Ball on 2016-09-15
You don't need to install an unsupported, unreleased Ubuntu to do this, in fact, I'd advise against that. You can install the mainline kernel or the kernel that you know works for your card.

See [some of the answers here]("http://askubuntu.com/questions/119080/how-to-update-kernel-to-the-latest-mainline-version-without-any-distro-upgrade"). First answer looks promising. It's pretty straightforward.

Find the kernel that the working 16.10 is using then locate and install that from the mainline kernels. Reboot and select that kernel from the grub options.

---

### Post by makitso on 2016-09-16
Tried both 4.5 and 4.6 kernels but they still use the Intel Corporation Broadwell-U Integrated Graphics (rev 09).  What I want is to use the Intel Corporation HD Graphics 5500 (rev 09).  How do I do this?

---

