---
title: "&quot;Couldn't get UEFI db list &quot; bug after the second opening Ubuntu"
date: 2018-08-19
forum: General Help
---

### Post by my-lord on 2018-08-19
I am trying to migrate W&#304;ndows to Ubuntu.I have prepared bootable USB with rufus. I restarted my laptop and went to the setup page, setting my USB drive as main boot option and disabling all other options.

I encountered the same following problem:
[https://askubuntu.com/q/861743/861776](https://askubuntu.com/q/861743/861776)
I fixed this problem with using acpi=off.


I have erased all disk and made clean installation.On the first opening I have installed development tools(JDK,Netbeans...) and move my files to Ubuntu.On the second opening I get following GRUB menu.
> 
    1.Advanced GRUB Options for Ubuntu
    2.Ubuntu


After choosing the second option , I get following error.

    > ACPI Error : [_UPC] Namespace lookup failure,AE_ALREADYEXIST(Z0170031/dswload-378)
    
    ACPI Exception : AE_ALREADY_EXIST During name lookup/catalog failure
    
    ACPI Exception : AE_ALREADY_EXIST(SSDT:xh_rupli) while loading table (Z0170831/tbxfload-228)

    ACPI Error : 1 table load failures, 0 successful(Z0170831/tbxfload-228)
    Couldn't get size : 0x800000000...e
    MODSIGN :Couldn't get UEFI db list 


I have done some research on internet find following solutions:
[B]
First Solution[/B]
I closed Secure Boot from BIOS settings but It didn't work.I still get same error.


*Ubuntu version : 18.04.1 LTS*

---

### Post by oldfred on 2018-08-19
Another thread with issue.
[https://ubuntuforums.org/showthread.php?t=2380700](https://ubuntuforums.org/showthread.php?t=2380700)

I think there is some change to allow users to add there own keys to install proprietary drivers with Secure Boot on. Ubuntu cannot certified third party drivers, but users can create their own keys.
I do not currently run Secure Boot and often easier for now not to. Perhaps in future it may be required.

---

