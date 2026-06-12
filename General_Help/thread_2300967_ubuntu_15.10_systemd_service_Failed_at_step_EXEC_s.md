---
title: "ubuntu 15.10 systemd service: Failed at step EXEC spawning : No such file or director"
date: 2015-10-29
forum: General Help
---

### Post by mike4ubuntu on 2015-10-29
I'm having trouble even getting a simple test service running in the new systemd with 15.10.  It complains that it can't find the service script files, but they are on the disk where specified in the service file.  Anybody have any ideas?

```

Oct 29 17:08:54 studio4 systemd[890]: test-startup.service: Failed at step EXEC spawning /opt/services/test-startup-prestart.sh: No such file or directory
Oct 29 17:08:54 studio4 systemd[931]: test-startup.service: Failed at step EXEC spawning /usr/bin/test-startup.sh: No such file or directory
Oct 29 17:08:54 studio4 systemd[1]: test-startup.service: Control process exited, code=exited status=203
Oct 29 17:08:54 studio4 systemd[1]: test-startup.service: Unit entered failed state.
Oct 29 17:08:54 studio4 systemd[1]: test-startup.service: Failed with result 'exit-code'.

```

```

cat /lib/systemd/system/test-startup.service 
[Unit]
Description=Job that runs Mike Lepore's test startup service
After=network.target remote-fs.target nss-lookup.target

[Service]
Type=forking
Environment=statedir=/var/cache/foo
ExecStartPre=-/opt/services/test-startup-prestart.sh
ExecStart=/usr/bin/test-startup.sh

[Install]
WantedBy=multi-user.target

```

```

ll /usr/bin/test-startup.sh
4 -rwxr-xr-x 1 root root 1198 Oct 29 16:49 /usr/bin/test-startup.sh*
ll /opt/services/test-startup-prestart.sh
4 -rwxrwxrwx 1 mike mike 1204 Oct 29 15:54 /opt/services/test-startup-prestart.sh*

```

---

### Post by mike4ubuntu on 2015-11-02
bump

anybody?

is 15.10 not worth the effort?

is anybody using ubuntu anymore?

---

### Post by col48 on 2015-11-02
I've no idea what this is all about, but has the process you are invoking got the necessary permissions?  [This is the "New to Ubuntu" section of the forums, after all!]

---

### Post by mike4ubuntu on 2015-11-02
I just created this thread in the General Help forum, because I didn't know where else to put it.  If this is for Ubuntu noobs, then yeah, it probably won't get too many replies.  What forum does it fit better with?

It could be a permissions, but I can't tell which file/folder would be the problem.  I was hoping to find someone who is pretty familiar with systemd.  I've only ever used upstart up until now, but upstart doesn't seem to be supported in 15.10 at all.

---

