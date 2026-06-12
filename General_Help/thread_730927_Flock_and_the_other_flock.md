---
title: "Flock and the other flock"
date: 2008-03-21
forum: General Help
---

### Post by maniheer on 2008-03-21
Are there two programs called flock? Because every time I type flock in terminal, this comes up

flock (util-linux-ng 2.13)
Usage: flock [-sxun][-w #] fd#
       flock [-sxon][-w #] file [-c] command...
  -s  --shared     Get a shared lock
  -x  --exclusive  Get an exclusive lock
  -u  --unlock     Remove a lock
  -n  --nonblock   Fail rather than wait
  -w  --timeout    Wait for a limited amount of time
  -o  --close      Close file descriptor before running command
  -c  --command    Run a single command string through the shell
  -h  --help       Display this text
  -V  --version    Display version

And when I type /usr/share/flock/flock the flock browser comes up.:confused: I got the .deb package from getdeb.net to install flock (the web browser).

What does the other flock do? And can I uninstall it?

---

### Post by makan on 2008-04-04
create a symlink for your flock (browser) 

```
sudo ln -s /usr/share/flock/flock /usr/bin/flock-browser
```

after that you can run you flock browser by typing flock-browser

for complete howto: [http://ubuntuforums.org/showthread.php?t=268273](http://ubuntuforums.org/showthread.php?t=268273)

---

