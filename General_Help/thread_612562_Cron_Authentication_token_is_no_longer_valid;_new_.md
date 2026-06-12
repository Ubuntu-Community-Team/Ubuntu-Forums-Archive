---
title: "Cron: Authentication token is no longer valid; new one required."
date: 2007-11-14
forum: General Help
---

### Post by rossigee on 2007-11-14
Root cron jobs stopped working as of about October 26th. They were working fine, then I started seeing the following in /var/log/cron.log:

Nov 14 06:18:01 jungle1 /USR/SBIN/CRON[1263]: (amavis) CMD (test -e /usr/sbin/amavisd-new-cronjob && /usr/sbin/amavisd-new-cronjob sa-sync)
Nov 14 06:25:01 jungle1 CRON[1289]: Authentication token is no longer valid; new one required.
Nov 14 06:39:01 jungle1 CRON[1327]: Authentication token is no longer valid; new one required.
Nov 14 07:09:01 jungle1 CRON[1425]: Authentication token is no longer valid; new one required.

It suggests that jobs for the 'amavis' user are still working fine, but any jobs for the 'root' user have stopped working.

I'm running NSS_LDAP, which works fine for all other purposes. As this is a message relating to 'PAM_NEW_AUTHTOK_REQD' in libpam, I guess that something in pam changed. Not sure how to do an equivalent of 'rpm -qa --last' under Debian/Ubuntu to check, though. I notice some new symlinks in /lib/security around the time it broke, so I suspect it may be related to an Ubuntu update...

lrwxrwxrwx 1 root root    11 2007-10-26 07:31 pam_unix_acct.so -> pam_unix.so
lrwxrwxrwx 1 root root    11 2007-10-26 07:31 pam_unix_auth.so -> pam_unix.so
lrwxrwxrwx 1 root root    11 2007-10-26 07:31 pam_unix_passwd.so -> pam_unix.so
lrwxrwxrwx 1 root root    11 2007-10-26 07:31 pam_unix_session.so -> pam_unix.so
-rw-r--r-- 1 root root 52088 2006-12-20 17:59 pam_unix.so

My /etc/pam.d/cron is as default:

@include common-auth
auth       required   pam_env.so
@include common-account
@include common-session
# Sets up user limits, please define limits for cron tasks
# through /etc/security/limits.conf
session    required   pam_limits.so

My /etc/pam.d/common-auth is:

auth    sufficient      pam_ldap.so nullok_secure
auth    required        pam_unix.so use_first_pass

Any suggestions as to how to determine what changed, or the cause of the problem would be much appreciated.

Thanks,

--
Ross

---

### Post by rossigee on 2007-11-16
Solved it. The clue was in the /var/log/auth.log file:

Nov 16 10:58:01 jungle1 CRON[5907]: (pam_unix) expired password for user root (root enforced)

I couldn't change the password with 'passwd root' as I haven't set up /etc/pam.d/passwd properly (and don't need to). I just updated the 'expired' field for root in /etc/shadow manually. Shortly after, my /var/log/cron.log came back to life and things that should be happening started happening again :)

--
Ross

---

