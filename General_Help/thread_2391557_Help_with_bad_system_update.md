---
title: "Help with bad system update"
date: 2018-05-10
forum: General Help
---

### Post by schmitta on 2018-05-10
I am not too swift so please bear with me. A month or so ago UBUNTU/Linux tried to do a system update and it failed about half way through. Since then I can't get the monitor to come up after doing a suspend and I   have to do a cold start from the reset switch on the computer. I tried to do a <sudo apt update> to fix the problem and got the following:

E: The repository 'http://ppa.launchpad.net/linaro-maintainers/tools/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

Someone told me it may be a driver for the monitor that did not download correctly.  Any help would be greatly appreciated.

---

### Post by deadflowr on 2018-05-10
You need to remove the linaro-maintainers ppa as it does not exist for xenial.
Easiest way is through Software and Updates > Other Software.
Find the linaro entry and set it to disable or highlight and select remove.
The updates should run again.

You may need to try running
```
sudo apt-get update
sudo apt-get install -f
```
the install -f command is to fix broken packages.

---

### Post by schmitta on 2018-05-22
Thank you for your help.

---

