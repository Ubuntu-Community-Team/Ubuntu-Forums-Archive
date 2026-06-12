---
title: "Terminal problem"
date: 2007-07-11
forum: General Help
---

### Post by heyilikeyoursweater on 2007-07-11
I did something to my terminal a long time ago, and I don't remember what. When I open it, all it shows is th $ sign. It should show username@computername or something. Another thing is that I don't get the features of pressing the arrow keys to do stuff, like go back to the last thing entered. When I press the keys I get these signs: ^[[A^[[C^[[B^[[D and so forth. How do I change this?

---

### Post by NickD-NLUG on 2007-07-12
You can change the prompt on your terminal by altering .bashrc, this is the relevant section from my .bashrc:

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
xterm-color)
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
    ;;
*)
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
    ;;
esac

# Comment in the above and uncomment this below for a color prompt
#PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'
    ;;
*)
    ;;
esac

As for not being able to use the arrows, I don't know... but check the "character encoding" section under "Terminal" in your terminal's options...

---

### Post by heyilikeyoursweater on 2007-07-12
My character encoding is just the normal UTF-8. Why does that make a difference?

---

