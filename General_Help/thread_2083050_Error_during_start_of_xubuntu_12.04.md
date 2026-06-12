---
title: "Error during start of xubuntu 12.04"
date: 2012-11-11
forum: General Help
---

### Post by Mars-x on 2012-11-11
Hi all, 
I have a little problem. During start of the system, I got Error:

> 
iptables-restore v1.4.12: Couldn't load target `ufw-skip-to-policy-input`:No such file or directory

Error occurred at line: 19
Try `iptables-restore -h` or `iptables-restore --help` for more information.

Problem running `/etc/ufw/after.rules`

and 
> 
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service rc6

The script you are attempting to invoke has been converted to an Upstart job, but 6 is not supported for Upstart jobs.
error: `/etc/init.d/rc` exited outside the expected code flow.

I compare files /etc/ufw/after.rules on machine with the error and on other machine and they are the same. 

Can anyone help me to solve these problems? 
Thanks.

---

