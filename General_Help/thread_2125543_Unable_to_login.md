---
title: "Unable to login"
date: 2013-03-14
forum: General Help
---

### Post by dbclinton on 2013-03-14
Hello,
For some reason, my attempt to login to my account this morning failed (I'm using 12.04 and gnome-fallback). The other users on the system are all accessible, but I can't get in (and, as I'm the only admin user, that can be a pain). 
Visual symptom: when I enter my password correctly the login screen disappears and reappears. It will catch an incorrect password attempt as normal.
auth.log output:
> Mar 14 08:47:12 dbclinton lightdm: pam_unix(lightdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost=  user=dbclinton
Mar 14 08:47:12 dbclinton lightdm: pam_winbind(lightdm:auth): getting password (0x00000388)
Mar 14 08:47:12 dbclinton lightdm: pam_winbind(lightdm:auth): pam_get_item returned a password
Mar 14 08:47:12 dbclinton lightdm: pam_winbind(lightdm:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Mar 14 08:47:15 dbclinton lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "dbclinton"
Mar 14 08:47:20 dbclinton lightdm: pam_unix(lightdm:session): session closed for user lightdm
Mar 14 08:47:20 dbclinton lightdm: pam_unix(lightdm:session): session opened for user dbclinton by (uid=0)
Mar 14 08:47:20 dbclinton lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Mar 14 08:47:20 dbclinton lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0)
Mar 14 08:47:20 dbclinton lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Mar 14 08:47:21 dbclinton lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "dbclinton"
Mar 14 08:47:21 dbclinton dbus[650]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.53" (uid=104 pid=3037 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.17" (uid=0 pid=1492 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Mar 14 08:47:24 dbclinton lightdm: pam_succeed_if(lightdm:auth): requirement "user ing
auth.log output from my attempt to login from a thin client on my network:
> tail -f auth.log 
Mar 14 09:33:07 dbclinton sshd[3997]: Connection closed by 192.168.0.28 [preauth]
Mar 14 09:33:08 dbclinton sshd[3999]: Connection closed by 192.168.0.28 [preauth]
Mar 14 09:33:13 dbclinton sshd[4001]: Accepted password for dbclinton from 192.168.0.28 port 44917 ssh2
Mar 14 09:33:13 dbclinton sshd[4001]: pam_unix(sshd:session): session opened for user dbclinton by (uid=0)
Mar 14 09:33:14 dbclinton sshd[4154]: subsystem request for sftp by user dbclinton
Mar 14 09:33:15 dbclinton sshd[4154]: Received disconnect from 192.168.0.28: 11: disconnected by user
Mar 14 09:33:15 dbclinton sshd[4001]: pam_unix(sshd:session): session closed for user dbclinton

I have no idea why pam_winbind is showing up here. I'm not using Samba on my system.

Any ideas?
Thanks,

---

### Post by schragge on 2013-03-14
Seems you somehow managed to have installed *libpam-winbind* and/or *winbind4*. Try to uninstall them.
```
sudo apt-get remove winbind\*
```

---

### Post by dbclinton on 2013-03-14
> **schragge said:**
> Seems you somehow managed to have installed *libpam-winbind* and/or *winbind4*. Try to uninstall them.
```
sudo apt-get remove winbind\*
```

Thanks. I came across this suggestion via google, but I wasn't 100% sure it was applicable to me. 
Now I'll take the plunge!
David

---

### Post by dbclinton on 2013-03-14
Unfortunately, removing (and purging) winbind didn't help me login. Here's some new output from my latest attempts (via thin client):
> syslog
Mar 14 12:36:25 dbclinton ldminfod[4038]: connect from 192.168.0.26 (192.168.0.26)
Mar 14 12:36:26 dbclinton nbd_server[1914]: connect from 192.168.0.26, assigned file is /opt/ltsp/images/i386.img
Mar 14 12:36:26 dbclinton nbd_server[1914]: Can't open authorization file (null) (Bad address).
Mar 14 12:36:26 dbclinton nbd_server[1914]: Authorized client
Mar 14 12:36:26 dbclinton nbd_server[4051]: Starting to serve
Mar 14 12:36:26 dbclinton nbd_server[4051]: Size of exported file/device is 266027008
Mar 14 12:36:26 dbclinton nbd_server[4051]: Disconnect request received.
Mar 14 12:36:26 dbclinton nbd_server[1914]: Child exited with 0

auth.log 
Mar 14 12:34:46 dbclinton sshd[3385]: Accepted password for dbclinton from 192.168.0.28 port 55687 ssh2
Mar 14 12:34:46 dbclinton sshd[3385]: pam_unix(sshd:session): session opened for user dbclinton by (uid=0)
Mar 14 12:34:46 dbclinton sshd[3516]: Received disconnect from 192.168.0.28: 11: disconnected by user
Mar 14 12:34:46 dbclinton sshd[3385]: pam_unix(sshd:session): session closed for user dbclinton
Mar 14 12:35:54 dbclinton sshd[3567]: Connection closed by 192.168.0.26 [preauth]

---

### Post by dbclinton on 2013-03-14
And this is from my latest attempt to login directly to the server:
> Mar 14 12:28:33 dbclinton lightdm: pam_unix(lightdm:session): session opened for user dbclinton by (uid=0)
Mar 14 12:28:33 dbclinton lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Mar 14 12:28:33 dbclinton lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0)
Mar 14 12:28:33 dbclinton lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Mar 14 12:28:34 dbclinton lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "dbclinton"
Mar 14 12:28:34 dbclinton dbus[747]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.49" (uid=104 pid=2632 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.21" (uid=0 pid=1679 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Thanks

---

### Post by steeldriver on 2013-03-14
what does your ~/.xsession-errors say? have you checked the directory permissions on your home dir and the ownership / permissions on ~/.Xauthority?

---

### Post by dbclinton on 2013-03-14
> **steeldriver said:**
> what does your ~/.xsession-errors say? have you checked the directory permissions on your home dir and the ownership / permissions on ~/.Xauthority?

Here's the begining of xsessions-errors:
> MainThread 2013/03/12 08:16:17.4961 (sabayon-apply): No profile for user 'dbclinton' found
No profile for user 'dbclinton' found
MainThread 2013/03/12 08:16:17.4963 (sabayon-apply): Fatal exception!  Exiting abnormally.
MainThread 2013/03/12 08:16:17.4964 (sabayon-apply): Traceback (most recent call last):
  File "/usr/sbin/sabayon-apply", line 149, in <module>
    sys.exit (util.EXIT_CODE_NO_USER_PROFILE)
SystemExit: 3

===== BEGIN MILESTONES (/usr/sbin/sabayon-apply) =====
MainThread 2013/03/12 08:16:17.4961 (sabayon-apply): No profile for user 'dbclinton' found
MainThread 2013/03/12 08:16:17.4963 (sabayon-apply): Fatal exception!  Exiting abnormally.
MainThread 2013/03/12 08:16:17.4964 (sabayon-apply): Traceback (most recent call last):
  File "/usr/sbin/sabayon-apply", line 149, in <module>
    sys.exit (util.EXIT_CODE_NO_USER_PROFILE)
SystemExit: 3
Why would my login have no profile? My account certainly still exists...that's what I am currently using via su to manage the system. And my password is also still unchanged...

And here are the permissions for my .Xauthority:
> dbclinton@dbclinton:~$ ls -l .Xauthority
-rw------- 1 root root 54 Mar 13 17:36 .Xauthority

Is it supposed to be owned by root? It doesn't quite seem right...

---

### Post by dbclinton on 2013-03-14
And here are the permissions on my home folder:
> dbclinton@dbclinton:/home$ ls -l | grep dbclinton
drwxr-x--- 99 dbclinton dbclinton 12288 Mar 14 12:57 dbclinton


I noticed that the other users are drwxr-xr-x
Should mine be that way too?

---

### Post by dbclinton on 2013-03-14
> **steeldriver said:**
> ownership / permissions on ~/.Xauthority?

That was it! I used chown to move my .Xauthority back from root ownership and I'm back in!
I would still love to know how this happened in the first place. Does anyone know if there were any updates over the past 48 hours that could have done this?
Thanks a million!

---

### Post by schragge on 2013-03-14
This could have happened, e.g. if you started X as root from command line like *sudo startx*
Here is a good explanation why you should never use sudo with GUI applications:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by schragge on 2013-03-14
[size=-1]*double-post: content removed*[/size]

---

### Post by dbclinton on 2013-03-14
> **schragge said:**
> This could have happened, e.g. if you started X as root from command line like *sudo startx*
Here is a good explanation why you should never use sudo with GUI applications:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

That's exactly what happened! I had always wondered what startx would do... :)
Who says that Ubuntu doesn't come with great support?

---

