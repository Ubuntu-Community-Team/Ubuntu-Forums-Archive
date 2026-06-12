---
title: "Run command as login shell in altyo terminal?"
date: 2014-04-30
forum: General Help
---

### Post by grumblebum2 on 2014-04-30
I have the application **undistract-me** installed but only works when I set gnome-terminal preferences to "Run command as login shell"
and add this to my **~/.bashrc** file....
```
#notify when long running commands finish(undistract-me)
. /usr/share/undistract-me/long-running.bash
notify_when_long_running_commands_finish_install
```

I like to use the drop-down terminal altyo but undistract-me doesn't work with it.

I can't see an option in altyo to "Run command as login shell".
Would using a custom shell, fix this and what do I write for the custom shell?

undistract-me description...
> If you are running an environment which supports notifications via
 libnotify, you can install this, and then you'll get a notification when
any command finishes that took longer than ten seconds to finish.

This package installs a set of bash functions and settings which will be
pulled into a bash login shell via /etc/profile.d

---

### Post by grumblebum2 on 2014-04-30
Bump...
Anyone.
Basically, how can I make undistract-me behave the same in the altyo terminal as it does in gnome-terminal.
[https://github.com/linvinus/AltYo](https://github.com/linvinus/AltYo)
[https://launchpad.net/~linvinus/+archive/altyo](https://launchpad.net/~linvinus/+archive/altyo)

---

### Post by grumblebum2 on 2014-05-01
It seems that having a PROMPT_COMMAND in the ~/.bashrc causes undistract-me to fail in altyo.

Don't know how all this works but I had a line ...
```
PROMPT_COMMAND="history -a; $PROMPT_COMMAND"
```
which would show an error in altyo...
```
bash: PROMPT_COMMAND: line 0: syntax error near unexpected token `;'
bash: PROMPT_COMMAND: line 0: `preexec_set_exit;history -a; ;preexec_invoke_cmd'
glen@Trusty:~$
```

Commenting that line out allowed undistract-me to work in altyo.

---

