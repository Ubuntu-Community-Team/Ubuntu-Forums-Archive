---
title: "tracker-miner filling my storage with the same log"
date: 2024-03-30
forum: General Help
---

### Post by detscadosu24 on 2024-03-30
Hello,
I am having an issue with my 64-bit Ubuntu 22.04.4 LTS system (GNOME 42.9), the var/log/syslog and syslog.1 files are getting spammed by a repeating message that is filling up my whole 256 GB SSD (right now they are 23 GB and 89 GB in size respectively). What can I do to solve this? Below you will find the problematic log.
Thanks

```
Mar 15 16:08:10 matteo-laptop tracker-miner-f[2970]: g_file_has_prefix: assertion 'G_IS_FILE (prefix)' failed
Mar 15 16:08:10 matteo-laptop tracker-miner-f[2970]: g_file_equal: assertion 'G_IS_FILE (file2)' failed
Mar 15 16:08:10 matteo-laptop tracker-miner-f[2970]: g_file_has_prefix: assertion 'G_IS_FILE (prefix)' failed
Mar 15 16:08:10 matteo-laptop tracker-miner-f[2970]: g_file_equal: assertion 'G_IS_FILE (file2)' failed
Mar 15 16:08:10 matteo-laptop tracker-miner-f[2970]: g_file_has_prefix: assertion 'G_IS_FILE (prefix)' failed
Mar 15 16:08:10 matteo-laptop tracker-miner-f[2970]: g_file_equal: assertion 'G_IS_FILE (file2)' failed
...and so on...
```

---

### Post by HermanAB on 2024-03-30
Tracker miner is an idiotic desktop search function of Nautilus file manager.  It can be disabled:
"It appears that tracker can be disabled by simply going to Settings -> Search -> [Window bar] Switch Off."

[https://unix.stackexchange.com/questions/515775/gnome-desktops-tracker-spams-syslog-at-boot](https://unix.stackexchange.com/questions/515775/gnome-desktops-tracker-spams-syslog-at-boot)

---

### Post by TheFu on 2024-03-30
After you disable that message, why not place limits on the sizes for your log files?  /etc/systemd/journald.conf is the file where that can be accomplished. There's a manpage for it.  
```
$ man journald.conf  
```
to see the documented options, but the file is already commented with explanations.

For syslog specifically, you can also limit the size of that in the /etc/logrotate.d/rsyslog file.  There should be 15 examples of options in the same directory.  Nobody needs more than a few MB of logs. It isn't like you (or anyone) will be reading 1GB of logs.  Having a reasonable limit is a good idea, especially if you use Gnome.

---

### Post by detscadosu24 on 2024-03-31
> **HermanAB said:**
> Tracker miner is an idiotic desktop search function of Nautilus file manager.  It can be disabled:
"It appears that tracker can be disabled by simply going to Settings -> Search -> [Window bar] Switch Off."

[https://unix.stackexchange.com/questions/515775/gnome-desktops-tracker-spams-syslog-at-boot](https://unix.stackexchange.com/questions/515775/gnome-desktops-tracker-spams-syslog-at-boot)

I already tried that, the fix does not work. I keep getting the same logs.

---

### Post by MAFoElffen on 2024-03-31
For 22.04.x:
```

sudo chmod -x /usr/libexec/tracker-miner-fs-3
sudo chmod -x /usr/libexec/tracker-extract-3

```
...disables it's executable binaries. Strange, & out-of-the-box, but it works.

---

### Post by HermanAB on 2024-04-01
+1 for removing the executable flags.

Also do a “kill -9 whatever” while you are at it, to actually stop the annoyance.

This annoying indexing program is one of the reasons I don’t use Gnome.

---

### Post by detscadosu24 on 2024-04-01
> **MAFoElffen said:**
> For 22.04.x:
```

sudo chmod -x /usr/libexec/tracker-miner-fs-3
sudo chmod -x /usr/libexec/tracker-extract-3

```
...disables it's executable binaries. Strange, & out-of-the-box, but it works.

Thank you, I will let the PC run for a while and update this post to let you know if that actually solved it.

---

