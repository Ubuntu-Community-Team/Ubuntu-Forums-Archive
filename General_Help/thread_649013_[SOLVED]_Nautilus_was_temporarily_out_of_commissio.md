---
title: "[SOLVED] Nautilus was temporarily out of commission"
date: 2007-12-24
forum: General Help
---

### Post by artesian_spring on 2007-12-24
Last time I logged in, I had two problems:
1) My desktop background didn't display at first. When I went to System->Preferences->Appearance, it sorted itself out.
2) Nautilus wouldn't work. I tried opening different folders, from both the "Places" menu and the command line; it neither opened nor gave any error messages (in the time that I waited before ending the process). Related to this--I think--is that no desktop icons would display.

Everything else worked, except these two things. I rebooted and logged in again, and everything was okay.

My questions are:
1) Does anyone know why this happened? Is there something I need to fix?
2) Should I file a bug report? If so, what error logs should I include the contents of?

---

### Post by FuturePilot on 2007-12-24
I think you may have run into this bug
[https://bugs.launchpad.net/bugs/150471]("https://bugs.launchpad.net/bugs/150471")
It's happened to me a bunch of times. Killing Nautilus and then restarting it should fix it when it happens.

---

### Post by artesian_spring on 2007-12-24
Looking at the launchpad thread you linked, it seems like the best workaround is to add "killall nautilus" just before "exit 0" in etc/gdm/PostSession/Default.

Pjotr12345 summarizes the solution:

> In the terminal:
sudo gedit /etc/gdm/PostSession/Default

Now add "killall nautilus" just above "exit 0". The file reads then as follows:

```
#!/bin/sh

PATH="/usr/bin:$PATH:/bin:/usr/bin"
OLD_IFS=$IFS

gdmwhich () {
  COMMAND="$1"
  OUTPUT=
  IFS=:
  for dir in $PATH
  do
    if test -x "$dir/$COMMAND" ; then
      if test "x$OUTPUT" = "x" ; then
        OUTPUT="$dir/$COMMAND"
      fi
    fi
  done
  IFS=$OLD_IFS
  echo "$OUTPUT"
}
killall nautilus
exit 0
```

I followed these instructions; now I'll have to wait and see if the problem reappears.

---

