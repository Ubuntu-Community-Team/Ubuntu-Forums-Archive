---
title: "No safety catch for 'stop' command?"
date: 2015-09-19
forum: General Help
---

### Post by jamadagni on 2015-09-19
Well this is not really a question but something I wanted to discuss. Yesterday I was trying to figure out a way to temporarily stop and then restart a process. I finally found my answer [here](http://unix.stackexchange.com/q/2107/54067) but before that, I was looking around. Often I experiment by just hitting what I think is the most natural command for my intended task on the terminal and if really such a command exists it will then display its syntax.

So I hit **stop** and ENTER and to my horror my KDE session just logged out! Thankfully I didn't have any serious windows with unsaved data open so it wasn't so horrible in the end.

Previously, I have never had any data lost by this method since all destructive commands like **rm** and **shred** require me to specify what to destroy, and commands like **reboot** require me to be superuser and those like **mkfs** require both.

Later, **man stop** reveals a page from initctl(8):
>     stop   JOB [KEY=VALUE]...
              Requests that an instance of the named JOB be stopped by changing its goal to stop.  The status of the job is displayed on standard output when the command completes.
...
              _When called from the pre-start stanza of a job configuration, stop may be called without an argument to cancel the start._
              By default SIGTERM is sent to the job process. If it does not respond within a reasonable period, it will be forcibly stopped by sending SIGKILL.


What the #%*^? It still says it requires an argument except “*when called from the pre-start stanza of a job configuration*”. How does my ordinary terminal become such a context?

I have since added a ~/.bash_aliases entry:
```

alias stop="echo \"Yikes! 'stop' will forcefully log you out!\" ; false"

```

BTW I'm using Kubuntu Trusty LTS with latest updates.

---

### Post by asmoore82 on 2015-09-19
I can confirm in Ubuntu 14.04 LTS on stock Unity that this command does nothing as expected:

```
**$ stop**
stop: missing job name
Try `stop --help' for more information.
```

Killing your session is quite unexpected and undesired! The only stretch of imagination that I can think of is that some GUI terminal emulators simply open a command shell while others do a true login session. I'm not really sure of the full difference other than they cause either .bashrc or .bash_profile to run instead - this is why it's common practice to call .bashrc from .bash_profile so you are covered either way. Perhaps KDE is doing a full terminal login and this somehow leads to the unexpected result?

---

