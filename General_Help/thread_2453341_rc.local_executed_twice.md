---
title: "rc.local executed twice"
date: 2020-11-08
forum: General Help
---

### Post by simone-c on 2020-11-08
Hi,

out of a sudden my rc.local started to execute twice on every boot. First noticed it two weeks ago after restarting one of the servers.
I noticed that, because I used rc.local to execute a custom command. Which now starts two processes and causes a conflict

I have this behavior on two different servers both running the latest Ubuntu 20

Anyone knows what has happened and which update may have caused this?

And please let me know if this is a known issue and there is a workaround until it's fixed

Thanks!

---

### Post by ActionParsnip on 2020-11-08
Your script could check if it's already running and not run if there is an instance already

---

### Post by simone-c on 2020-11-16
Yes, I could develop a logic to exit if the rc.local has already executed. But doesn't it sound like a bug that should be investigated and fixed? I don't think that rc.local has been designed to be run a random number of time

---

### Post by yapidumoac on 2020-11-16
Maybe: SystemD creates a rc-local.service which calls rc-local.

---

### Post by Tadaen_Sylvermane on 2020-11-16
The proper solution would be to stop relying on rc.local and move yourself to systemd service files. On my recent 20.04 installation rc.local doesn't even exist. Need to keep up with changes rather than holding on to the past.

---

### Post by dinkidonk on 2020-11-17
A simple run once sollution:

```
#!/bin/sh
if [ -f /dev/shm/myscript_run_once ]; then
  exit 0
fi
touch /dev/shm/myscript_run_once
echo "Starting..."
```

A systemd service is the better way to go these days, just remember that when running a script from a systemd service either no environment or a very limited one is available and this may break functionality if relying on environment variables.

---

