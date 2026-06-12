---
title: "Removing a broken package"
date: 2014-05-10
forum: General Help
---

### Post by Nigel_Storm on 2014-05-10
G'day guys,

Recently, I tried to install a package; and it failed as in it didn't install and spat out an error msg... 

And everytime I try and update my system, I get this error msg:

> 
The hostname -f command returned: $1

Your system needs to have a fully qualified domain name (fqdn) in
order to install the var-qmail packages.

Installation aborted.

dpkg: error processing qmail (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of qmail-run:
 qmail-run depends on qmail (>= 1.06-2.1); however:
  Package qmail is not configured yet.
dpkg: error processing qmail-run (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                Errors were encountered while processing:
 qmail
 qmail-run
E: Sub-process /usr/bin/dpkg returned an error code (1)



So I cannot install any updates or things of that like. How can I remove this broken link so that I can continue to install other packages?

Many thanks,

Nigel.

---

### Post by matt_symes on 2014-05-10
Hi

I take it you no longer wish to have qmail installed ?

If so, open a terminal and type

```
sudo apt-get purge qmail
```

Enter your password.

Then type

```
sudo apt-get update
```

Post back any errors.

Kind regards

---

### Post by Nigel_Storm on 2014-05-10
> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  qmail* qmail-run*
0 to upgrade, 0 to newly install, 2 to remove and 3 not to upgrade.
2 not fully installed or removed.
After this operation, 2,310 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 97082 files and directories currently installed.)
Removing qmail-run ...
update-service: warning: /etc/service/qmail-send does not exist.

update-service: warning: /etc/service/qmail-smtpd does not exist.

update-service: warning: /etc/service/qmail-verify does not exist.

Purging configuration files for qmail-run ...
Removing qmail ...
rmdir: failed to remove `/var/lib/qmail': Directory not empty
Purging configuration files for qmail ...
rmdir: failed to remove `/var/lib/qmail': Directory not empty
Processing triggers for man-db ...



Looks like its removed that. Thank you.

---

