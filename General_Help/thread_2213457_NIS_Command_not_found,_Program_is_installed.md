---
title: "NIS: Command not found, Program is installed"
date: 2014-03-26
forum: General Help
---

### Post by maevik on 2014-03-26
I am putting together an nis network login system, but running into an error where the command nis is not found even after the program has been installed. portmap (rpcbind), ypserv, and all that seem to work ok, but I cannot start, restart, etc, nis.

```
compchem_admin@compchem-server:~$ sudo apt-get install nis
[sudo] password for compchem_admin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nis is already the newest version.
The following package was automatically installed and is no longer required:
  thunderbird-globalmenu
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
compchem_admin@compchem-server:~$ nis
No command 'nis' found, did you mean:
 Command 'fis' from package 'redboot-tools' (main)
 Command 'nes' from package 'mednafen' (universe)
 Command 'nes' from package 'fceu' (universe)
 Command 'nns' from package 'tcllib' (universe)
 Command 'ns' from package 'ns2' (universe)
nis: command not found
compchem_admin@compchem-server:~$ 
```

---

### Post by TheFu on 2014-03-26
It has been a few years, but I don't think there is a "program" called NIS. I think it is a metapackage - but I could be wrong.
If yppasswd works and netgroups work, then NIS is working.

Are you aware of the huge security problems with NIS?

---

