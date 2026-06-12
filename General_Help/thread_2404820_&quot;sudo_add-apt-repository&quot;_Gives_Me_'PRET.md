---
title: "&quot;sudo add-apt-repository&quot; Gives Me 'PRETTY_NAME' Error"
date: 2018-10-28
forum: General Help
---

### Post by SBTlauien on 2018-10-28
I'm trying to add a repository but I keep on getting an error.  I did an update and an upgrade, along with a reboot, but I'm still getting this error.

I get the same error regardless of the repository that I'm trying to add.  It looks like a Python error of some sort.

This is what I'm getting...

```

Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 11, in <module>
    from softwareproperties.SoftwareProperties import SoftwareProperties, shortcut_handler
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 64, in <module>
    from . import shortcuts
  File "/usr/lib/python3/dist-packages/softwareproperties/shortcuts.py", line 23, in <module>
    _DEF_CODENAME = aptsources.distro.get_distro().codename
  File "/usr/lib/python3/dist-packages/aptsources/distro.py", line 576, in get_distro
    os_release = _OSRelease()
  File "/usr/lib/python3/dist-packages/aptsources/distro.py", line 529, in __init__
    self.inject_lsb_compat()
  File "/usr/lib/python3/dist-packages/aptsources/distro.py", line 533, in inject_lsb_compat
    self.result['Description'] = self.result['PRETTY_NAME']
KeyError: 'PRETTY_NAME'

```

Searching around, I haven't found any solutions.

---

### Post by dino99 on 2018-10-29
install/reinstall python3-software-properties

---

### Post by &amp;KyT$0P# on 2018-10-29
If dino99 suggestion doesn't work, please post the output from running this command in Terminal -
```
cat /etc/os-release
```

---

### Post by SBTlauien on 2018-10-31
> **dino99 said:**
> install/reinstall python3-software-properties

This did not work.

> **halogen2 said:**
> If dino99 suggestion doesn't work, please post the output from running this command in Terminal -
```
cat /etc/os-release
```

Here it is...

```

NAME=""
VERSION="18.04.1 LTS (Bionic Beaver)"
ID=ubuntu
ID_LIKE=debian
NAME=""
VERSION_ID="18.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"

```

---

### Post by mc4man on 2018-10-31
/etc/os-release is a link to the file  /usr/lib/os-release , here's mine
```
NAME="Ubuntu"
VERSION="18.04.1 LTS (Bionic Beaver)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 18.04.1 LTS"
VERSION_ID="18.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=bionic
UBUNTU_CODENAME=bionic
```

Maybe try editing your's to match

---

### Post by SBTlauien on 2018-11-03
> **mc4man said:**
> /etc/os-release is a link to the file  /usr/lib/os-release , here's mine
```
NAME="Ubuntu"
VERSION="18.04.1 LTS (Bionic Beaver)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 18.04.1 LTS"
VERSION_ID="18.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=bionic
UBUNTU_CODENAME=bionic
```

Maybe try editing your's to match

This solved it.  I have an install script that removes the 'Ubuntu' from the first line, but it also was removing the PRETTY_NAME variable as well.

Thank you.

---

