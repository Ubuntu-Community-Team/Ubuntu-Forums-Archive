---
title: "Difference in behaviour of 'service &lt;service-name&gt; status"
date: 2016-09-28
forum: General Help
---

### Post by davaweb on 2016-09-28
I am confused by the different behaviour of service <service-name> status between 14.04 and 16.04.

14.04:
```
$ sudo service vpnfirewall status
[sudo] password for david:
echo $?
```
returned
 0

16.04:
```
$ sudo service vpnfirewall status
[sudo] password for david:
```
returns:
&#9679; vpnfirewall.service - LSB: VPN Firewall
   Loaded: loaded (/etc/init.d/vpnfirewall; bad; vendor preset: enabled)
   Active: active (exited) since Wed 2016-09-28 14:36:14 AEST; 53s ago
     Docs: man:systemd-sysv-generator(8)
  Process: 745 ExecStart=/etc/init.d/vpnfirewall start (code=exited, status=0/SU

Sep 28 14:36:14 Ubuntu-160401-C systemd[1]: Starting LSB: VPN Firewall...
Sep 28 14:36:14 Ubuntu-160401-C vpnfirewall[745]: OK: Loading VPN firewall...
Sep 28 14:36:14 Ubuntu-160401-C vpnfirewall[745]: OK: The firewall should not sh
Sep 28 14:36:14 Ubuntu-160401-C vpnfirewall[745]: OK: besides output beginning w
Sep 28 14:36:14 Ubuntu-160401-C vpnfirewall[745]: OK: VPN firewall loaded.
Sep 28 14:36:14 Ubuntu-160401-C systemd[1]: Started LSB: VPN Firewall.
lines 1-12/12 (END)

What is it telling me in 16.04, please and why the different outputs?

---

