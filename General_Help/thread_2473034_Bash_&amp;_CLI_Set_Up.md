---
title: "Bash &amp; CLI Set Up"
date: 2022-03-21
forum: General Help
---

### Post by mockrun on 2022-03-21
Greetings all,
I am trying to set up my Bash Terminal to show:
I would like the cursor to blink and on the next line WITH the $.

```
user@computerName:~/dir/dir
$ _
```


But I have...

```
user@computerName:~/dir/dir$
_

```

I tinkered around and am not sure what next?

```
if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
    PS1="$PS1\n"
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\n: \w\a\]$PS1"
    PS1="$PS1\n"
    ;;
*)
    ;;
esac
```

---

### Post by Holger_Gehrke on 2022-03-21
What else did you expect to happen if you append a newline character to the end of the prompt ? You need to put the '\n' where you want the new line to begin, like so:
```

PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w[COLOR=#00ff00]\n[/COLOR]\$ '

```

You should also remove both the lines saying PS1="$PS1\n".

Holger

---

### Post by Impavidus on 2022-03-22
You probably have a colour terminal, so the first line with PS1= is the one you want to modify. You could modify the next as well, just in case you use a black-and-white terminal one day. Just insert the \n where you need it. You can't have a newline in the title of the terminal, so I wouldn't modify that line with \e]0;. That line prepends an instruction to the prompt to set the title of the terminal window.

As for blinking, you can make some text blink with the \033[5m escape sequence. This can be combined with the instructions for colours, for example```
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[05;95m\]\w\[\033[00m\]\$ '
```will make the curent working directory blink in bright magenta.

This will only tell bash to instruct the terminal to set those colours and blink the text. You may have to change your terminal settings to accept those instruction from bash; blinking may be disabled by default.

I haven't found anything in [wiki's ANSI escape code](https://en.wikipedia.org/wiki/ANSI_escape_code) about setting the blinking cursor. I think that's something you have to configure in the terminal settings. Don't expect the cursor and the text to blink in phase.

---

### Post by MAFoElffen on 2022-03-22
You didn't say it what you meant by "BASH Terminal" was a Console or Graphical Terminal Emulation (and if, which one)...

That would affect how you change the cursor shape, blinking (or not), and blink rate...

---

### Post by dragonfly41 on 2022-03-22
I have yakuake installed with blinking cursor.

Add ..
BlinkingCursorEnabled=true
to the [Terminal Features] section of the .profile file in ~.local/share/konsole.

---

