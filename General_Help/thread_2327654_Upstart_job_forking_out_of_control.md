---
title: "Upstart job forking out of control"
date: 2016-06-13
forum: General Help
---

### Post by kerzane on 2016-06-13
I am trying to run a particular daemon through upstart.

Outside of upstart it runs as expected, and produces a pid file which matches the process id.

When launched in upstart however (without expect fork or daemon), the process seems to fork in an uncontrolled way. The pid file will match the inital pid upstart detected, and the forked process is not identified by upstart, so that it assumes the service is not running.

When launched with expect daemon or fork, upstart still fails to collect the pid of the new process. The pid of the original and final processes differ by about 4 or 5, which could mean that it is forking that many times, which I understand can't be tracked.

What could it be that causes the job to fork within upstart but not otherwise? Why can upstart not track the new PID? Why is the PID file not overwritten by the new process?

Here is my upstart script:

```


description "bitcoinUnlimited"
start on filesystem and static-network-up
stop on runlevel [!2345]
oom score -500
#expect fork
#respawn
#respawn limit 10 60 # 10 times in 60 seconds
#post-stop exec sleep 10
#expect daemon
#expect fork
script
    user=bitcoinUnlimited
    home=/mnt/storage_hd/var/lib/$user
    cmd=/usr/local/bin/bitcoinUnlimitedd
    pidfile=$home/.bitcoin/bitcoind.pid
    # Don't change anything below here unless you know what you're doing
    test -e $pidfile -a ! -d "/proc/$(cat $pidfile)" && rm $pidfile
    test -e $pidfile -a "$(cat /proc/$(cat $pidfile)/cmdline)" != "$cmd" && rm $pidfile
    exec start-stop-daemon --start -c $user --chdir $home --pidfile $pidfile -m --startas $cmd
end script


```

---

### Post by kerzane on 2016-06-14
Bump.

Don't know where else to ask this guys.

In short: Why would a job fork when run through upstart, where as it does not when run normally? How can I debug this behaviour?

Many thanks.

---

