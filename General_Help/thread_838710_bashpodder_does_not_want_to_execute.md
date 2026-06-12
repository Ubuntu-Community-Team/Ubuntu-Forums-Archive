---
title: "bashpodder does not want to execute"
date: 2008-06-23
forum: General Help
---

### Post by minchina on 2008-06-23
Hey all. I am trying to set up bashpodder, the podcast downloading script.  I know that amaroK can do podcasts, but I want to try and use a command line/cron tool.  Anyway.....

I followed this older howto:
[http://ubuntuforums.org/showthread.php?t=41085](http://ubuntuforums.org/showthread.php?t=41085)

and changed the urls so it was current.  Everything downloaded fine, but for some reason I can't get anything to become executable.  When I do this:

chmod -R 744 bashpodder.shell

and then use the dir command, bashpodder.shell shows up but it is not green.  When I try and run it (by typing bashpodder.shell), I get this:

bash: bashpodder.shell: command not found


I even tried chmod 700 bashpodder.shell, but still nothing.  I know that I am ignorant as the day is long on bash scripting, but what am I missing?

thanks
michael

---

### Post by lloyd_b on 2008-06-23
> **minchina said:**
> Hey all. I am trying to set up bashpodder, the podcast downloading script.  I know that amaroK can do podcasts, but I want to try and use a command line/cron tool.  Anyway.....

I followed this older howto:
[http://ubuntuforums.org/showthread.php?t=41085](http://ubuntuforums.org/showthread.php?t=41085)

and changed the urls so it was current.  Everything downloaded fine, but for some reason I can't get anything to become executable.  When I do this:

chmod -R 744 bashpodder.shell

and then use the dir command, bashpodder.shell shows up but it is not green.  When I try and run it (by typing bashpodder.shell), I get this:

bash: bashpodder.shell: command not found


I even tried chmod 700 bashpodder.shell, but still nothing.  I know that I am ignorant as the day is long on bash scripting, but what am I missing?

thanks
michael

First off, the "-R" option of chmod means "recursive" - it's used to change the permissions of subdirectories and the files in them.  Not needed in this case.

Second, "744" is "rwxr--r--", which is rather odd for an executable.  I'd go with "755", which is "rwxr-xr-x", if you want others to be able to run it, or "700" ("rwx------") if you want it to be "private".

Finally, to run a file in the current directory, you need to explicitly tell bash where to find it: "./bashpodder.shell", rather than just "bashpodder.shell".
Or you can move it into a directory that's in your PATH.  If it's in a directory in the PATH, then just typing "bashpodder.shell" will work.

Lloyd B.

---

### Post by minchina on 2008-06-25
That did the trick.  Thanks for the quick response.

---

