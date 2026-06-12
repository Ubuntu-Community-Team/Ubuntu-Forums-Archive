---
title: "Unable to use the typical wildcard for this script... alternatives?"
date: 2016-06-17
forum: General Help
---

### Post by Roasted on 2016-06-17
Hi friends. Through some testing with a project, I ended up with a few dozen guest session entries in my /etc/passwd. I'd like to clean these up. It appears as if /usr/sbin/guest-account remove guest-abcde (assuming guest-abcde is the guest account entry I'm looking to remove) successfully removes the session. The catch is, that's just one session. I wanted to remove them all, so I tried the above command with guest-*, but it errors out, citing invalid user.

Is there a way to append this command, but with guest-(anything-listed-here) and have it accept it?

P.S. - It seems as if LightDM will run this script if you log out of your session first. If you restart/shut down from the gear menu in the upper right, it does not successfully clean out the old guest accounts first. Hence how I had a number accumulate.

---

### Post by &amp;KyT$0P# on 2016-06-17
The "typical wildcards" are handled by the shell and would match files & directories in the current working directory.  You'd need to try something like this:
```
for i in `cat /etc/passwd | grep -P -i '^guest-' | sed -r -e 's/:.*$//g'`;do /usr/sbin/guest-account remove "$i";done
```

---

