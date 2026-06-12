---
title: "Very slow terminal login"
date: 2008-03-26
forum: General Help
---

### Post by CheShA on 2008-03-26
One of my boxes has suddenly started taking an age to complete a login / su.  It takes about 90 seconds after entering the password to get the prompt back from **su**.

Logging in  via ** ssh -vvvv** , it does all the negotiation fine, then hangs at this point before completeing the process fine:

```
debug1: Next authentication method: password
chesha@myserver's password: 
debug3: packet_send2: adding 48 (len 69 padlen 11 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug1: Entering interactive session.

#######HANGS FOR 60-90 seconds #######

debug2: callback start
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 0
etc...

```

I've tried watching 
tail-f /var/log/auth.log
tail-f /var/log/syslog
tail-f /var/log/messages
tail -f /var/log/user.log

.. through the process, but none of them show anything.  Does anyone have any ideas for anywhere else i can look?

Thanks

---

### Post by pointone on 2008-03-26
Have you edited your /etc/nsswitch.conf file?

---

### Post by CheShA on 2008-03-27
Hi Pointone, thanks for your reply.

No i haven't edited this at all, I checked this before and it is as default (?):
```

passwd:         compat
group:          compat
shadow:         compat

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

It's weird because I haven't made any significant changes to this box recently, I hadn't even updated this box for a week or two at the point when this started happening.

I have, however added a user but /etc/passwd /etc/group and /etc/shadow look A-OK.  I have also configured ssh for use with RSA authentication, but this problem isn't just affecting ssh,  it affects any kind of login, even just *su*.

---

### Post by pointone on 2008-03-27
Check /var/log/auth.log; this contains whatever is logged by PAM. If you can't find any hints, you could add the debug/audit option to your PAM stack.

Edit /etc/pam.d/common-*, and add "debug" or "audit" (audit is more extreme) to the pam_unix instances.

For example, my common-auth reads:

```
auth    required    pam_unix.so nullok_secure
```

Change it to:

```
auth    required    pam_unix.so nullok_secure debug
```

Do this for common-auth, common-session, and common-account. common-password shouldn't be the problem--it's only called for password changes.

---

### Post by CheShA on 2008-04-01
Hi man,

thanks for the pointers, that sounds like it will be enough to get me moving - I'll have a dig around today.

---

### Post by CheShA on 2008-04-01
I have set these all to audit but they aren't giving much away. Interestingly, the auth.log seems to be running behind what I am seeing at the terminal. I have added some timestamps to the following logs to show what was happening at the command line:
```

Apr  1 13:05:49 CheShA: su typed at root prompt
Apr  1 13:06:26 CheShA: prompt reappears
Apr  1 13:06:45 myserver su[12372]: Successful su for root by root
Apr  1 13:06:54 myserver su[12372]: + pts/2 root:root
Apr  1 13:07:08 myserver su[12372]: pam_unix(su:session): session opened for user root by chesha(uid=0)

Apr  1 13:08:17 CheShA: exit typed at root prompt
Apr  1 13:08:31 CheShA: prompt reappears
Apr  1 13:09:27 myserver su[12372]: pam_unix(su:session): session closed for user root

```

---

### Post by CheShA on 2008-04-01
DOH

I see from [here ]("http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/sag-pam_unix.html") that debugging out put goes into syslog.. I'm barking up the wrong tree. I will have another root around. :-/

---

### Post by CheShA on 2008-04-01
I think i may also have found something else interesting.... it seems as though the more times I log in the slower it gets - the first login to the machine after a reboot is quick, then after that the amount of time it takes gets progressively longer....

---

### Post by jmcochran21 on 2008-06-05
I am having the exact same problem with my Ubuntu system, any suggestions on other places to look? I've rooted around in auth.log and syslog trying to find some clue but have come up empty handed.

---

### Post by CheShA on 2008-06-06
Sorry man, I didn't end up fixing this. Something else broke and I just ended up rebuilding this server.

---

