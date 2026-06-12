---
title: "Upgrade to feisty not working"
date: 2007-03-22
forum: General Help
---

### Post by stchman on 2007-03-22
I entered the following comand in a terminal after first doing a sudo su

gksu "upgrade-manager -c -d"

Nothing happened.

What is going on?

---

### Post by hikaricore on 2007-03-22
don't you mean:


"update-manager -c -d"  ??

---

### Post by stchman on 2007-03-22
> **hikaricore said:**
> don't you mean:


"update-manager -c -d"  ??

That command does not work as well.  When I type that into a terminal it says -c is not an option.

---

### Post by fragos on 2007-03-22
I don't think you need the " characters.  Try it without them.  "s are frequently used in forums to separate the command line text from the rest of the sentence.  On the command line they have a different meaning.

---

### Post by stchman on 2007-03-24
> **hikaricore said:**
> don't you mean:


"update-manager -c -d"  ??

This is the output I got when I entered the command at the command line:


[COLOR="Red"]root@bob-laptop:/home/bob# gksu “update-manager -c -d”
gksu: invalid option -- c
GKsu version 1.9.3

Usage: gksu [-u <user>] [options] <command>

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

root@bob-laptop:/home/bob#[/COLOR]


I am at a loss.  As you can see I using a root terminal.

---

### Post by HereInOz on 2007-03-24
As said earlier, try it without the quotation marks.  See how you go.

---

### Post by confused57 on 2007-03-24
Maybe this will help:

[https://help.ubuntu.com/community/FeistyUpgrades](https://help.ubuntu.com/community/FeistyUpgrades)

---

