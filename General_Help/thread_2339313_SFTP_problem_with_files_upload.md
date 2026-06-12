---
title: "SFTP problem with files upload"
date: 2016-10-07
forum: General Help
---

### Post by selera on 2016-10-07
Hi, I just install Ubuntu this week, and have problem with uploading files via SFTP.
First I use FileZilla, then use BareFTP, I also try FireFTP (Firefox add-on), and the last one I use sftp command from terminal. All have same problem, I can connect to server (my hosting, godaddy managed wordpress) but when uploading files, "timed out" (on FileZilla & bareFTP) and on sftp command "stalled".

I never have this problem uploading when using FileZilla on my last OS (Windows XP) and also have no problem when using AndFTP on my Andorid phone (and this is my temporary way to upload files now).
Can anyone help to fix this?

Thanks

---

### Post by TheFu on 2016-10-07
Does ssh work?
Did you install openssh-server?
Is there a firewall blocking connections?

What do the log files show?  On a client, increase the debug output with -vvv options. Anything helpful in that output?
Which userid is the remote connection using? Hopefully, not root - never root.

---

### Post by selera on 2016-10-09
I can login with ssh.
Is UFW a firewall?

filezilla log
```

Status:    Connecting to <server>...
Status:    Connected to <server>
Status:    Retrieving directory listing...
Status:    Listing directory <directory>
Status:    Directory listing of "<directory>" successful
Status:    Connecting to <server>...
Status:    Connected to <server>
Status:    Starting upload of <path/file>
Status:    local:<path/file> => remote:<path/file>
Error:    Connection timed out after 60 seconds of inactivity
Error:    File transfer failed
Status:    Disconnected from server

```

sftp log
```

user@mchine:~$ sftp username@server
Connected to <server>.
sftp> cd <directory>
sftp> put <path/file>
Uploading <path/file> to <path/file>
<path/file>   0%    0     0.0KB/s - stalled -

```
after waiting (maybe time out)
```

<path/file>   0%    0     0.0KB/s - stalled -packet_write_wait: Connection to <ip> port 22: Broken pipe

```

---

