---
title: "Ubuntu 20.04.2 LTS landscape-sysinfo Output?"
date: 2021-02-22
forum: General Help
---

### Post by SAH62 on 2021-02-22
This is a very minor thing, but it has me curious since I can't find anything anywhere that explains how the plugin output of the landscape-sysinfo command can be split into multiple columns. On one of my machines, I see this (note that the plugin output is in one column):

> 
Welcome to Ubuntu 20.04.2 LTS (GNU/Linux 5.10.13-x86_64-linode141 x86_64)


 * Documentation:  [https://help.ubuntu.com](https://help.ubuntu.com)
 * Management:     [https://landscape.canonical.com](https://landscape.canonical.com)
 * Support:        [https://ubuntu.com/advantage](https://ubuntu.com/advantage)


  System information as of Mon 22 Feb 2021 06:47:34 AM EST


  System load:           0.08
  Usage of /:            16.9% of 156.38GB
  Memory usage:          35%
  Swap usage:            2%
  Processes:             195
  Users logged in:       0
  IPv4 address for eth0: <address>
  IPv6 address for eth0: <address>


0 updates can be installed immediately.
0 of these updates are security updates.


On a second machine (sorry, tabs are messed up, but note that the plugin output is displayed in two columns):

> 
Welcome to Ubuntu 20.04.2 LTS (GNU/Linux 5.4.0-65-generic x86_64)


 * Documentation:  [https://help.ubuntu.com](https://help.ubuntu.com)
 * Management:     [https://landscape.canonical.com](https://landscape.canonical.com)
 * Support:        [https://ubuntu.com/advantage](https://ubuntu.com/advantage)


  System information as of Mon 22 Feb 2021 06:51:34 AM EST


  System load:  0.0                Processes:             214
  Usage of /:   6.7% of 370.08GB    Users logged in:       0
  Memory usage: 5%                 IPv4 address for eth0: <address>
  Swap usage:   0%                 IPv4 address for eth1: <address>


0 updates can be installed immediately.
0 of these updates are security updates.


Why am I seeing single-column plugin output on one machine and two-column output on another?

---

### Post by schragge on 2021-02-22
This is handled in the function [format_sysinfo]("https://github.com/CanonicalLtd/landscape-client/blob/07b68d9c3e7c2524b1250dadc1a3b2aaf7cbcdc1/landscape/sysinfo/sysinfo.py#L123"). If the two-column output doesn't fit in 80 characters it will be print as single column.

---

### Post by SAH62 on 2021-02-22
Thanks! Strange thing is that I have both terminal emulators set to 140 characters wide, and Ubuntu seems to have accepted that:

> 
$ echo $COLUMNS
140
$


---

### Post by schragge on 2021-02-22
The function defaults to **width=80**. The default value doesn't get changed when the function [is called]("https://github.com/CanonicalLtd/landscape-client/blob/07b68d9c3e7c2524b1250dadc1a3b2aaf7cbcdc1/landscape/sysinfo/deployment.py#L118"). So setting COLUMNS has no effect.

---

