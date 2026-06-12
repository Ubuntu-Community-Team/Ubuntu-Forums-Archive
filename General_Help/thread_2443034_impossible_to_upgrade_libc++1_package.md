---
title: "impossible to upgrade libc++1 package"
date: 2020-05-10
forum: General Help
---

### Post by alain.roger on 2020-05-10
Hi,

I upgraded from ubuntu 19.10 to 20.04 (KDE).
After upgrade, i have the following package that does not upgrade and stay with 19.10 version, after a "sudo apt upgrade" command.

```
[FONT=monospace][COLOR=#000000]Reading package lists... Done[/COLOR]
Building dependency tree        
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libc++1
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
[/FONT]
```

i tried "sudo apt list --upgradable" and got:
```
[FONT=monospace][COLOR=#000000]Listing... Done[/COLOR]
[COLOR=#18B218]libc++1[/COLOR][COLOR=#000000]/focal 1:10.0-50~exp1 amd64 [upgradable from: 1:9.0-49~exp1][/COLOR]
[COLOR=#B26818]N: [/COLOR][COLOR=#000000]There is 1 additional version. Please use the '-a' switch to see it[/COLOR]
[/FONT]
```

using "sudo apt list --upgradable -a" returned :
```
[FONT=monospace][COLOR=#000000]Listing... Done[/COLOR]
[COLOR=#18B218]libc++1[/COLOR][COLOR=#000000]/focal 1:10.0-50~exp1 amd64 [upgradable from: 1:9.0-49~exp1][/COLOR]
[COLOR=#18B218]libc++1[/COLOR][COLOR=#000000]/now 1:9.0-49~exp1 amd64 [installed,upgradable to: 1:10.0-50~exp1][/COLOR]
[/FONT]
```

i tried:
- sudo apt update
- sudo apt upgrade
- sudo apt full-upgrade
- sudo apt dist-upgrade

none of them allows to upgrade the package libc++1 to focal (20.04) version.

What am I doing wrong ?

thx

---

### Post by CelticWarrior on 2020-05-10
The same happened to me (solution included): [https://ubuntuforums.org/showthread.php?t=2441409](https://ubuntuforums.org/showthread.php?t=2441409)

---

### Post by alain.roger on 2020-05-11
i tried also sudo apt-get -s install libc++1/focal but without success in my case.

Next sudo apt update gave me the same output:

```
[FONT=monospace][COLOR=#000000]Fetched 306 kB in 6s (47,8 kB/s)                                                                                                                                                                                                                                [/COLOR]
Reading package lists... Done
Building dependency tree        
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libc++1
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Upgrade done ...[/FONT]
```

so i had no choice to remove libc++1, and to reinstall it again.
This time the right version has been installed.

---

