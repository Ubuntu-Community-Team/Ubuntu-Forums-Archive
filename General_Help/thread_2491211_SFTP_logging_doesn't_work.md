---
title: "SFTP logging doesn't work"
date: 2023-09-29
forum: General Help
---

### Post by micron1390 on 2023-09-29
Hello,
Could you tell me please has anyone encountered setting up logs for the SFTP protocol on Ubuntu 22.04?  I have the following configs the SFTP server itself is working, I connect but the logs are not poured into the /var/log/sftp.log directory  


cat /etc/ssh/sshd_config
```

Subsystem sftp /usr/lib/openssh/sftp-serverMatch User test

ForceCommand internal-sftp -f LOCAL7 -l INFO

PasswordAuthentication yes

ChrootDirectory /var/sftp

PermitTunnel no

AllowAgentForwarding no

AllowTcpForwarding no

X11Forwarding no

```

cat /etc/rsyslog.d/60-sftp.conf
```

# Create socket within chrooted directories to allow for logging

$AddUnixListenSocket /var/sftp/uploads/dev/log

# Parse the data logged at level INFO and facility LOCAL7 into /var/log/sftp.log

LOCAL7.info /var/log/sftp.log

# Report logins and logoffs

:syslogtag,startswith,"sftp-server" /var/log/sftp.log
```

Thanks in advance for suggestions.

---

### Post by MAFoElffen on 2023-09-29
<<Should probably be moved to Server>>
I looked in up in the RedHat Docs. Ubuntu should be similar in how that is set... It say the caveat there is the chroot...

RE: [https://access.redhat.com/articles/1374633](https://access.redhat.com/articles/1374633)

> 
The base release of openssh doesn't have the ability to log from a chrooted environment, if there is no available and configured socket located in /dev/log.

But that article does describe how to set that up for a chrooted sftp...

---

### Post by btindie on 2023-10-02
```
$AddUnixListenSocket /var/sftp/uploads/dev/log
```
is incorrect. Your setup uses [FONT=system]/var/sftp[/FONT] as the chroot base which means the sftp process expects to find the socket at [FONT=system]/var/sftp/dev/log[/FONT]

I've got similar working fine on multiple systems. Except for the rsyslog config for which I use the newer style
```
input(type="imuxsock" HostName="sftp" Socket="/var/sftp/dev/log")

:hostname, isequal, "sftp" {
  /var/log/sftp.log
  stop
}
```
and filter based on the hostname field.

---

