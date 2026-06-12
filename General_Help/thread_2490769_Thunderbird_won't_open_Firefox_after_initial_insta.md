---
title: "Thunderbird won't open Firefox after initial instance"
date: 2023-09-15
forum: General Help
---

### Post by von Stalhein on 2023-09-15
Hi all,

As per the title - click on a link in a Thunderbird email after first  start of PC (Ubuntu 23.04 on Wayland) and it opens up the browser and  navs to the page.

Next click on an email link, the Firefox icon wobbles (like a Mac notification) but I have to alt-tab or mouse to the browser window.

I've been in about:config in both programs to check network handlers and  other protocols that load tabs in the background but to no avail.

No tweaks or changes other than whatever updates Ubuntu push out.

Any ideas? 					Thanks!

---

### Post by SeijiSensei on 2023-09-19
Had the problem today and found the solution here for Kubuntu 22.04: [https://askubuntu.com/questions/1422920/how-does-one-enable-wsl-interoperability-on-ubuntu-22-04](https://askubuntu.com/questions/1422920/how-does-one-enable-wsl-interoperability-on-ubuntu-22-04)

Ubuntu now installs a module to provide compatibility with Microsoft's [WSL]("https://learn.microsoft.com/en-us/windows/wsl/install"). Unfortunately, if you're not on a Windows machine you get all sorts of errors. 

If you run thunderbird from the command prompt you get this:
```

$ thunderbird &
grep: /proc/sys/fs/binfmt_misc/WSLInterop: No such file or directory
WSL Interopability is disabled. Please enable it before using WSL.
grep: /proc/sys/fs/binfmt_misc/WSLInterop: No such file or directory
[error] WSL Interoperability is disabled. Please enable it before using WSL.
/usr/bin/wslview: line 216: /mnt/c/Windows/System32/reg.exe: No such file or directory
/usr/bin/wslview: line 149: /mnt/c/Windows/System32/chcp.com: No such file or directory
/usr/bin/wslview: line 156: /mnt/c/Windows/System32/WindowsPowerShell/v1.0/powershell.exe: No such file or directory
/usr/bin/wslview: line 149: /mnt/c/Windows/System32/chcp.com: No such file or directory

```

The solution is to remove the module:

```

sudo apt update
sudo apt purge wslu

```

then open Thunderbird. 

This problem exists in all current versions of Thunderbird for Ubuntu including the .deb file provided by the Thunderbird repository and the downloadable binary for Linux. I'm running Thunderbird 115.2.2 which I downloaded directly from [here](https://www.thunderbird.net/en-US/download/). It had the same WSL problems as the other versions.

This is a **really annoying problem** that arose out of nowhere simply because everyone wants to get into bed with Microsoft. Ubuntu should not be shipping wslu by default, but only if the installer recognizes it's on WSL.

As I expected, this problem does not arise on my Debian 12 system using the same downloaded binary. It's the presence of wslu that triggers the problem.

---

### Post by von Stalhein on 2023-09-25
Thanks very much for that info!
I've not been near this machine for a week. 
Thunderbird updated and the problem went away, which is both good and annoying at the same time.

---

### Post by SeijiSensei on 2023-09-30
As I said, this is a problem that may be unique to Ubuntu. Debian 12 has no such issues.

---

