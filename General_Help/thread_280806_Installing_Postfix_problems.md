---
title: "Installing Postfix problems"
date: 2006-10-20
forum: General Help
---

### Post by hartunnoo on 2006-10-20
Help!
I got error during installing postfix 

Reading package lists... Done
Building dependency tree... Done
postfix is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up postfix (2.2.10-1ubuntu0.1) ...
setting inet_protocols: all

Postfix is now set up with the changes above.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

[COLOR="Red"]Running newaliases
 * Stopping Postfix Mail Transport Agent postfix                                                                                                      [ ok ]
 * Starting Postfix Mail Transport Agent postfix                                                                                                             postfix: fatal: /etc/postfix/postfix-script: No such file or directory
                                                                                                                                                      [fail]
invoke-rc.d: initscript postfix, action "restart" failed.
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/COLOR]

do you know what is the problem? :(

---

### Post by hartunnoo on 2006-10-20
well never mind I got the answer.

I just type this 

apt-get --purge remove postfix

it solves my problem. :)

---

