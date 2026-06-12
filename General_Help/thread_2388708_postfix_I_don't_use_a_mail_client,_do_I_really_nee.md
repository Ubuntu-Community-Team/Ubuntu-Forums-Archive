---
title: "postfix: I don't use a mail client, do I really need it on desktop edition?"
date: 2018-04-06
forum: General Help
---

### Post by &amp;wP*!) on 2018-04-06
I am using Ubuntu 17.10.

I don't use any mail client locally on my desktop edition, but by default the mail service is enabled.
Is it safe to disable/uninstall this completely and how?

At /var/log/syslog I see following messages:

```

...
Apr  6 13:44:31 sporadiccrash configure-instance.sh[1243]: postconf: fatal: open /etc/postfix/main.cf: No such file or directory
...
Apr  6 13:44:33 sporadiccrash systemd[1]: postfix@-.service: Control process exited, code=exited status=1
Apr  6 13:44:33 sporadiccrash systemd[1]: Failed to start Postfix Mail Transport Agent (instance -).
Apr  6 13:44:33 sporadiccrash systemd[1]: postfix@-.service: Unit entered failed state.
Apr  6 13:44:33 sporadiccrash systemd[1]: postfix@-.service: Failed with result 'exit-code'.
...
Apr  6 13:44:41 sporadiccrash nm-dispatcher[791]: postconf: fatal: open /etc/postfix/main.cf: No such file or directory

```

---

### Post by TheFu on 2018-04-06
If you haven't specifically configured postfix (an MTA), it is used for local email only.  

Basically that means cron and messages to webmaster/root accounts.  A typical desktop user wouldn't have any use for postfix, even if they install a thick email client program like thunderbird.  Why?  Because this email clients have settings to communicate with outside mail servers over IMAP/POP3 and authenticated SMTPS using port 587 or 465/tcp.

But the OS uses cron, the system does.  Then having a way to read those outputs files which are send via local email, especially when there is a failure, is important.   Not having an MTA on a Unix system is an anti-pattern, usually.  One of the core services that Unix has provided almost since the beginning was email.

---

### Post by &amp;wP*!) on 2018-04-06
> **TheFu said:**
> If you haven't specifically configured postfix (an MTA), it is used for local email only.  

Basically that means cron and messages to webmaster/root accounts.  A typical desktop user wouldn't have any use for postfix, even if they install a thick email client program like thunderbird.  Why?  Because this email clients have settings to communicate with outside mail servers over IMAP/POP3 and authenticated SMTPS using port 587 or 465/tcp.
[B]
But the OS uses cron, the system does.  Then having a way to read those outputs files which are send via local email, especially when there is a failure, is important.   Not having an MTA on a Unix system is an anti-pattern, usually.  One of the core services that Unix has provided almost since the beginning was email.[/B]

Thank you for this explanation 

Can you advise whether the steps are OK for local mail of cron/system messaging? I did following steps and observed following:

1. Reconfigure the package (on many web sites "apt-get install --reinstall postfix" recommended, but it did not work - it did not create the main.cf file)
```

sudo dpkg-reconfigure postfix

```

2. In the menu, "No configuration" was chosen, but at stdout following text appeared:
```
Postfix (main.cf) configuration was untouched.  If you need to make changes, 
edit /etc/postfix/main.cf (and others) as needed.  To view Postfix 
configuration values, see postconf(1).

After modifying main.cf, be sure to run 'service postfix reload'.

Running newaliases
Processing triggers for libc-bin (2.26-0ubuntu2.1) ...
```
According to the information above, I have copied manually the main.cf file. Then I have rebooted.

The /var/log/syslog has after the reboot following:
```
Apr  7 00:45:57 sporadiccrash systemd[1]: Starting Postfix Mail Transport Agent (instance -)...
...
Apr  7 00:45:57 sporadiccrash postfix/postfix-script[1418]: starting the Postfix mail system
Apr  7 00:45:57 sporadiccrash postfix/master[1420]: daemon started -- version 3.2.3, configuration /etc/postfix
...
Apr  7 00:45:57 sporadiccrash systemd[1]: Started Postfix Mail Transport Agent (instance -).
Apr  7 00:45:57 sporadiccrash systemd[1]: Starting Postfix Mail Transport Agent...
Apr  7 00:45:57 sporadiccrash systemd[1]: Started Postfix Mail Transport Agent.
...

Apr  7 00:46:07 sporadiccrash systemd[1]: Reloading Postfix Mail Transport Agent (instance -).
Apr  7 00:46:07 sporadiccrash postfix/postfix-script[1615]: refreshing the Postfix mail system
Apr  7 00:46:07 sporadiccrash postfix/master[1420]: reload -- version 3.2.3, configuration /etc/postfix
Apr  7 00:46:07 sporadiccrash systemd[1]: Reloaded Postfix Mail Transport Agent (instance -).
Apr  7 00:46:07 sporadiccrash systemd[1]: Reloading Postfix Mail Transport Agent.
Apr  7 00:46:07 sporadiccrash systemd[1]: Reloaded Postfix Mail Transport Agent.
...
Apr  7 00:46:17 sporadiccrash systemd[1]: Reloading Postfix Mail Transport Agent (instance -).
Apr  7 00:46:17 sporadiccrash postfix/postfix-script[1676]: refreshing the Postfix mail system
Apr  7 00:46:17 sporadiccrash postfix/master[1420]: reload -- version 3.2.3, configuration /etc/postfix
Apr  7 00:46:17 sporadiccrash systemd[1]: Reloaded Postfix Mail Transport Agent (instance -).
Apr  7 00:46:17 sporadiccrash systemd[1]: Reloading Postfix Mail Transport Agent.
Apr  7 00:46:17 sporadiccrash systemd[1]: Reloaded Postfix Mail Transport Agent.
...
```

Is it OK that agent is reloaded a couple of times by systemd in the beginning?

---

### Post by TheFu on 2018-04-07
Sorry.  I've never not configured postfix on any of my systems.  If the config files aren't properly created, I don't know what happens.  systemd attempting to restart it seems reasonable. I was unable to find the systemd postfix.service script on my system after a quick search.  Don't know why. Without seeing that I can't say if it attempts to run 1 time or forever.

BTW, rebooting the system generally isn't required for 99% of things on Unix-like systems.

---

### Post by HermanAB on 2018-04-08
On a personal system you don't need a MTA.  Especially on a laptop computer, it is just a waste of power.

---

### Post by &amp;wP*!) on 2018-04-08
[QUOTE=HermanAB]On a personal system you don't need a MTA. Especially on a laptop computer, it is just a waste of power. [/QUOTE]

Thank you for the reply. Actually I wanted to uninstall it first, but the comment below confused me (you can find it if you scroll up).

[QUOTE=TheFu]But the OS uses cron, the system does. Then having a way to read those outputs files which are send via local email, especially when there is a failure, is important. Not having an MTA on a Unix system is an anti-pattern, usually. One of the core services that Unix has provided almost since the beginning was email.[/QUOTE]

This comment is a from server administration point of view, where such a mailing service should be there (even though this user is not using mail service). 

On a desktop system like mine, all the messages from all executables can be found /var/log/syslog, dmesg output etc anyway.

Thus I have uninstalled the package, by following [these instructions]("http://installion.co.uk/ubuntu/xenial/main/p/postfix/uninstall/index.html")

Thanks again!

---

