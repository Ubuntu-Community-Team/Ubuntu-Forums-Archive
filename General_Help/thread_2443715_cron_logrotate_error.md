---
title: "cron logrotate error"
date: 2020-05-19
forum: General Help
---

### Post by marchello_lippi2 on 2020-05-19
Hi all, 
Getting below error:
```

[COLOR=#000000][FONT=monospace]/etc/cron.daily/logrotate:[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace] Failed to access socket path: /var/run/fail2ban/fail2ban.sock. Is fail2ban running?[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]error: error running non-shared postrotate script for /var/log/fail2ban.log of '/var/log/fail2ban.log '[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]run-parts: /etc/cron.daily/logrotate exited with return code 1[/FONT][/COLOR]

```
How do I fix it? Please advise.

---

### Post by dino99 on 2020-05-19
fail2ban.sock might be one of these non-shared postrotate script

---

### Post by btindie on 2020-05-19
> **dino99 said:**
> fail2ban.sock might be one of these non-shared postrotate script
Nope, it's a unix socket used to control the fail2ban process. That message will mean that either the logrotate script doesn't have permission to access it, unlikely, or the fail2ban process isn't running so the socket doesn't exist.

You don't mention which version of Ubuntu you're using so it may have changed, but on mine the postrotate hook looks like
```
    postrotate
         fail2ban-client flushlogs 1>/dev/null
    endscript

```

Are you running fail2ban? If not, just uninstall it.

If you want to leave it on there you could always just redirect *stderr *as in
```
fail2ban-client flushlogs 2>&1 1>/dev/null
```
which will suppress that message.

If you need anymore info then please provide the contents of your /etc/logrotate.d/fail2ban file.

---

