---
title: "How to run Java 8 JNLP on IcedTea?"
date: 2021-02-07
forum: General Help
---

### Post by rtek1000 on 2021-02-07
Hello,


I managed to run the application correctly on Windows 10, but I can't on Linux.


I discovered on the internet that IcedTea is necessary to run the *.jnlp file, and it seems that the currently available version (icedtea-next) only works with Java 11.


But it looks like this *.jnlp application I'm trying to run works only with Java 8.

Does anybody know how to solve this?


I tried several tips, but they seem to be out of date.

Version of Linux (Xubuntu) I'm running:

[COLOR=#333333][FONT=&amp]$ cat /etc/os-release[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]NAME="Ubuntu"[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]VERSION="20.04.2 LTS (Focal Fossa)"[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]ID=ubuntu[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]ID_LIKE=debian[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]PRETTY_NAME="Ubuntu 20.04.2 LTS"[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]VERSION_ID="20.04"[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]HOME_URL="https://www.ubuntu.com/"[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]SUPPORT_URL="https://help.ubuntu.com/"[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]VERSION_CODENAME=focal[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]UBUNTU_CODENAME=focal
[/FONT][/COLOR]


Thank you.

---

### Post by Holger_Gehrke on 2021-02-07
It's icedtea-netx, not icedtea-next.

Do you have a Java Runtime Environment for Java 8 installed (package openjdk-8-jre, might need some others ...) ? Have you tried setting that as the default Java using update-java-alternatives ('update-java-alternatives -l' to get a list, 'sudo update-alternatives -s <name of the jre to set as default >' to set a default JRE) ?

Holger

---

