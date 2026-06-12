---
title: "[Is my OS crippled?] I can't do anything in the terminal"
date: 2016-12-02
forum: General Help
---

### Post by flamingicecave on 2016-12-02
Any command I try to run always gets interrupted by Vyprvpn. I installed it to try to use their VPN service and now it won't go away and it's interrupting any command lines I do. Whenever I try to run something, anything, I get this error "E: The package vyprvpn needs to be reinstalled, but I can't seem to find an archive for it." Again, this error shows up when I try to run almost anything in my terminal. I've tried uninstalling the package normally, purging it, killing the process, everything. I just can't get rid of it. Should I just reinstall my OS?


Running Ubuntu 16.04 LTS on a Dell Chromebook 11 via crouton.

---

### Post by #&amp;thj^% on 2016-12-02
Don't know anything about it but to reinstall it have a look here
[https://support.goldenfrog.com/hc/en-us/articles/204102996-VyprVPN-CLI-for-Linux](https://support.goldenfrog.com/hc/en-us/articles/204102996-VyprVPN-CLI-for-Linux)
And maybe VyprVPN Support would be a better place to get support.
[https://support.goldenfrog.com/hc/en-us/requests/new](https://support.goldenfrog.com/hc/en-us/requests/new)

And when using the Terminal have you tried to issue
```
clear
```
Best of Luck Though
EDIT: Just thought about this also...when the terminal starts acting up...Try using Key Combo>>"Ctrl+c"
Make sure the focus is on the terminal though.

---

### Post by ajgreeny on 2016-12-02
How did you install Vyprvpn?
Was it a .deb archive from the site shown by 1fallen or some other method?

Probably worth trying ```
sudo dpkg -P --simulate vyprvpn*
```and if thet runs with no errors remove the **--simulate** option.
You can also try removing it using synaptic if you have it installed.

---

