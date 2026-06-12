---
title: "SFTP using SSH chrootdirectory issue with user account will not connect to SFTP"
date: 2020-12-15
forum: General Help
---

### Post by gazcbg on 2020-12-15
Hi,

I just setup a VPS with Ubuntu 20.04 server on it and setup an account with username 'backups' and set a password
Location: /home/backups 
User/group: backups:backups


So I went into /etc/ssh/sshd_config and added

```

Match user backups
  ChrootDirectory /home/backups/Files
  PasswordAuthentication yes
  X11Forwarding no
  AllowAgentForwarding no
  AllowTcpForwarding no
  ForceCommand internal-sftp

```

However when I try and connect using Filezilla, it will not connect.

When I comment out the ChrootDirectory it works fine.

When I ```
chown -R /home/backups root:root
```
It will connect fine - however this it not really safe way to do it.

What am I missing here? as it appear to be a permission issue.

Thanks

Regards,
Gaz

---

### Post by TheFu on 2020-12-15
There are many other requirements according to the sshd_config manpage. Please read at least the section about using chroot. Excerpts:
```

             The ChrootDirectory must contain the necessary files and directo&#8208;
             ries to support the user's session.  For an interactive session
             this requires at least a shell, typically sh(1), and basic /dev
             nodes such as null(4), zero(4), stdin(4), stdout(4), stderr(4),
             and tty(4) devices.  For file transfer sessions using SFTP no ad&#8208;
             ditional configuration of the environment is necessary if the in-
             process sftp-server is used, though sessions which use logging
             may require /dev/log inside the chroot directory on some operat&#8208;
             ing systems (see sftp-server(8) for details).

             For safety, it is very important that the directory hierarchy be
             prevented from modification by other processes on the system (es&#8208;
             pecially those outside the jail).  Misconfiguration can lead to
             unsafe environments which sshd(8) cannot detect.
```
The internal-sftp server manpage has some hints as well.
```
     -d start_directory
             specifies an alternate starting directory for users.  The path&#8208;
             name may contain the following tokens that are expanded at run&#8208;
             time: %% is replaced by a literal '%', %d is replaced by the home
             directory of the user being authenticated, and %u is replaced by
             the username of that user.  The default is to use the user's home
             directory.  This option is useful in conjunction with the
             sshd_config(5) ChrootDirectory option.
...
     On some systems, sftp-server must be able to access /dev/log for logging
     to work, and use of sftp-server in a chroot configuration therefore re&#8208;
     quires that syslogd(8) establish a logging socket inside the chroot di&#8208;
     rectory.
```

---

