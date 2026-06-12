---
title: "Apt-get error"
date: 2005-03-22
forum: General Help
---

### Post by ChaperonNoir on 2005-03-22
Hello ! Since yesterday, when installing a package i get this error message.

Errors were encountered while processing:
 postfix
 mutt
 postfix-tls
 ubuntu-base
E: Sub-process /usr/bin/dpkg returned an error code (1)


What does that mean ? How can i fix it  :-(

---

### Post by lao_V on 2005-03-22
I was also getting this error. However after re-configuring mutt it disappeared. Cant remember how to configure mutt but try to install postfix and I think it will tell you what needs to be done.

Alternatively, you could try to re-install ubuntu-base?

---

### Post by Johan on 2005-03-22
[QUOTE=lao_V]Cant remember how to configure mutt ...[/QUOTE]

You'll accomplish that by dpkg --configure mutt. :-)

---

### Post by ChaperonNoir on 2005-03-22
Thanks it works now.

However i don't see why mutt is so important with apt-get

---

### Post by lao_V on 2005-03-22
[QUOTE=ChaperonNoir]Thanks it works now.

However i don't see why mutt is so important with apt-get[/QUOTE]
 I don't understand either. Maybe someone will come up with an explanation?

---

### Post by cdhotfire on 2005-03-22
Mutt is a sophisticated text-based Mail User Agent. Some highlights: 

  o MIME support (including RFC1522 encoding/decoding of 8-bit message
   headers and UTF-8 support).
 o PGP/MIME support (RFC 2015).
 o Advanced IMAP client supporting SSL encryption and SASL authentication.
 o POP3 support.
 o Mailbox threading (both strict and non-strict).
 o Default keybindings are much like ELM.
 o Keybindings are configurable; Mush and PINE-like ones are provided as
   examples.
 o Handles MMDF, MH and Maildir in addition to regular mbox format.
 o Messages may be (indefinitely) postponed.
 o Colour support.
 o Highly configurable through easy but powerful rc file.

[http://higgs.djpig.de/ubuntu/www/hoary/mail/mutt](http://higgs.djpig.de/ubuntu/www/hoary/mail/mutt)

---

### Post by mish on 2005-03-31
I've had similar errors since upgrading from warty to hoary, but configuring mutt doesn't help.  postfix appears to be the blocking problem.  If I try to configure it I get

[FONT=Lucida Console]root@mishine:~ # dpkg --configure postfix
Setting up postfix (2.1.5-9ubuntu3) ...

Postfix configuration was untouched.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
 * Starting Postfix Mail Transport Agent...
postsuper: fatal: scan_dir_push: open directory incoming/F: Permission denied
 *stfix/postfix-script: fatal: Postfix integrity check failed!                     [fail]
invoke-rc.d: initscript postfix, action "start" failed.
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 postfix
[/FONT]

whenever I run apt-get install XXX, the install runs fine, but at the end I get

[FONT=Lucida Console]root@mishine:~ # apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
9 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up postfix (2.1.5-9ubuntu3) ...

Postfix configuration was untouched.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
 * Starting Postfix Mail Transport Agent...
postsuper: fatal: scan_dir_push: open directory incoming/F: Permission denied
 *stfix/postfix-script: fatal: Postfix integrity check failed!                     [fail]
invoke-rc.d: initscript postfix, action "start" failed.
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of at:
 at depends on mail-transport-agent; however:
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing at (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mailx:
 mailx depends on exim4 | mail-transport-agent; however:
  Package exim4 is not installed.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing mailx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mutt:
 mutt depends on exim4 | mail-transport-agent; however:
  Package exim4 is not installed.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing mutt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of anacron:
 anacron depends on exim4 | mail-transport-agent; however:
  Package exim4 is not installed.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing anacron (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of postfix-tls:
 postfix-tls depends on postfix; however:
  Package postfix is not configured yet.
 postfix-tls depends on postfix (= 2.1.5-9ubuntu3); however:
  Package postfix is not configured yet.
dpkg: error processing postfix-tls (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-base:
 ubuntu-base depends on at; however:
  Package at is not configured yet.
 ubuntu-base depends on mailx; however:
  Package mailx is not configured yet.
 ubuntu-base depends on mutt; however:
  Package mutt is not configured yet.
 ubuntu-base depends on postfix; however:
  Package postfix is not configured yet.
 ubuntu-base depends on postfix-tls; however:
  Package postfix-tls is not configured yet.
dpkg: error processing ubuntu-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb:
 lsb depends on exim4 | mail-transport-agent; however:
  Package exim4 is not installed.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
 lsb depends on at; however:
  Package at is not configured yet.
dpkg: error processing lsb (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on anacron; however:
  Package anacron is not configured yet.
 ubuntu-desktop depends on lsb; however:
  Package lsb is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 postfix
 at
 mailx
 mutt
 anacron
 postfix-tls
 ubuntu-base
 lsb
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/FONT]

Anyone got any ideas what to do?  i've searched google to no effect.

---

### Post by mish on 2005-04-04
Fixed the problem.  I had a small root partition, and in order to do the upgrade /var had to be moved to a new partition.  So the fix was 

chown -R postfix /var/spool/postfix
postsuper -s

followed by

dpkg --configure postfix
apt-get -f install

phew

---

### Post by David Marrs on 2005-10-14
Well I'm glad that worked for you. Nothing going for me, though. I'm getting the same message as everyone else has. None of the suggested solutions have worked so far.

Oh, i've just realised this is an old thread for the hoary release. This has just happened to me after dist-upgrading to breezy. So I guess I'm posting in the wrong forum :p

---

### Post by deppingh on 2005-10-15
[QUOTE=David Marrs]Well I'm glad that worked for you. Nothing going for me, though. I'm getting the same message as everyone else has. None of the suggested solutions have worked so far.

Oh, i've just realised this is an old thread for the hoary release. This has just happened to me after dist-upgrading to breezy. So I guess I'm posting in the wrong forum :p[/QUOTE]


I had the same problem after upgrading to breezy.  The solution for me was to simply stop postifx before running apt-get again:

sudo /etc/init.d/postfix stop
sudo apt-get install

---

### Post by Jessehk on 2005-10-15
(To the poster above)

THANKS!!!!:D:D:D

I have been trying to fix this error for about 3 hours now, and your simple solution solved the problem! 

Many thanks :)

*relief....*

---

