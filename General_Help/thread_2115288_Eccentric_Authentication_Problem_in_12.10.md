---
title: "Eccentric Authentication Problem in 12.10"
date: 2013-02-12
forum: General Help
---

### Post by Hanine on 2013-02-12
This might be a duplicate of other password related questions but it's somehow eccentric.
  I have three accounts in my **Ubuntu 12.10** system (one  standard and two administrators). One of the administrator accounts is  my main development account and suddenly before yesterday, it started to  act weird (since the latest updates - Kernel and others:
  
[LIST]
[*]At the **greeter stage**, when I enter my password, it  instantly returns 'Incorrect password'. It does not even check. (N.B:  The password is absolutely correct)
[*]At **TTY**, impossible to login, once I enter my login  name and then the password, it instantly re-prompts me to enter the  login name...It feels like tha path to authenticate this account has  been accidently locked or access-sealed.
[/LIST]
  I logged in with my second admin account and changed the password for  the troublesome account, but no luck, reverted the password back to its  original value and set the account to auto-login. rebooted and then,  indeed the account logged in. Yet, the abonormality remains:
  
[LIST]
[*]I **cannot perform root privilege actions (sudo & gksudo)**.  Once I enter my password, nothing happens. The only time when the  password is accepted is when the screen is locked and that I am prompted  to enter the password to unlock it.
[/LIST]
  

I checked the sudoers file an dit's fine (permission and content).
I also checked that my username belongs to sudo and admin groups.
So basically, it feels like it is an authentication problem related to credentials of this account. A wrong permission can be the cause of this but how in the world would I know which file or which folder. :(



I checked the ownership of my home folder and it's okay. I have no clue why this is happening. Some help is very appreciated.
    *Ubuntu 12.10 Unity uname: Linux l502x 3.5.0-23-generic #35-Ubuntu SMP Thu Jan 24 13:15:40 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux*

---

### Post by matt_symes on 2013-02-12
Hi
 
Can you use su ?
 
What does /var/log/auth.log say ?
 
Have you checked PAM ?
 
Can you use pkexec ?
 
Kind regards

---

### Post by Hanine on 2013-02-13
Hello,

[LIST]
[*]I cannot use su.
[*]the auth.log says nothing useful.
[*]the PAM directory contains common files, I read them and found nothing suspicious.
[/LIST]

[LIST]
[*]I cannot run pkexec (when pkexec prompts me for the password and I enter the password, it returns "Authentication failure".
[*]As I mentioned, I have three accounts, two of them work fine for authentication actions and login. The third and main one has this big issue.
[/LIST]
Here is some content of the auth.log:


```
Feb 12 03:20:36 l502x passwd[4911]: pam_smbpass(passwd:chauthtok): Failed to find entry for user hanine.
Feb 12 03:20:47 l502x passwd[4911]: pam_unix(passwd:chauthtok): password changed for hanine
Feb 12 03:20:47 l502x passwd[4911]: pam_smbpass(passwd:chauthtok): Failed to find entry for user hanine.
Feb 12 03:21:05 l502x lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "hanine"
Feb 12 03:21:05 l502x lightdm: pam_unix(lightdm:auth): auth could not identify password for [hanine]
Feb 12 03:21:05 l502x lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "hanine"
Feb 12 03:21:06 l502x lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "hanine"
Feb 12 03:21:38 l502x lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "hanine"
Feb 12 03:21:43 l502x lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "hanine"
Feb 12 03:23:36 l502x sudo:    admin : TTY=pts/0 ; PWD=/home/hanine ; USER=root ; COMMAND=/usr/bin/passwd hanine
Feb 12 03:23:36 l502x passwd[5502]: pam_smbpass(passwd:chauthtok): Failed to find entry for user hanine.
Feb 12 03:23:52 l502x passwd[5502]: pam_unix(passwd:chauthtok): password changed for hanine
Feb 12 03:23:52 l502x passwd[5502]: pam_smbpass(passwd:chauthtok): Failed to find entry for user hanine.
Feb 12 03:24:17 l502x sudo:    admin : TTY=pts/0 ; PWD=/home/hanine ; USER=root ; COMMAND=/usr/bin/passwd hanine
Feb 12 03:24:17 l502x passwd[5520]: pam_smbpass(passwd:chauthtok): Failed to find entry for user hanine.
Feb 12 03:24:24 l502x passwd[5520]: pam_unix(passwd:chauthtok): password changed for hanine
Feb 12 03:24:24 l502x passwd[5520]: pam_smbpass(passwd:chauthtok): Failed to find entry for user hanine.
Feb 12 03:27:51 l502x sudo:    admin : TTY=pts/0 ; PWD=/home/hanine ; USER=root ; COMMAND=/bin/rm .xsession-errors
Feb 12 03:28:42 l502x sudo:    admin : TTY=pts/0 ; PWD=/home/hanine ; USER=root ; COMMAND=/bin/rm .Xauthority
Feb 12 03:29:22 l502x sudo:    admin : TTY=pts/0 ; PWD=/home/hanine ; USER=root ; COMMAND=/bin/mkdir .xsession-errors-old-files
Feb 12 03:29:36 l502x sudo:    admin : TTY=pts/0 ; PWD=/home/hanine ; USER=root ; COMMAND=/bin/mv .xsession-errors.old .xsession-errors_OLD1 .xsession-errors-old-files .xsession-errors-old-files/
Feb 12 03:34:15 l502x sudo:    admin : TTY=pts/2 ; PWD=/home/hanine ; USER=root ; COMMAND=/usr/bin/sakis3g connect
Feb 12 14:10:08 l502x lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "hanine"
Feb 12 14:10:15 l502x lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "hanine"
Feb 12 14:13:23 l502x accounts-daemon: request by system-bus-name::1.66 [gnome-control-center user-accounts pid:3028 uid:1001]: enable automatic login for user 'hanine' (1000)
Feb 12 14:16:54 l502x lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "hanine"
Feb 12 14:16:54 l502x lightdm: pam_unix(lightdm:auth): auth could not identify password for [hanine]
Feb 12 14:16:55 l502x lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "hanine"
Feb 12 14:16:55 l502x lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "hanine"
Feb 12 14:16:57 l502x lightdm: pam_unix(lightdm:auth): authentication failure; logname= uid=0 euid=0 tty=:1 ruser= rhost=  user=hanine
Feb 12 14:16:59 l502x lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "hanine"
Feb 12 14:17:43 l502x lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "hanine"
Feb 12 14:18:00 l502x lightdm: pam_unix(lightdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost=  user=hanine
Feb 12 14:18:02 l502x lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "hanine"
Feb 12 14:18:06 l502x lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "hanine"
Feb 12 14:18:14 l502x lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "hanine"
Feb 12 14:18:17 l502x lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "hanine"
Feb 12 14:19:05 l502x lightdm: pam_unix(lightdm-autologin:session): session opened for user hanine by (uid=0)
Feb 12 14:20:04 l502x gnome-keyring-daemon[2173]: keyring alias directory: /home/hanine/.local/share/keyrings
Feb 12 14:50:18 l502x gnome-screensaver-dialog: pam_unix(gnome-screensaver:auth): authentication failure; logname= uid=1000 euid=1000 tty=:0.0 ruser= rhost=  user=hanine
Feb 12 14:55:48 l502x sudo:    admin : TTY=pts/3 ; PWD=/home/admin ; USER=root ; COMMAND=/bin/chown hanine:hanine /home/hanine/
Feb 12 14:59:22 l502x polkitd(authority=local): Operator of unix-session:/org/freedesktop/ConsoleKit/Session1 successfully authenticated as unix-user:admin to gain TEMPORARY authorization for action com.ubuntu-tweak.daemon.clean for system-bus-name::1.138 [/usr/bin/python /usr/bin/ubuntu-tweak] (owned by unix-user:hanine)
Feb 12 15:56:26 l502x polkitd(authority=local): Operator of unix-session:/org/freedesktop/ConsoleKit/Session1 FAILED to authenticate to gain authorization for action org.gnome.controlcenter.user-accounts.administration for unix-process:10018:582882 [gnome-control-center user-accounts] (owned by unix-user:hanine)
Feb 12 16:16:41 l502x sudo:    admin : TTY=tty2 ; PWD=/home/admin ; USER=root ; COMMAND=/usr/sbin/adduser hanine sudo
Feb 12 16:16:49 l502x sudo:    admin : TTY=tty2 ; PWD=/home/admin ; USER=root ; COMMAND=/usr/sbin/adduser hanine admin
Feb 12 16:16:49 l502x gpasswd[17020]: user hanine added by root to group admin
Feb 12 17:11:49 l502x lightdm: pam_unix(lightdm-autologin:session): session closed for user hanine
Feb 12 17:11:49 l502x lightdm: pam_xdg_support(lightdm-autologin:session): Could not delete directory /run/user/hanine
Feb 12 17:23:58 l502x lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "hanine"
Feb 12 17:23:58 l502x lightdm: pam_unix(lightdm:auth): auth could not identify password for [hanine]
Feb 12 17:23:58 l502x lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "hanine"
Feb 12 17:23:59 l502x lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "hanine"
Feb 12 17:24:04 l502x lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "hanine"
Feb 12 17:24:08 l502x lightdm: pam_unix(lightdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost=  user=hanine
Feb 12 17:24:10 l502x lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "hanine"
Feb 12 17:25:36 l502x lightdm: pam_unix(lightdm-autologin:session): session opened for user hanine by (uid=0)
Feb 12 17:26:29 l502x gnome-keyring-daemon[2147]: keyring alias directory: /home/hanine/.local/share/keyrings
Feb 12 17:42:29 l502x sudo:    admin : TTY=pts/2 ; PWD=/home/admin ; USER=root ; COMMAND=/bin/chown -R hanine:hanine /home/hanine
Feb 12 17:47:36 l502x gnome-screensaver-dialog: pam_unix(gnome-screensaver:auth): authentication failure; logname= uid=1000 euid=1000 tty=:0.0 ruser= rhost=  user=hanine
Feb 12 17:56:14 l502x su[17624]: pam_unix(su:auth): authentication failure; logname=hanine uid=1000 euid=0 tty=/dev/pts/4 ruser=hanine rhost=  user=root
Feb 12 17:56:16 l502x su[17624]: FAILED su for root by hanine
Feb 12 17:56:16 l502x su[17624]: - /dev/pts/4 hanine:root
Feb 12 17:56:57 l502x su[17888]: pam_unix(su:auth): authentication failure; logname=hanine uid=1000 euid=0 tty=/dev/pts/4 ruser=hanine rhost=  user=root
Feb 12 17:56:59 l502x su[17888]: FAILED su for root by hanine
Feb 12 17:56:59 l502x su[17888]: - /dev/pts/4 hanine:root
Feb 12 17:59:07 l502x polkitd(authority=local): Operator of unix-session:/org/freedesktop/ConsoleKit/Session1 FAILED to authenticate to gain authorization for action org.freedesktop.policykit.exec for unix-process:16882:180734 [bash] (owned by unix-user:hanine)
Feb 12 17:59:07 l502x pkexec[18604]: hanine: Error executing command as another user: Request dismissed [USER=root] [TTY=/dev/pts/4] [CWD=/home/hanine] [COMMAND=/usr/bin/gedit]
Feb 12 18:17:33 l502x lightdm: pam_unix(lightdm-autologin:session): session closed for user hanine
Feb 12 18:17:33 l502x lightdm: pam_xdg_support(lightdm-autologin:session): Could not delete directory /run/user/hanine
Feb 12 18:32:48 l502x lightdm: pam_unix(lightdm-autologin:session): session opened for user hanine by (uid=0)
Feb 12 18:33:39 l502x gnome-keyring-daemon[2142]: keyring alias directory: /home/hanine/.local/share/keyrings
Feb 12 19:05:48 l502x lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "hanine"
Feb 12 19:07:38 l502x sudo:    admin : TTY=pts/2 ; PWD=/home/admin ; USER=root ; COMMAND=/usr/bin/passwd hanine
Feb 12 19:07:38 l502x passwd[17421]: pam_smbpass(passwd:chauthtok): Failed to find entry for user hanine.
Feb 12 19:07:44 l502x passwd[17421]: pam_unix(passwd:chauthtok): password changed for hanine
Feb 12 19:07:44 l502x passwd[17421]: pam_smbpass(passwd:chauthtok): Failed to find entry for user hanine.
Feb 12 19:08:03 l502x lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "hanine"
Feb 12 19:08:13 l502x lightdm: pam_unix(lightdm:auth): authentication failure; logname= uid=0 euid=0 tty=:1 ruser= rhost=  user=hanine
Feb 12 19:08:15 l502x lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "hanine"
Feb 12 19:08:18 l502x lightdm: pam_unix(lightdm:auth): authentication failure; logname= uid=0 euid=0 tty=:1 ruser= rhost=  user=hanine
Feb 12 19:08:20 l502x lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "hanine"
Feb 12 19:09:47 l502x lightdm: pam_unix(lightdm-autologin:session): session opened for user hanine by (uid=0)
Feb 12 19:10:39 l502x gnome-keyring-daemon[2099]: keyring alias directory: /home/hanine/.local/share/keyrings
Feb 12 19:11:27 l502x sudo: pam_unix(sudo:auth): authentication failure; logname=hanine uid=1000 euid=0 tty=/dev/pts/0 ruser=hanine rhost=  user=hanine
Feb 12 19:12:31 l502x sudo:    admin : TTY=pts/1 ; PWD=/home/admin ; USER=root ; COMMAND=/usr/bin/passwd hanine
Feb 12 19:12:31 l502x passwd[4491]: pam_smbpass(passwd:chauthtok): Failed to find entry for user hanine.
Feb 12 19:12:38 l502x passwd[4491]: pam_unix(passwd:chauthtok): password changed for hanine
Feb 12 19:12:38 l502x passwd[4491]: pam_smbpass(passwd:chauthtok): Failed to find entry for user hanine.
Feb 12 22:44:16 l502x sudo: pam_unix(sudo:auth): authentication failure; logname=hanine uid=1000 euid=0 tty=/dev/pts/0 ruser=hanine rhost=  user=hanine
Feb 13 13:24:01 l502x lightdm: pam_unix(lightdm-autologin:session): session opened for user hanine by (uid=0)
Feb 13 13:24:52 l502x gnome-keyring-daemon[2061]: keyring alias directory: /home/hanine/.local/share/keyrings
Feb 13 13:40:49 l502x polkitd(authority=local): Operator of unix-session:/org/freedesktop/ConsoleKit/Session1 FAILED to authenticate to gain authorization for action org.freedesktop.policykit.exec for unix-process:3554:15127 [bash] (owned by unix-user:hanine)
Feb 13 13:40:49 l502x pkexec[8783]: hanine: Error executing command as another user: Request dismissed [USER=root] [TTY=/dev/pts/0] [CWD=/home/hanine] [COMMAND=/usr/bin/apt-get update]
Feb 13 13:49:13 l502x polkitd(authority=local): Operator of unix-session:/org/freedesktop/ConsoleKit/Session1 FAILED to authenticate to gain authorization for action org.freedesktop.policykit.exec for unix-process:10395:133011 [bash] (owned by unix-user:hanine)
Feb 13 13:49:13 l502x pkexec[11324]: hanine: Error executing command as another user: Request dismissed [USER=root] [TTY=/dev/pts/2] [CWD=/home/hanine] [COMMAND=/usr/bin/gedit]
```


to summarize:
- commands preceeded by sudo or gksudo or pkexec fail immediately.
- login with this account fails immediately (the pasword is correct, but it seems like this account has been blacklisted somehow, due to an accidental wrong permission or another command).
- the password is accepted only when I am prompted after an autologin to enter it for keyring unlocking and when I am prompted to unlock the screen after a inactivity.



Regards.

---

### Post by schragge on 2013-02-13
Do *getent passwd hanine* and *sudo getent shadow hanine* work? Do not post the output here, just check if they work.

---

### Post by Hanine on 2013-02-13
the **first one  works** (*getent passwd hanine*) and it returns the same entry as in /etc/passwd
while the s**econd command does return nothing** (*sudo getent shadow hanine*) (obvious :( since sudo command fails silently).

---

### Post by schragge on 2013-02-13
But does it work from another account? I mean does *sudo getent shadow hanine* work when you're logged in **not** as *hanine*?

---

### Post by Hanine on 2013-02-13
Yes it does when I am logged in as another admin account.

---

### Post by schragge on 2013-02-13
First, check that *smbpasswd* is installed (*which smbpasswd*). If not, install the package *samba-common-bin*. Then, add *hanine* to Samba's *passwd.tlb* (*smbpasswd -a hanine*).

If that doesn't help, try to add the 'debug' or 'audit' options to the *pam_smbpass.so* lines in */usr/share/pam-configs/smbpasswd-migrate*, then *sudo pam-auth-update*, and watch for anything suspicious from pam_smbpass.so in */var/log/auth.log*, or other log files.

---

### Post by Hanine on 2013-02-13
> **schragge said:**
> First, check that *smbpasswd* is installed (*which smbpasswd*). If not, install the package *samba-common-bin*. Then, add *hanine* to Samba's *passwd.tlb* (*smbpasswd -a hanine*).

If that doesn't help, try to add the 'debug' or 'audit' options to the *pam_smbpass.so* lines in */usr/share/pam-configs/smbpasswd-migrate*, then *sudo pam-auth-update*, and watch for anything suspicious from pam_smbpass.so in */var/log/auth.log*, or other log files.

smbpasswd is installed, so is samba-common-bin. 
When tried to add hanine to samba passwd: 

```
sudo smbpasswd -a hanine
Failed to open /var/lib/samba/secrets.tdb
Failed to open /var/lib/samba/secrets.tdb
PANIC (pid 18804): could not open secrets db
BACKTRACE: 6 stack frames:
 #0 smbpasswd(log_stack_trace+0x1a) [0x7f411d508a3a]
 #1 smbpasswd(smb_panic+0x22) [0x7f411d508b12]
 #2 smbpasswd(get_global_sam_sid+0x5c1) [0x7f411d424e81]
 #3 smbpasswd(main+0x47e) [0x7f411d3c02be]
 #4 /lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xed) [0x7f411ab2776d]
 #5 smbpasswd(+0xab995) [0x7f411d3c0995]
smb_panic(): calling panic action [/usr/share/samba/panic-action 18804]
smb_panic(): action returned status 0
Can not dump core: corepath not set up
admin@l502x:~$ sudo touch /var/lib/samba/secrets.tlb
touch: cannot touch `/var/lib/samba/secrets.tlb': No such file or directory
admin@l502x:~$ sudo mkdir -p /var/lib/samba/
admin@l502x:~$ sudo touch /var/lib/samba/secrets.tlb
admin@l502x:~$ sudo smbpasswd -a hanine
New SMB password:
Retype new SMB password:
Added user hanine.
admin@l502x:~$
``` 

I ll be debugging again and feedback right away.

---

### Post by Hanine on 2013-02-13
Surprise. It is working now. I can finally login and perform root actions.

Here are the actions I carried out before the problem got solved:


[LIST=1]
[*]- **sudo ppa-purge ppa:gnome3-team/gnome3 **  (in order to revert back to supported gnome packages like nautilus, ...etc)
[*]- creating directory : **/var/lib/samba/** and then: **sudo smbpasswd -a hanine**
[*]- **sudo pam-auth-update** (all the authentication modules were already selected, so I just cliked okay).
[/LIST]
I really thank you for your troubleshooting. I owe you one. :o

---

### Post by matt_symes on 2013-02-13
Hi

I see you both have been busy :D

Good work both of you and i'm glad it's fixed.

Kind regards

---

