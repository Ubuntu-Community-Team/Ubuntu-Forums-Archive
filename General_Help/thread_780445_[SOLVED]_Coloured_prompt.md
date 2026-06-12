---
title: "[SOLVED] Coloured prompt"
date: 2008-05-03
forum: General Help
---

### Post by Fass on 2008-05-03
So, I just got Hardy setup on a new hard drive. Went to .bashrc to enable a nice, coloured prompt only to see that it was changed and you are supposed to:

```
# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_colored_prompt=yes

if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
	# We have color support; assume it's compliant with Ecma-48
	# (ISO/IEC-6429). (Lack of such support is extremely rare, and such
	# a case would tend to support setf rather than setaf.)
	color_prompt=yes
    else
	color_prompt=
    fi
fi

if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'
    ;;
*)
    ;;
esac

```

Thing is, though, uncommenting "force_colored_prompt=yes" doesn't work. The prompt stays colourless. I've tried fiddling with the profile settings in the gnome terminal, but to no avail. Anyone know how to get my pretty prompt back? Thanks.

Edit: Well, after posting I read it again and I saw the error, which seems to be a bug. There is a mistake in the script, notably the "if [ -n "$force_color_prompt" ]; then" part. It should of course say "if [ -n "$force_color**ed**_prompt" ]; then". If one edits it to say that, the prompt gets its nice colours. :)

---

### Post by AcidHawk on 2008-05-08
Nice spotting.  I just saw this 2 days ago and was about to add this to the forum today..

Nicely explained also.

---

### Post by millamane on 2008-05-17
Wow... No joke.. good eye. 

I was having the EXACT same problem.. Working perfect now! Thanks

---

### Post by yoda2031 on 2008-05-17
Me too!  Thanks!

Now to get myself "distracted" by those pretty colours in my terminal!!!  Never mind the fact my desktop background is the midriff of a naked female biological unit (humanoid, fear not) - that's not nearly as distracting as the colours... oh the colours... oops, gave away the fact I'm british there somewhat, didn't I?  Oh well...

---

### Post by nooblot on 2008-07-06
> **Fass said:**
> 
Edit: Well, after posting I read it again and I saw the error, which seems to be a bug. There is a mistake in the script, notably the "if [ -n "$force_color_prompt" ]; then" part. It should of course say "if [ -n "$force_color**ed**_prompt" ]; then". If one edits it to say that, the prompt gets its nice colours. :)

:lolflag: Hahah I was also scratching my head then I searched out this thread.

Damn programmers/QA...someone was slacking off.

---

