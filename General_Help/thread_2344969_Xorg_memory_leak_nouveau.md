---
title: "Xorg memory leak nouveau"
date: 2016-11-29
forum: General Help
---

### Post by th317erd on 2016-11-29
Hello! X appears to have a memory leak and searching for Google for a solution has resulted in nothing. I would file a bug report but I am uncertain which logs to attach or commands to run to provide information.

My issue is that X slowly consumes memory. After only 1 day of uptime on my Acer Aspire laptop, X is using 11.7% of my 8G of memory. I am constantly having to reboot because of this. When the computer is idle (but I never put it to sleep) I have Chrome, a terminal, and sublime text 3 running at all times (and xscreensaver).

My hardware is as follows:
[LIST]
[*]Intel Core i7 4500U
[*]NVIDIA GeForce GT 750M (using nouveau driver)
[*]8GB memory
[/LIST]

Software:
[LIST]
[*]Lubuntu
[*]xcompmgr
[*]conky
[*]xscreensaver
[/LIST]

uname -a:
Linux ********* 4.4.0-47-generic #68-Ubuntu SMP Wed Oct 26 19:39:52 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

X -version:
X.Org X Server 1.18.4
Release Date: 2016-07-19
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.4.0-45-generic x86_64 Ubuntu
Current Operating System: Linux ******** 4.4.0-47-generic #68-Ubuntu SMP Wed Oct 26 19:39:52 UTC 2016 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-47-generic.efi.signed root=UUID=6ca716c8-3e55-4282-92c2-0bfd63d66e03 ro noprompt persistent quiet splash vt.handoff=7
Build Date: 02 November 2016  10:06:10PM
xorg-server 2:1.18.4-0ubuntu0.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.33.6
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.


lsb_release -a:
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

Help? How can I track down the problem?

---

