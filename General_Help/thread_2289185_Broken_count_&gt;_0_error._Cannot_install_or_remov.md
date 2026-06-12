---
title: "Broken count &gt; 0 error. Cannot install or remove anything from software center."
date: 2015-08-02
forum: General Help
---

### Post by Margesh on 2015-08-02
Hello, I'm new to Ubuntu and I've encountered an error which I couldn't solve even after trying searching it on google for a while. I am getting a 'broken count >0 error. This usually means your installed packages have unmet dependencies.'
There's a red minus sign at the top.

I cannot even install a package manager to remove the broken package because I get error in the software center ; [http://i.imgur.com/arXhAo8.png](http://i.imgur.com/arXhAo8.png)

I also get this error : [http://i.imgur.com/ofJJRrN.png](http://i.imgur.com/ofJJRrN.png)  and of course, repairing it does not help.
I tried google and thought you might need the results of these commands:


Results on sudo dpkg --configure -a

```
]ads@ads-H61H2-M4:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of kde-telepathy-minimal:
 kde-telepathy-minimal depends on kde-config-telepathy-accounts (>= 15.04.0); however:
  Package kde-config-telepathy-accounts is not installed.

dpkg: error processing package kde-telepathy-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kde-telepathy:
 kde-telepathy depends on kde-telepathy-minimal (= 15.04.0-0ubuntu1~ubuntu15.04~ppa2); however:
  Package kde-telepathy-minimal is not configured yet.

dpkg: error processing package kde-telepathy (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 kde-telepathy-minimal
 kde-telepathy.


```

Results sudo apt-get install -f
```
ads@ads-H61H2-M4:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of kde-telepathy-minimal:
 kde-telepathy-minimal depends on kde-config-telepathy-accounts (>= 15.04.0); however:
  Package kde-config-telepathy-accounts is not installed.

dpkg: error processing package kde-telepathy-minimal (--config.ure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kde-telepathy:
 kde-telepathy depends on kde-telepathy-minimal (= 15.04.0-0ubuntu1~ubuntu15.04~ppa2); however:
  Package kde-telepathy-minimal is not configured yet.

dpkg: error processing package kde-telepathy (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 kde-telepathy-minimal
 kde-telepathy
ads@ads-H61H2-M4:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  kde-l10n-engb
Use 'apt-get autoremove' to remove it.
The following extra packages will be installed:
  kde-config-telepathy-accounts
The following NEW packages will be installed:
  kde-config-telepathy-accounts
0 upgraded, 1 newly installed, 0 to remove and 188 not upgraded.
2 not fully installed or removed.
Need to get 131 kB of archives.
After this operation, 697 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/ vivid/main kde-config-telepathy-accounts i386 15.04.1-0ubuntu1~ubuntu15.04~ppa1 [131 kB]
Fetched 131 kB in 2s (59.6 kB/s)                        
(Reading database ... 237260 files and directories currently installed.)
Preparing to unpack .../kde-config-telepathy-accounts_15.04.1-0ubuntu1~ubuntu15.04~ppa1_i386.deb ...
Unpacking kde-config-telepathy-accounts (15.04.1-0ubuntu1~ubuntu15.04~ppa1) ...
dpkg: error processing archive /var/cache/apt/archives/kde-config-telepathy-accounts_15.04.1-0ubuntu1~ubuntu15.04~ppa1_i386.deb (--unpack):
 trying to overwrite '/usr/share/accounts/services/google-im.service'., which is also in package account-plugin-google 0.12+15.04.20150415.1-0ubuntu1
Errors were encountered while processing:
 /var/cache/apt/archives/kde-config-telepathy-accounts_15.04.1-0ubuntu1~ubuntu15.04~ppa1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

I can see that KDE-telepathy is causing errors but I don't know much about Ubuntu so I don't exactly know. I had installed the Kubuntu desktop for the plasma so I don't know where did the telepathy stuff come from. I would just like to go back to ubuntu interface without any error, any loss in data and be able to use the software center again without any re-instalation. 

Thank you in advance.

---

### Post by dino99 on 2015-08-02
try that command from a terminal:
> sudo apt-get purge kde-telepathy*

---

### Post by Margesh on 2015-08-02
> **dino99 said:**
> try that command from a terminal:

Thanks. That worked like a charm.

---

