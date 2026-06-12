---
title: "Possible Successful hacking attempt to my Ubuntu machine?"
date: 2013-08-30
forum: General Help
---

### Post by Mesopotamia on 2013-08-30
Hi all,

I accessed my Ubuntu (not so secure server) this morning and accessed it via VNC to see (for the second day in a row) that my Chrome browser had a Western Union page loaded in it with someone's account. I tried browse through the account but the page was killed.

I checked the Chrome browsing history and everything, but the Western Union, pages were in the history page (go back for 6 hours).

I checked the /var/log/auth.log and I don't seem to find any SUCCESSFUL SSH2 attempts to my server. There were multiple attempts with different usernames but all failed.

Could you please advise what else needs to be checked? For some reason, I doubt it's an Ubuntu hacking attempt and more to do with Chrome, but your input is appreciated. They (whoever they are in Brazil or Russia) didn't touch any of my home files.

Cheers

There are a lot of these messages:
> Aug 31 06:19:30 Babylon sshd[19563]: Invalid user gast1 from 92.61.37.112Aug 31 06:19:30 Babylon sshd[19563]: input_userauth_request: invalid user gast1 [preauth]
Aug 31 06:19:30 Babylon sshd[19563]: pam_unix(sshd:auth): check pass; user unknown
Aug 31 06:19:30 Babylon sshd[19563]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=92.61.37.112 
Aug 31 06:19:32 Babylon sshd[19563]: Failed password for invalid user gast1 from 92.61.37.112 port 47634 ssh2
Aug 31 06:19:33 Babylon sshd[19563]: Received disconnect from 92.61.37.112: 11: Bye Bye [preauth]
Aug 31 06:19:36 Babylon sshd[19565]: reverse mapping checking getaddrinfo for 7618el834.sritis.lt [92.61.37.112] failed - POSSIBLE BREAK-IN ATTEMPT!

---

### Post by nerdtron on 2013-08-30
Is your server accessible from the internet or the outside world? If so, you should have secured it beforehand.
During this type of situation of possible break-in attempts, we immediately take down the server and replace it with a fresh one. Then we investigate this offline server about possible changes. You aren't sure yet if there really is a break in. Or if there is a break in, the attacker could change some files that you will possibly look.

For example, he could inject the cat command or the ls command and he could add bogus log files that will show no one has logged in. Worst if it could add a program that logs key strokes and send them to the attacker. You see, if there is a break in attempt, it'll be hard to pinpoint exactly what the attacker had viewed or changed, unless you have a backup of your system and compared the changes.

My advice here, if you are no longer confident on the consistency/security of your server, take it down before it can do any further damage. And review you security settings.

EDIT: I looked at my /var/log/auth.log in my mail server and I have a lot of authentication failures from ssh
```
Aug 25 17:48:04 mail sshd[5576]: Failed password for root from 119.80.39.55 port 40171 ssh2Aug 25 17:48:04 mail sshd[5576]: Received disconnect from 119.80.39.55: 11: Bye Bye [preauth]
Aug 25 17:48:06 mail sshd[5578]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=119.80.39.55  user=root

```

I get these regularly and I have fail2ban to ban them on too many attempts. I guess as long as there are no successful logins on the auth.log that you aren't aware of, you're OK.

---

### Post by ian-weisser on 2013-08-30
Nerdtron is right.
Take your system offline immediately.
Reinstall afresh. Restore your data from backups.

Happened to me a couple years ago. My security is much stronger now.

---

### Post by SeijiSensei on 2013-08-30
Never use VNC on an Internet-facing server.  It's not secure enough unless you access it over an encrypted tunnel with SSH or OpenVPN.

---

### Post by Mesopotamia on 2013-08-30
Having an exam in the next few days and I can't risk re-installing everything from scratch. I will do that in the next few days.

Thanks everyone for your input. I will take it off the internet immediately.

---

### Post by zealibib slaughter on 2013-08-30
I do not ever keep a vnc session running for security reasons.  If I got to remote access my desktop I invoke a vnc session via ssh then kill the vnc server after I am done.  I also use ssh keys instead of passwords.  I agree you should take the system down for further review and you really should reinstall and restore.

---

