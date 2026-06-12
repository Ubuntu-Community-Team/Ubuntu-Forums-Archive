---
title: "Bash Prompt - Help Please"
date: 2012-10-18
forum: General Help
---

### Post by Atbash on 2012-10-18
I'm trying to permanently alter my bash prompt.  I've read that I need to edit my .bashrc file.  Would someone mind telling me where to find this?  Is this the file titled bash.bashrc in the etc folder? 

Also, should I edit the "PS1=" section of this file for the desired effect?  :confused:

---

### Post by Habitual on 2012-10-18
```
/home/$user/.bashrc
```

[http://tldp.org/HOWTO/Bash-Prompt-HOWTO/](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/)

---

### Post by papibe on 2012-10-18
The easier way would be to add a line on the end of the file ~/.bashrc

For instance:
```
PS1="myprompt >"
```
Let us know how it goes.
Regards.

---

### Post by Cheesemill on 2012-10-18
The file you are looking for is .bashrc in your home folder.

To see hidden files just hit CTRL+H in your file browser (any files or folders that begin with a . are hidden by default).

---

### Post by Atbash on 2012-10-19
Thanks for the help.  Got it.  :)

---

### Post by rnerwein on 2012-10-19
> **Atbash said:**
> Thanks for the help.  Got it.  :)

hello 
just for fun. i alter my bash-promt in:

case "$TERM" in
xterm*|rxvt*)
    PS1=""
    if [ "`id -u`" -eq 0 ]
    then
        PS1="\[\033[01;31m\]\u\[\033[00m\]@\h:\w \A-> "
    else
        PS1="\[\033[01;32m\]\u\[\033[00m\]@\h:\w \A-> "
    fi
    stty -echoctl
    ;;
*)
    ;;
esac

this gives my a promt relayed on the user and if the user is root the name is red.
normal user is shown in green.
here are my promts:
[COLOR=SeaGreen]richi[/COLOR]@tschang:~ 12:29->
or
[COLOR=Red]root[/COLOR]@tschang:~ 12:31->

---

### Post by buckyaustin on 2012-10-19
That is actually a brilliant idea. Should be used by all terminal emulators. But only seems useful to new users. But could potentialy save alot of the new users to prevent them doing the mistakes that I, for instance, have done in the past. And still do lol. Took me two weeks t oget my system up and running the way I wanted because I got the terminal mixed up. Kept forgetting to give myself root privlidges.

---

### Post by Cheesemill on 2012-10-19
I have a pretty similar PS1 myself:
```
if [ `id -u` != "0" ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;31m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
fi

```To see just what can be achieved with your PS1 take a look at this thread, some of the things in it are brilliant.

[https://bbs.archlinux.org/viewtopic.php?id=50885](https://bbs.archlinux.org/viewtopic.php?id=50885)

---

### Post by drmrgd on 2012-10-19
Wow!  Thanks for posting that!  I thought my prompt was clever, using different colors for Root and User.  This Arch thread blew my mind.  Now I have lots of stuff to play with!

---

