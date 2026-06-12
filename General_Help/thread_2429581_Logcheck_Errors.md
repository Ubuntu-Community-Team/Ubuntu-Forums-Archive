---
title: "Logcheck Errors"
date: 2019-10-20
forum: General Help
---

### Post by sniper8752 on 2019-10-20
I am trying to get logcheck to run on my system, but I get e-mails that are as follows:
```
Warning: If you are seeing this message, your log files may not have beenchecked!


Details:
Could not run logtail or save output


Check temporary directory: /tmp/logcheck.cJcsta


Also verify that the logcheck user can read all files referenced in
/etc/logcheck/logcheck.logfiles!


declare -x HOME="/var/lib/logcheck"
declare -x LANG="en_US.UTF-8"
declare -x LOGNAME="logcheck"
declare -x MAILTO="root"
declare -x OLDPWD
declare -x PATH="/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin"
declare -x PWD="/var/lib/logcheck"
declare -x SHELL="/bin/sh"
declare -x SHLVL="1"
```

The two log files I have defined, are owned by the group, 'adm'.  Also, the /tmp file that it references has not been created.

---

