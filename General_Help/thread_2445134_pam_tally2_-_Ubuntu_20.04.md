---
title: "pam_tally2 - Ubuntu 20.04"
date: 2020-06-09
forum: General Help
---

### Post by ryanyoungevhc on 2020-06-09
Hello,
I am running Ubuntu 20.04 and am having some trouble figuring out how to get pam_tally2.so to work. I put the following in /etc/pam.d/login:

[COLOR=#000000][FONT=Menlo][COLOR=#39C026]auth[/COLOR] [COLOR=#DB27DA]required[/COLOR] [COLOR=#CA3323]pam_tally2.so[/COLOR] onerr=fail deny=3 unlock_time=600

Even If I try to login incorrectly, the tally does not increase.

[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Menlo]root@ftpcharts2:/etc/pam.d# egrep -v "^#|^$" login[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]auth       optional   pam_faildelay.so  delay=3000000[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]auth required pam_tally2.so onerr=fail deny=3 unlock_time=600[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]auth       requisite  pam_nologin.so[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so close[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]session    required     pam_loginuid.so[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]session    optional   pam_motd.so motd=/run/motd.dynamic[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]session    optional   pam_motd.so noupdate[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so open[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]session       required   pam_env.so readenv=1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]session       required   pam_env.so readenv=1 envfile=/etc/default/locale[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]@include common-auth[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]auth       optional   pam_group.so[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]session    required   pam_limits.so[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]session    optional   pam_lastlog.so[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]session    optional   pam_mail.so standard[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]session    optional   pam_keyinit.so force revoke[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]@include common-account[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]@include common-session[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]@include common-password[/FONT][/COLOR]

```


For instane:
```

[COLOR=#000000][FONT=Menlo]root@ftpcharts2:/etc/pam.d# pam_tally2 --user=ryayoung[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Login           Failures Latest failure     From[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]ryayoung            0    

[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Jun  9 18:07:26 ftpcharts2 sshd[19825]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=10.70.47.161  user=ryayoung[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Jun  9 18:07:26 ftpcharts2 sshd[19825]: pam_sss(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=10.70.47.161 user=ryayoung[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Jun  9 18:07:26 ftpcharts2 sshd[19825]: pam_sss(sshd:auth): received for user ryayoung: 7 (Authentication failure)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Jun  9 18:07:28 ftpcharts2 sshd[19822]: error: PAM: Authentication failure for ryayoung from 10.70.47.161[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]^C[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]root@ftpcharts2:/etc/pam.d# pam_tally2 --user=ryayoung[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Login           Failures Latest failure     From[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]ryayoung            0  [/FONT][/COLOR]

```

Any help would be appreciative. Thanks for your time ahead of time.

---

### Post by ryanyoungevhc on 2020-06-09
Also I am using sss for authentication as well.

---

