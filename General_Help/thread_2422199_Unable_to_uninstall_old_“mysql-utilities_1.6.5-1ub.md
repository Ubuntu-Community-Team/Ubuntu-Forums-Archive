---
title: "Unable to uninstall old “mysql-utilities_1.6.5-1ubuntu16.10_all.deb” in Ubuntu 19.04."
date: 2019-07-03
forum: General Help
---

### Post by pranav.bhattarai on 2019-07-03
My Java Sir told me to install MySQL-server, workbench, and connector. I did that somehow.

After launching Workbench, I went to Tools > Start Shell for MySQL Utilities. Which gave me this popup: [https://imgur.com/GQvHKsI](https://imgur.com/GQvHKsI)

Pressing Download option redirected me to this website: [https://imgur.com/ETr2nrY](https://imgur.com/ETr2nrY)

pranav@inspiron-5548:~$ sudo apt-get upgrade
[sudo] password for pranav: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  mysql-connector-python
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 1,362 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 216555 files and directories currently installed.)
Removing mysql-connector-python (8.0.16-1ubuntu19.04) ...
Traceback (most recent call last):
  File "<string>", line 1, in <module>
ModuleNotFoundError: No module named 'distutils.sysconfig'
dpkg: error processing package mysql-connector-python (--remove):
 installed mysql-connector-python package post-removal script subprocess returned error exit status 1
Errors were encountered while processing:
 mysql-connector-python
E: Sub-process /usr/bin/dpkg returned an error code (1)

So, I thought I should uninstall this, and I used **sudo apt-get remove --purge mysql-connector-python** command, but it also didn't work, and it throws me the same error as above.

What to do? I am in limbo here! Since any new development did in "mysql-utilities" is aged back to Jan 17, 2017, I don't think I will be needing this anymore. I did the mistake trying to install old archived deb package. (newbie)

*IF u know, how to remove it, what is it, it would be really helpful to tell me about it.*

---

### Post by pranav.bhattarai on 2019-07-04
[FONT=Arial]Normally, sudo apt autoremove should have worked but in this case, I used this command to the solved issue:[/FONT]
[FONT=inherit]
[/FONT][FONT=inherit]sudo mv /var/lib/dpkg/info/mysql-connector-python*/tmp[/FONT][FONT=inherit]

[/FONT][FONT=Arial]After using the above command, use sudo apt autoremove again and that will solve everything.[/FONT]
[FONT=Arial]For more details about this issue, visit [this]("https://itsfoss.com/dpkg-returned-an-error-code-1/") site.[/FONT]

---

