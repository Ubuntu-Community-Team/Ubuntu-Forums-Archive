---
title: "(A better way of ) logging my system actions in the console"
date: 2007-10-06
forum: General Help
---

### Post by kentl on 2007-10-06
Hi!

I want to log *certain* commands I perform in Bash, and preferably I want to store some *additional meta information* with (some of) the commands I log. It would be nice if I could do something like:
[LIST=1]
[*]Mark the beginning of a sequence of commands with "Installing and configuring OpenSSH"
[*]sudo apt-get install openssh
[*]Insert comment "I want to disable root logon and only allow public key login"
[*]Commands for editing some of its configuration files with my text editor (using vim, emacs etc)
[*]Commands for restarting the ssh daemon
[*]Mark the end of the current command sequence
[/LIST]
And then I would have a section in my ~/.systemlogfile
```
Begin "Installing and configuring OpenSSH"
    1. Executed "sudo apt-get install OpenSSH"
    # I want to disable root logon and only allow public key login
    2. Changed line "foo1foo1foo1" into "bar1bar1bar1" of ~/ssh/someconfigfile
    3. Changed line "foo2foo2foo2" into "bar2bar2bar2" of ~/ssh/someconfigfile
End "Installing and configuring OpenSSH"
```

As you can see I'm looing for something **more descriptive than just saving my Bash history to a file**. I want the log file to be as human readable as possible, as I'm going to read it. Saving a diff instead of 2 and 3 isn't the best solution for one line changes IMHO. If I do change the file in more complex ways saving a diff makes sense to me.

[COLOR="LightBlue"]**Is there any log file utility out there which I should look into?**[/COLOR] Or is this a "make it yourself" type of situation? How do you solve the problem of logging what you do to your system?

---

