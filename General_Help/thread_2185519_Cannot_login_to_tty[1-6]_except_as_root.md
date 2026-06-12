---
title: "Cannot login to tty[1-6] except as root"
date: 2013-11-03
forum: General Help
---

### Post by bhh1988 on 2013-11-03
Hello,

When I press [Ctrl+Alt+F<1-6>] it takes me to tty1 through tty6 respectively, no problem. But at the login prompt, if I try to login with my username and password, it just immediately takes me back to the same login prompt. The only way I can actually log in to the console is as root.

Here're the relevant lines from my /var/log/auth.log

Nov  2 21:03:04 bhh1988-H67MA-USB3-B3 login[3116]: pam_unix(login:session): session opened for user bhh1988 by LOGIN(uid=0)
Nov  2 21:03:04 bhh1988-H67MA-USB3-B3 login[3116]: pam_unix(login:session): session closed for user bhh1988
Nov  2 21:03:53 bhh1988-H67MA-USB3-B3 login[5546]: pam_unix(login:session): session opened for user root by bhh1988(uid=0)
Nov  2 21:03:53 bhh1988-H67MA-USB3-B3 login[8258]: ROOT LOGIN  on '/dev/tty1'

You see that at 21:03:04 I try to login as bhh1988, but the session just opens and immediately closes. About 50 seconds later I tried logging in as root, which is successful. Interestingly it says that the session was opened by bhh1988 (my username) though.

I also checked out /var/log/syslog and /var/log/kern.log. At the time of the login failure, I see the line:

Nov  2 21:03:04 bhh1988-H67MA-USB3-B3 kernel: [ 1430.218803] init: tty1 main process ended, respawning

Any idea what's going on, or what else I can look at for more clues?

I am on 12.04

---

### Post by CatKiller on 2013-11-03
By default you can't login as root at all, so you've clearly been fiddling with stuff. Some indication of what it is that you've done might help someone work out where you've gone wrong.

---

### Post by bhh1988 on 2013-11-04
Hmm. I don't ever remember fiddling with login-related things. What are some things that I could post that might be useful?

Here's my /etc/pam.d/login file:

> #
# The PAM configuration file for the Shadow `login' service
#

# Enforce a minimal delay in case of failure (in microseconds).
# (Replaces the `FAIL_DELAY' setting from login.defs)
# Note that other modules may require another minimal delay. (for example,
# to disable any delay, you should add the nodelay option to pam_unix)
auth       optional   pam_faildelay.so  delay=3000000

# Outputs an issue file prior to each login prompt (Replaces the
# ISSUE_FILE option from login.defs). Uncomment for use
# auth       required   pam_issue.so issue=/etc/issue

# Disallows root logins except on tty's listed in /etc/securetty
# (Replaces the `CONSOLE' setting from login.defs)
#
# With the default control of this module:
#   [success=ok new_authtok_reqd=ok ignore=ignore user_unknown=bad default=die]
# root will not be prompted for a password on insecure lines.
# if an invalid username is entered, a password is prompted (but login
# will eventually be rejected)
#
# You can change it to a "requisite" module if you think root may mis-type
# her login and should not be prompted for a password in that case. But
# this will leave the system as vulnerable to user enumeration attacks.
#
# You can change it to a "required" module if you think it permits to
# guess valid user names of your system (invalid user names are considered
# as possibly being root on insecure lines), but root passwords may be
# communicated over insecure lines.
auth [success=ok new_authtok_reqd=ok ignore=ignore user_unknown=bad default=die] pam_securetty.so

# Disallows other than root logins when /etc/nologin exists
# (Replaces the `NOLOGINS_FILE' option from login.defs)
auth       requisite  pam_nologin.so

# SELinux needs to be the first session rule. This ensures that any 
# lingering context has been cleared. Without out this it is possible 
# that a module could execute code in the wrong domain.
# When the module is present, "required" would be sufficient (When SELinux
# is disabled, this returns success.)
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so close

# This module parses environment configuration file(s)
# and also allows you to use an extended config
# file /etc/security/pam_env.conf.
# 
# parsing /etc/environment needs "readenv=1"
session       required   pam_env.so readenv=1
# locale variables are also kept into /etc/default/locale in etch
# reading this file *in addition to /etc/environment* does not hurt
session       required   pam_env.so readenv=1 envfile=/etc/default/locale

# Standard Un*x authentication.
@include common-auth

# This allows certain extra groups to be granted to a user
# based on things like time of day, tty, service, and user.
# Please edit /etc/security/group.conf to fit your needs
# (Replaces the `CONSOLE_GROUPS' option in login.defs)
auth       optional   pam_group.so

# Uncomment and edit /etc/security/time.conf if you need to set
# time restrainst on logins.
# (Replaces the `PORTTIME_CHECKS_ENAB' option from login.defs
# as well as /etc/porttime)
# account    requisite  pam_time.so

# Uncomment and edit /etc/security/access.conf if you need to
# set access limits.
# (Replaces /etc/login.access file)
# account  required       pam_access.so

# Sets up user limits according to /etc/security/limits.conf
# (Replaces the use of /etc/limits in old login)
session    required   pam_limits.so

# Prints the last login info upon succesful login
# (Replaces the `LASTLOG_ENAB' option from login.defs)
session    optional   pam_lastlog.so

# Prints the motd upon succesful login
# (Replaces the `MOTD_FILE' option in login.defs)
session    optional   pam_motd.so

# Prints the status of the user's mailbox upon succesful login
# (Replaces the `MAIL_CHECK_ENAB' option from login.defs). 
#
# This also defines the MAIL environment variable
# However, userdel also needs MAIL_DIR and MAIL_FILE variables
# in /etc/login.defs to make sure that removing a user 
# also removes the user's mail spool file.
# See comments in /etc/login.defs
session    optional   pam_mail.so standard

# Standard Un*x account and session
@include common-account
@include common-session
@include common-password

# SELinux needs to intervene at login time to ensure that the process
# starts in the proper default security context. Only sessions which are
# intended to run in the user's context should be run after this.
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so open
# When the module is present, "required" would be sufficient (When SELinux
# is disabled, this returns success.)

The only thing that jumps out at me from this login file is the part that says:

> # Disallows other than root logins when /etc/nologin exists
# (Replaces the `NOLOGINS_FILE' option from login.defs)
auth       requisite  pam_nologin.so

But I don't have an /etc/nologin so that doesn't appear to me the culprit.

---

