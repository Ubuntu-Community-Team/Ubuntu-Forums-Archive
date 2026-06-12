---
title: "Weird login problem in Ubuntu 12.04"
date: 2014-10-01
forum: General Help
---

### Post by miguelio on 2014-10-01
I have several Administrator accounts in an Ubuntu 12.04 installation. Since today I can not access one of them from GUI. In text mode it works fine, however.

I tried the recipe found in this thread: [http://ubuntuforums.org/showthread.php?t=2115288](http://ubuntuforums.org/showthread.php?t=2115288)
but it didn't work.

This is my /var/auth.log lines for the moment I was trying to log in:

```
Oct  1 12:41:00 lis-PID-GNA-linux lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0)
Oct  1 12:41:00 lis-PID-GNA-linux lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Oct  1 12:41:00 lis-PID-GNA-linux lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "miguel"
Oct  1 12:48:42 lis-PID-GNA-linux lightdm: pam_unix(lightdm:session): session closed for user lightdm
Oct  1 12:48:43 lis-PID-GNA-linux lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0)
Oct  1 12:48:43 lis-PID-GNA-linux lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Oct  1 12:48:44 lis-PID-GNA-linux lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "miguel"
Oct  1 12:48:47 lis-PID-GNA-linux lightdm: pam_unix(lightdm:session): session closed for user lightdm
Oct  1 12:48:48 lis-PID-GNA-linux lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0)
Oct  1 12:48:48 lis-PID-GNA-linux lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Oct  1 12:48:48 lis-PID-GNA-linux lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "miguel"
Oct  1 12:49:07 lis-PID-GNA-linux lightdm: pam_unix(lightdm:session): session closed for user lightdm
Oct  1 12:49:08 lis-PID-GNA-linux lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0)
Oct  1 12:49:08 lis-PID-GNA-linux lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Oct  1 12:49:08 lis-PID-GNA-linux lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "miguel"
Oct  1 12:49:16 lis-PID-GNA-linux lightdm: pam_unix(lightdm:session): session closed for user lightdm
Oct  1 12:49:17 lis-PID-GNA-linux lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0)
Oct  1 12:49:17 lis-PID-GNA-linux lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Oct  1 12:49:18 lis-PID-GNA-linux lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "miguel"
Oct  1 12:49:31 lis-PID-GNA-linux lightdm: pam_unix(lightdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost=  user=miguel

```

Thanks

---

### Post by miguelio on 2014-10-01
Solved. The account was using Gnome-classic, which didn't work. Removing and installing again the package [COLOR=#0A0200][FONT=Arial]gnome-session-fallback[/FONT][/COLOR] did the trick.

---

