---
title: "Mail stopped working (dovecot)"
date: 2014-06-20
forum: General Help
---

### Post by networkguy09 on 2014-06-20
I setup my mail server several months ago and it has been working fine. Then I noticed I had stopped getting e-mail to my email client (my phone) so I did a reboot on the mail server yesterday and it fixed the issue temporarily. Now today I am not getting e-mails to my client again. I sent several test e-mails to my mail server from yahoo. I checked in the mail file and I am not even receiving the e-mails now (I was yesterday even when my mail client was failing to download them). I didn't make any change to create this problem. The mail server just stopped working. Any help is appreciated. If anyone can recommend a third party company paid support (someone who will do a live chat or team viewer with me to fix this problem I would very much like that)


cat /proc/version
Linux version 2.6.32-042stab090.3 (root@kbuild-rh6-x64) (gcc version 4.4.6 20120305 (Red Hat 4.4.6-4) (GCC) ) #1 SMP Fri Jun 6 09:35:21 MSK 2014

I noticed when I stop and start dovecot I get the following in the dovecot.log


Jun 20 10:02:11 imap: Warning: Killed with signal 15 (by pid=1 uid=0 code=kill)
Jun 20 10:02:11 imap(myemailaddy): Warning: Killed with signal 15 (by pid=1 uid=0 code=kill)
Jun 20 10:02:11 imap(myemailaddy): Warning: Killed with signal 15 (by pid=1 uid=0 code=kill)
Jun 20 10:02:11 auth: Warning: Killed with signal 15 (by pid=1 uid=0 code=kill)
Jun 20 10:02:11 imap-login: Warning: Killed with signal 15 (by pid=1 uid=0 code=kill)
Jun 20 10:02:11 log: Warning: Killed with signal 15 (by pid=1 uid=0 code=kill)
Jun 20 10:02:11 master: Warning: Killed with signal 15 (by pid=1 uid=0 code=kill)



I also have this issue that happened and I never got fixed [http://ubuntuforums.org/showthread.php?t=2221043&p=13008521#post13008521](http://ubuntuforums.org/showthread.php?t=2221043&p=13008521#post13008521)

---

### Post by networkguy09 on 2014-06-21
Getting failure notices to the emails I sent myself yesterday

---

