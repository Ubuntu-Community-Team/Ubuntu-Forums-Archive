---
title: "Remove files left after uninstalling a game."
date: 2020-11-13
forum: General Help
---

### Post by makem2 on 2020-11-13
Some while ago I tried steam on ubuntu but now would like to uninstall it.

I followed these instructions:

[https://askubuntu.com/questions/499874/completely-uninstall-steam-and-all-steam-games](https://askubuntu.com/questions/499874/completely-uninstall-steam-and-all-steam-games)

But after rebooting I get a pop-up asking me to complete the steam install for the current user and a desktop icon.

When I search for files remaining I get this lit:

[https://www.dropbox.com/s/6ru8xdjalomky5i/Screenshot_2020-11-13_18-19-50.png?dl=0](https://www.dropbox.com/s/6ru8xdjalomky5i/Screenshot_2020-11-13_18-19-50.png?dl=0)

Would it be safe to deleted those?

```

makem@XPS-13-9300:~$ cat /etc/os-release
NAME="Ubuntu"
VERSION="20.04.1 LTS (Focal Fossa)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 20.04.1 LTS"
VERSION_ID="20.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=focal
UBUNTU_CODENAME=focal
makem@XPS-13-9300:~$ 
makem@XPS-13-9300:~$ sudo dpkg --purge steam
dpkg: warning: ignoring request to remove steam which isn't installed
makem@XPS-13-9300:~$


```

---

### Post by makem2 on 2020-11-14
After another reboot the pop-up no longer appears but the files i found still remain. They are not taking up much space but I would prefer to remove them if possible without breaking xubuntu. It is the xxx.ko and xxx.h files which worry me. Aso if the installer is left behind and cannot find the files it needs it may cause a hangup of the whole system.

Best left alone?

---

### Post by CelticWarrior on 2020-11-14
Better left alone.

Those files are - probably - drivers for Steam hardware.

---

### Post by makem2 on 2020-11-14
Yes, I thought that might be the case. However, I think it 'may' be possible to remove the last 4 files on the list and so get rid of the Steam icon that comes on the desktop. This is the launcher which will reinstall all of steam from scratch. The command in it is:

```

/usr/bin/steam %U

```

Just need confirmation before I attempt it. Scared lol.

Edit: Moved the desktop icon to the waste basket, rebooted and it didn't come back. Conclusion: leave well alone.

Cheers

---

