---
title: "Adding boot arguements to grub"
date: 2015-12-16
forum: General Help
---

### Post by chazzyfresh33 on 2015-12-16
I'm trying to optimize for my UX31E as much as I can and came across this [https://help.ubuntu.com/community/AsusZenbook](https://help.ubuntu.com/community/AsusZenbook)

You'll  notice that there are some tips for what to do with the GRUB file at  the top of the page, and also in the Power Saving Optimizations section.
Is  there any chance that some of these commands will conflict with each  other? for example, does following the top suggestions mean I can't use  the power saving ones? also, where do these arguments need to be placed  in relation to the "Quiet Splash" that is already present?

Sorry, bit of a noob when it comes to GRUB

---

### Post by deadflowr on 2015-12-16
You mean from this part:
> 1. Add the following boot arguments _both_ to GRUB_CMDLINE_LINUX_DEFAULT and GRUB_CMDLINE_LINUX in /etc/default/grub.cfg: 


intel_pstate=disable pcie_aspm=force acpi_osi='Windows 2009' acpi_os_name='Windows 2009'




justt add those to the line that has quiet splash in it.
keep each entry one space apart from each
Like this
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_pstate=disable pcie_aspm=force acpi_osi='Windows 2009' acpi_os_name='Windows 2009'"
```
that should be what you want to do.

---

