---
title: "rsync over ssh with cron: connection problem"
date: 2015-06-09
forum: General Help
---

### Post by djmac on 2015-06-09
Hey all, I am having trouble getting an rsync cronjob to work over ssh.

The bash script containing the rsync commands / options works fine from the terminal (i.e. syncs to the remote machine over ssh without any problem). When run from the cron (user cron, not root) the sync fails. The following error messages are found in the rsync logfile:

```
 rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: unexplained error (code 255) at io.c(226) [sender=3.1.1]
```

I've seen similar problems to this in several different questions (e.g. here: [ssh/rsync issues]("http://ubuntuforums.org/showthread.php?t=2071941"),  [rsync: connection unexpectedly closed]("http://ubuntuforums.org/showthread.php?t=2243346") and [Why is this rsync + ssh cron job giving me 'Permission denied (publickey)' errors?]("https://askubuntu.com/questions/521142/why-is-this-rsync-ssh-cron-job-giving-me-permission-denied-publickey-error")), but haven't solved my problem yet..

FWIW, on the server:
```
[~]$ sudo service sshd status
openssh-daemon (pid  12191) is running...
```

(...and as mentioned above, it works from the command line - and ssh/scp/rsync works fine). 

Have also this option for the ssh identity file:
```
-e 'ssh -i /home/user/.ssh/id_rsa'
```

(and even full paths everything - including ssh and rsync.. eg:
```
/usr/bin/rsync -arvvv -e '/usr/bin/ssh -i /home/user/.ssh/id_rsa' ....
```

Which was also unsuccessful.. Not really sure what else to try - any ideas much appreciate. TIA

---

### Post by HermanAB on 2015-06-09
Try:
/usr/bin/rsync -arvvv -e '/usr/bin/ssh -vvv -i /home/user/.ssh/id_rsa' ....

---

### Post by djmac on 2015-06-10
One extra line in the log:

```
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: unexplained error (code 255) at io.c(226) [sender=3.1.1]
[sender] _exit_cleanup(code=12, file=io.c, line=226): about to call exit(255)
```

Maybe I should have mentioned the server is ScientificLinux (if that is relevant?)t:
```
[~]$ cat /proc/version
Linux version 2.6.32-431.20.3.el6.x86_64 (mockbuild@sl6.fnal.gov) (gcc version 4.4.7 20120313 (Red Hat 4.4.7-3) (GCC) ) #1 SMP Thu Jun 19 14:01:59 CDT 2014
```

---

### Post by djmac on 2015-06-10
Okay.  A bit of googling and this thread [Can't run rsync bash script with cron]("http://ubuntuforums.org/showthread.php?t=1218412") led me to add the following to my bash script:

```
export SSH_AUTH_SOCK=/run/user/1000/keyring/ssh
```

That seemed to solve the problem - (will mark as solved? - unless there is something wrong / bad about this).  It would be good to know why / how this works though, if someone want to elaborate?

---

### Post by Lars Noodén on 2015-06-10
> **djmac said:**
> Okay.  A bit of googling and this thread [Can't run rsync bash script with cron]("http://ubuntuforums.org/showthread.php?t=1218412") led me to add the following to my bash script:

```
export SSH_AUTH_SOCK=/run/user/1000/keyring/ssh
```

That seemed to solve the problem - (will mark as solved? - unless there is something wrong / bad about this).  It would be good to know why / how this works though, if someone want to elaborate?

You have the loaded the key into the agent and are using it that way, I would guess. The variable [SSH_AUTH_SOCK](http://manpages.ubuntu.com/manpages/trusty/en/man1/ssh-add.1.html) is needed because it points programs to the [socket](http://manpages.ubuntu.com/manpages/trusty/en/man7/unix.7.html) they can use to communicate with the agent.  The agent used is [ssh-agent](http://manpages.ubuntu.com/manpages/trusty/en/man1/ssh-agent.1.html), at least for 14.04.  You can see if it was started for your user automatically when you logged in.

```

 ps axjf | less

```

If that is not it, then you can see with [lsof](http://manpages.ubuntu.com/manpages/trusty/en/man8/lsof.8.html) what is using that socket.  

Whichever account(s) can read and write to the socket can use the keys in that particular agent.  Usually there is one agent per user, but root could use the socket too.

---

