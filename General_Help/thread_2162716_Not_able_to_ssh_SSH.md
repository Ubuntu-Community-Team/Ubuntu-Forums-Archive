---
title: "Not able to ssh SSH"
date: 2013-07-15
forum: General Help
---

### Post by safdarq19 on 2013-07-15
I recently upgraded Ubuntu and facing issue when I try to ssh remotely and locally.

Error Message:
debug3: channel 0: close_fds r -1 w -1 e 6
Connection to 10.27.90.244 closed.
Transferred: sent 3408, received 2456 bytes, in 25.3 seconds
Bytes per second: sent 134.5, received 96.9
debug1: Exit status -1

---

### Post by Ceiber Boy on 2013-07-15
Could you please provide some configuration informarion, hopefully someone will be able to offer advice based on that.

Hope you get the help you need.

---

### Post by safdarq19 on 2013-07-16
[FONT=arial]_**[FONT=courier new, monospace]ssh_config  configuration[/FONT]**_[/FONT]
[FONT=arial][FONT=courier new, monospace]Host *[/FONT][/FONT]
[FONT=arial][FONT=courier new, monospace]ForwardAgent yes[/FONT][/FONT]
[FONT=arial][FONT=courier new, monospace]    PasswordAuthentication no[/FONT][/FONT]
[FONT=arial][FONT=courier new, monospace]  Port 22[/FONT][/FONT]
[FONT=arial][FONT=courier new, monospace]    SendEnv LANG LC_*[/FONT][/FONT]
[FONT=arial][FONT=courier new, monospace]    HashKnownHosts yes[/FONT][/FONT]
[FONT=arial][FONT=courier new, monospace]    GSSAPIAuthentication yes[/FONT][/FONT]
[FONT=arial][FONT=courier new, monospace]    GSSAPIDelegateCredentials no


[/FONT][U][B][FONT=courier new, monospace]sshd_config configuration
[/FONT][/B][/U]**[FONT=courier new, monospace]I am trying to log in with safdar user.[/FONT]**[U][B][FONT=courier new, monospace]

[/FONT][/B][/U]
[FONT=courier new, monospace]Port 22[/FONT]
[FONT=courier new, monospace]Protocol 2[/FONT]
[FONT=courier new, monospace]HostKey /etc/ssh/ssh_host_rsa_key[/FONT]
[FONT=courier new, monospace]HostKey /etc/ssh/ssh_host_dsa_key[/FONT]
[FONT=courier new, monospace]HostKey /etc/ssh/ssh_host_ecdsa_key[/FONT]
[FONT=courier new, monospace]UsePrivilegeSeparation yes[/FONT]
[FONT=courier new, monospace]
[/FONT]
[FONT=courier new, monospace]KeyRegenerationInterval 3600[/FONT]
[FONT=courier new, monospace]ServerKeyBits 768[/FONT]
[FONT=courier new, monospace]
[/FONT]
[FONT=courier new, monospace]SyslogFacility AUTH[/FONT]
[FONT=courier new, monospace]LogLevel DEBUG[/FONT]
[FONT=courier new, monospace]
[/FONT]
[FONT=courier new, monospace]LoginGraceTime 120[/FONT]
[FONT=courier new, monospace]PermitRootLogin no[/FONT]
[FONT=courier new, monospace]StrictModes yes[/FONT]
[FONT=courier new, monospace]
[/FONT]
[FONT=courier new, monospace]RSAAuthentication yes[/FONT]
[FONT=courier new, monospace]PubkeyAuthentication yes[/FONT]
[FONT=courier new, monospace]
[/FONT]
[FONT=courier new, monospace]IgnoreRhosts yes[/FONT]
[FONT=courier new, monospace]RhostsRSAAuthentication no[/FONT]
[FONT=courier new, monospace]HostbasedAuthentication no[/FONT]
[FONT=courier new, monospace]
[/FONT]
[FONT=courier new, monospace]PermitEmptyPasswords no[/FONT]
[FONT=courier new, monospace]
[/FONT]
[FONT=courier new, monospace]ChallengeResponseAuthentication no[/FONT]
[FONT=courier new, monospace]
[/FONT]
[FONT=courier new, monospace]
[/FONT]
[FONT=courier new, monospace]
[/FONT]
[FONT=courier new, monospace]
[/FONT]
[FONT=courier new, monospace]X11Forwarding yes[/FONT]
[FONT=courier new, monospace]X11DisplayOffset 10[/FONT]
[FONT=courier new, monospace]PrintMotd no[/FONT]
[FONT=courier new, monospace]PrintLastLog no[/FONT]
[FONT=courier new, monospace]TCPKeepAlive yes[/FONT]
[FONT=courier new, monospace]
[/FONT]
[FONT=courier new, monospace]
[/FONT]
[FONT=courier new, monospace]AllowUsers safdar [/FONT]
[FONT=courier new, monospace]
[/FONT]
[FONT=courier new, monospace]AcceptEnv LANG LC_*[/FONT]
[FONT=courier new, monospace]
[/FONT]
[FONT=courier new, monospace]Subsystem sftp /usr/lib/openssh/sftp-server[/FONT]
[FONT=courier new, monospace]
[/FONT]
[FONT=courier new, monospace]UsePAM yes[/FONT]
[/FONT]

---

