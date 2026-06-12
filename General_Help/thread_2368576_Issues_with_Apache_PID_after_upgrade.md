---
title: "Issues with Apache PID after upgrade"
date: 2017-08-12
forum: General Help
---

### Post by Rich_Stanton on 2017-08-12
Hi,

I've recently upgraded a server from a previous LTS version to 14.04. Apache starts OK, but claims it hasn't. I.e. the console says it failed to start, however in actual fact it did start, and works fine. If I try & stop it, I get:
There are processes named 'apache2' running which do not match your pid file which are left untouched in the name of safety, Please review the situation by hand.

I can kill the pids, which enables me to restart apache, but then the whole issue starts all over again. I.e. console says it hasn't started, and if I want to restart it, I have to do so by hand. I don't know if it's related, but /var/run/apache2 is empty, despite apache2.conf specifying "PidFile /var/run/apache2.pid", and envvars specifying "export APACHE_PID_FILE=/var/run/apache2/apache2$SUFFIX.pid". I'm assuming these PID problems are contributing to the original problem.

I've had a look in error.log, it doesn't have much that's informative:
[Sat Aug 12 15:31:38.514038 2017] [mpm_prefork:notice] [pid 14320] AH00169: caught SIGTERM, shutting down
[Sat Aug 12 15:31:42.515663 2017] [ssl:warn] [pid 14600] AH01909: RSA certificate configured for rich.iniim.cf.ac.uk:443 does NOT include an ID which matches the server name
[Sat Aug 12 15:31:42.561259 2017] [ssl:warn] [pid 14601] AH01909: RSA certificate configured for rich.iniim.cf.ac.uk:443 does NOT include an ID which matches the server name
[Sat Aug 12 15:31:42.563840 2017] [mpm_prefork:notice] [pid 14601] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.22 OpenSSL/1.0.1f configured -- resuming normal operations
[Sat Aug 12 15:31:42.563907 2017] [core:notice] [pid 14601] AH00094: Command line: '/usr/sbin/apache2'



Any ideas how to fix this?

---

### Post by Rich_Stanton on 2017-08-12
Doh - just realised that the 2 PID directives are pointing to different places. Fixed that & it's all fine.

---

### Post by ajgreeny on 2017-08-12
Please mark as SOLVED from Thread Tools at the top of this thread.

---

