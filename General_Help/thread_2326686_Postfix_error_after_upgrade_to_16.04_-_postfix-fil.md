---
title: "Postfix error after upgrade to 16.04 - postfix-files is not a file."
date: 2016-06-03
forum: General Help
---

### Post by mrpg99 on 2016-06-03
Hi,

Had postfix up and running on my server, then upgraded from 15.10 to 16.04

Now the service wont start :

18:36:27] mrpg@pgdc001:[/usr/lib/postfix/sbin]: sudo service postfix start
Job for postfix.service failed because the control process exited with error code. See "systemctl status postfix.service" and "journalctl

18:37:51] mrpg@pgdc001:[/usr/lib/postfix/sbin]: sudo service postfix status
&#9679; postfix.service - LSB: Postfix Mail Transport Agent
   Loaded: loaded (/etc/init.d/postfix; bad; vendor preset: enabled)
  Drop-In: /run/systemd/generator/postfix.service.d
           &#9492;&#9472;50-postfix-$mail-transport-agent.conf
   Active: failed (Result: exit-code) since Fri 2016-06-03 18:37:51 CEST; 25s ago
     Docs: man:systemd-sysv-generator(8)
  Process: 5912 ExecStart=/etc/init.d/postfix start (code=exited, status=1/FAILURE)

Jun 03 18:37:48 pgdc001 postfix[6016]: Postfix is running with backwards-compatible default settings
Jun 03 18:37:48 pgdc001 postfix[6016]: See [http://www.postfix.org/COMPATIBILITY_README.html](http://www.postfix.org/COMPATIBILITY_README.html) for details
Jun 03 18:37:48 pgdc001 postfix[6016]: To disable backwards compatibility use "postconf compatibility_level=2" and "postfix reload"
Jun 03 18:37:50 pgdc001 postfix[5912]: /usr/lib/postfix/sbin/post-install: Error: /etc/postfix/postfix-files is not a file.
Jun 03 18:37:50 pgdc001 postfix/postfix-script[6039]: fatal: Postfix integrity check failed!
Jun 03 18:37:51 pgdc001 postfix[5912]:    ...fail!
Jun 03 18:37:51 pgdc001 systemd[1]: postfix.service: Control process exited, code=exited status=1
Jun 03 18:37:51 pgdc001 systemd[1]: Failed to start LSB: Postfix Mail Transport Agent.
Jun 03 18:37:51 pgdc001 systemd[1]: postfix.service: Unit entered failed state.
Jun 03 18:37:51 pgdc001 systemd[1]: postfix.service: Failed with result 'exit-code'.

My guess is that this is the issue : /usr/lib/postfix/sbin/post-install: Error: /etc/postfix/postfix-files is not a file. 

But i have no idea how to fix it, anyone?

Best Regards
Patric

---

### Post by mrpg99 on 2016-06-04
Hi,

I actually managed to fix this myself.

Turns out my /etc/hosts file was really strange, it had my hostname listed about 100 times, and postfix inserted a strange hostname into main.cf when it tried to re-configure it.

Sorting out my /etc/hosts fixed the postfix error.

Br
Paric

---

### Post by sheph on 2016-09-24
It was something else for me.  For me it was postfix-files didn't exist

in /etc/postfix I issued the following command...

mv postfix-files.dpkg-dist postfix-files

...and then ran...

apt-get --fix-broken install

...and it worked.

---

