---
title: "spotify unmute alias"
date: 2016-06-01
forum: General Help
---

### Post by ja-whitby on 2016-06-01
I am trying to set an alias to unmute spotify in ubuntu 14.04 as follows
alias unmute='for i in $(LC_ALL=C pactl list | grep -E '(^Sink Input)|(media.name = \"Spotify\"$)' | cut -d \# -f2 | grep -v Spotify); do pactl set-sink-input-mute "$i" no; done'
this gives unexpected token errors `('  
I have tried putting a slash / before each instance of bracket ( and ) but the error persists
any ideas?

---

### Post by ajgreeny on 2016-06-01
Have you tested that command in terminal?  Did it work there: I presume not or it should work as an alias.

---

### Post by ja-whitby on 2016-06-01
the command works fine on CLI, I'm not sure exactly how the command functions but it appears to search (grep) the results of the command 'pactl list' output to find which 'sink is allocated to spotify so that mute can be set as no(unmute) for that sink. I'm not sure what the cut command does in the middle, but the whole shebang does work if pasted into the command line (originally sourced from github). From what I can gather the alias operation does not like the bracketing and forward slash should get around this although I tried this and failed - obviously its a big advantage if I can get the alias working to avoid lots of typing.

---

### Post by ajgreeny on 2016-06-01
I have no reason to know whether or not this might help but try adding **bash -c** at the start of your command and also enclose the whole of your previous command in a set of quotation marks```
alias unmute='bash -c "for i in $(LC_ALL=C pactl list | grep -E '(^Sink Input)|(media.name = \"Spotify\"$)' | cut -d \# -f2 | grep -v Spotify); do pactl set-sink-input-mute "$i" no; done"'
```
It may make no difference at all but complex commands such as yours when run in anything other than as a simple terminal command sometimes need the extra **bash -c** in order to run properly.  This is usually only in things like the list of autostart commands but it must be worth a try, so copy my whole alias line to make sure you get the " and ' in the correct places and see if that works.

---

### Post by ja-whitby on 2016-06-01
thanks for the tip, I will try tomoz (program is on other laptop) - also seems to be POSIX basic and extended expressions which may treat metacharacters differently, including | so this may need to be /| - I shall try that also

---

### Post by ja-whitby on 2016-06-02
have tried both the above ideas but neither works.
I like the idea of enclosing the whole script in double quotes but am concerned that nesting may be an issue with the double quotes within the script.
I also I now think the correct escape character is backslash not forwardslash and tried this also to no avail. The list of metacharacters seems to vary with environment (may include $,# as well as |,() and maybe even ").
I think i have too many variables to solve this one so will fall back on using CLI history having now set it so it now appends and does not delete on power down.
Thank for all the help

---

