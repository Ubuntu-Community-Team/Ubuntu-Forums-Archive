---
title: "[SOLVED] Kerio Mail Server + Ubuntu 7.10"
date: 2007-11-26
forum: General Help
---

### Post by Poleh on 2007-11-26
Confirmation that the above process works with Ubuntu 7.10 as per the following post:
[http://ubuntuforums.org/showthread.php?t=460955](http://ubuntuforums.org/showthread.php?t=460955)

Please don't forget to over-write the default /etc/init.d/keriomailserver file with the one attached in the previous post, if you don't you can expect to see something like the following output:

```

root@ubuntu-vm:/opt/kerio/mailserver# sudo /etc/init.d/keriomailserver start
/etc/init.d/keriomailserver: line 105: /etc/rc.status: No such file or directory
/etc/init.d/keriomailserver: line 107: rc_reset: command not found
/etc/init.d/keriomailserver: line 111: checkproc: command not found
/etc/init.d/keriomailserver: line 118: startproc: command not found
/etc/init.d/keriomailserver: line 122: checkproc: command not found
/etc/init.d/keriomailserver: line 122: checkproc: command not found
/etc/init.d/keriomailserver: line 122: checkproc: command not found
/etc/init.d/keriomailserver: line 122: checkproc: command not found
/etc/init.d/keriomailserver: line 122: checkproc: command not found
/etc/init.d/keriomailserver: line 122: checkproc: command not found
/etc/init.d/keriomailserver: line 122: checkproc: command not found
/etc/init.d/keriomailserver: line 122: checkproc: command not found
/etc/init.d/keriomailserver: line 122: checkproc: command not found
/etc/init.d/keriomailserver: line 122: checkproc: command not found
Starting Kerio MailServer: /etc/init.d/keriomailserver: line 132: rc_failed: command not found
/etc/init.d/keriomailserver: line 175: rc_exit: command not found

```

---

### Post by gubemton on 2007-11-26
feexd! 

dont forget to download the attached initilization script u noob :P - [http://pastebin.com/m407285b0](http://pastebin.com/m407285b0)


- Ali

---

