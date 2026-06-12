---
title: "[SOLVED] Problem with 'gksudo nautilus'"
date: 2008-01-31
forum: General Help
---

### Post by arbulus on 2008-01-31
I'm having a problem getting nautilus to run as root.  

I'm using Openbox on Ubuntu Gutsy 32bit.  I'm trying to set up a nice menu option to open Nautilus as root, but the command doesn't work.   Here is the output that I get:

```

dave@dave:~$ gksudo nautilus --no-desktop
gksudo: unrecognized option `--no-desktop'
GKsu version 2.0.0

Usage: gksudo [-u <user>] [options] <command>

  --debug, -d
    Print information on the screen that might be
    useful for diagnosing and/or solving problems.

  --user <user>, -u <user>
    Call <command> as the specified user.

  --disable-grab, -g
    Disable the "locking" of the keyboard, mouse,
    and focus done by the program when asking for
    password.
  --prompt, -P
    Ask the user if they want to have their keyboard
    and mouse grabbed before doing so.
  --preserve-env, -k
    Preserve the current environments, does not set $HOME
    nor $PATH, for example.
  --login, -l
    Make this a login shell. Beware this may cause
    problems with the Xauthority magic. Run xhost
    to allow the target user to open windows on your
    display!

  --description <description|file>, -D <description|file>
    Provide a descriptive name for the command to
    be used in the default message, making it nicer.
    You can also provide the absolute path for a
    .desktop file. The Name key for will be used in
    this case.
  --message <message>, -m <message>
    Replace the standard message shown to ask for
    password for the argument passed to the option.
    Only use this if --description does not suffice.

  --print-pass, -p
    Ask gksu to print the password to stdout, just
    like ssh-askpass. Useful to use in scripts with
    programs that accept receiving the password on
    stdin.

  --sudo-mode, -S
    Make GKSu use sudo instead of su, as if it had been
    run as "gksudo".
  --su-mode, -w
    Make GKSu use su, instead of using libgksu's
    default.
```


I can use gksudo on other apps, such as gedit, but it won't work with Nautilus.  Is there something I'm doing wrong?  I see at first the output says " unrecognized option `--no-desktop' " but I don't understand what that's meaning.  I can run "nautilus --no-desktop" just fine by itself, but if I add "gksudo" it gives me this.  i don't want Nautilus to run the desktop, i just want the file manager to open. 

Any suggestions?

---

### Post by ~LoKe on 2008-01-31
```
gksu "nautilus --no-desktop"
```
=)

---

### Post by dannyboy79 on 2008-01-31
beat me to it.

---

### Post by arbulus on 2008-01-31
Wow, that was amazingly simple. I kinda feel silly for not thinking of that.

Thanks ~Loke!

---

