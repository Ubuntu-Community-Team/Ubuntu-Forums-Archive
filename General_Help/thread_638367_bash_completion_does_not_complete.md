---
title: "bash_completion does not complete"
date: 2007-12-11
forum: General Help
---

### Post by wkuballa on 2007-12-11
I noticed that "/etc/bash_completion" does not run correctly (at least on my system).  The script tries to assign a value to two readonly variables (at line 35 and 36).  The two assignment statements are within braces to prevent error messages from being displayed.  However, bash terminates the procedure with an 'exit' at the first assignment.  I.e., not only is the rest of the script not executed, the script does not return to its calling point as it would when terminated with a 'return' and other session initialization scripts following the call to bash_completion are not executed.

Is that some setting on my system that I need to change?  Or is this simply an error?

Regards,
Werner

---

### Post by jgneff on 2008-01-26
I see the same problem on Ubuntu 7.10. It seems to happen only when sourcing the file after logging in. The big problem it causes is that any environment variables (PATH, JAVA_HOME) that you might set at the end of .profile or .bashrc won't take effect if you simply source the file with one of the following:

```

$ . .profile
$ source .profile

```

or one of the following:

```

$ . .bashrc
$ source .bashrc

```

as both return early -- .profile when it sources .bashrc (with ". ~/.bashrc"), and .bashrc when it sources bash_completion (with ". /etc/bash_completion"), so neither file gets to the environment variables you just added or modified at the end.

If you log out and log back in again, both run to completion and your environment variables are set. But unless you know to log out and back in, it drives you crazy because you can't figure out why simply sourcing your updated .profile or .bashrc isn't working!

Then there's the whole undocumented ".pam_environment" trick you can use instead, but that's new and less familiar to most people just trying to change their PATH setting or add JAVA_HOME and other things on a per-user basis (rather than system-wide in "/etc/environment"). Getting environment variables set everywhere is confusing enough on Ubuntu, but this little glitch with bash_completion makes it more mysterious than necessary.

---

