---
title: "Autocompletion in a script"
date: 2006-08-22
forum: General Help
---

### Post by HAARP on 2006-08-22
Hi,
I have a script called "screen0":
```
DISPLAY=:0.0 "$@"
```
and "screen1"
```
DISPLAY=:0.1 "$@"
```

Basicly, I use them to launch graphical applications on a specific screen.
I open a terminal fullscreen on screen 1 and type:
```
screen0 quake2
```
This way, I play Quake 2 on screen 0 with console output on screen 1. Pretty useful.

The problem with that is, autocompletion of commands after screenX doesn't work. You know, where you type 
"qua" and press tab to get "quake2". I'd like to be able to do this with my screenX scripts. How would I do that?

---

### Post by HAARP on 2006-08-25
bump

---

### Post by HAARP on 2006-08-31
bumpity bump

---

### Post by IYY on 2006-08-31
There is a file you can edit (with sudo) called ```
/etc/bash_completion
```

In this file, you can find autocompletion rules for various applications. You will likely have to write your own section in it that will look through all programs in the user's path and autocomplete with them, unless there already is a section like that, but I couldn't find it when I briefly scanned the file. Even programs that expect another program as input (nohup, nice, exec) don't have this autocompletion.

---

### Post by ayoli on 2006-08-31
i m not sure that's possible, it's same when you run a command with sudo in front, ie sudo aptit + TAB won't do completion to have aptitude.
regards.

---

### Post by HAARP on 2006-08-31
> **ayoli said:**
> i m not sure that's possible, it's same when you run a command with sudo in front, ie sudo aptit + TAB won't do completion to have aptitude.
regards.

Actually, it does for me :|

> **IYY said:**
> There is a file you can edit (with sudo) called ```
/etc/bash_completion
```

In this file, you can find autocompletion rules for various applications. You will likely have to write your own section in it that will look through all programs in the user's path and autocomplete with them, unless there already is a section like that, but I couldn't find it when I briefly scanned the file. 

Ugh, that's quite complex :/ I'll try it when I've got more time. Thanks!

> Even programs that expect another program as input (nohup, nice, exec) don't have this autocompletion.

Try killall ;)

---

### Post by IYY on 2006-08-31
killall doesn't list all programs; it lists the running programs. This is also set in the file I pointed you to, with the following code:

```
_killall()
{
        local cur

        COMPREPLY=()
        cur=${COMP_WORDS[COMP_CWORD]}

        if [ $COMP_CWORD -eq 1 ] && [[ "$cur" == -* ]]; then
                _signals
        else
                COMPREPLY=( $( compgen -W '$( command ps axo command | \
                              sed -ne "1d; s/^\[\?\([^-][^] ]*\).*$/\1/p" | \
                              sed -e "s/.*\///" )' -- $cur ) )
        fi

        return 0
}
[ $UNAME = Linux -o $UNAME = FreeBSD ] && complete -F _killall killall pkill
```

You could make a similar piece of code for your program.

Edit:

While typing this, I poked around in that file a bit more and actually found the solution to your program. The command 'which' autocompletes program names, so all you have to do (in that file) is to find the line

```
complete -c command type which
```

and at the end of it, add your command.

:D

---

### Post by HAARP on 2006-08-31
> **IYY said:**
> killall doesn't list all programs; it lists the running programs. This is also set in the file I pointed you to, with the following code:

```
_killall()
{
        local cur

        COMPREPLY=()
        cur=${COMP_WORDS[COMP_CWORD]}

        if [ $COMP_CWORD -eq 1 ] && [[ "$cur" == -* ]]; then
                _signals
        else
                COMPREPLY=( $( compgen -W '$( command ps axo command | \
                              sed -ne "1d; s/^\[\?\([^-][^] ]*\).*$/\1/p" | \
                              sed -e "s/.*\///" )' -- $cur ) )
        fi

        return 0
}
[ $UNAME = Linux -o $UNAME = FreeBSD ] && complete -F _killall killall pkill
```

You could make a similar piece of code for your program.

Well, I thought, if killall can list running programs, exisiting programs shouldn't be any harder


> Edit:

While typing this, I poked around in that file a bit more and actually found the solution to your program. The command 'which' autocompletes program names, so all you have to do (in that file) is to find the line

```
complete -c command type which
```

and at the end of it, add your command.

:D

Great piece of information. Working perfectly fine, thanks again!
Instead of adding it to **bash_completion**, I made 2 files in **/etc/bash-completion.d/** which also works :)

*deletes one item from todo-list*

---

### Post by IYY on 2006-08-31
No problem! I'm glad I figured this out, because this is the kind of thing I may need to do myself one day.

---

### Post by ayoli on 2006-09-01
wow, how stupid am i  :D bash_completion wasn't enabled in my custom bashrc, now it completes well after which, killall and i know more about customize completions, thx !
regards.

---

### Post by 3rdalbum on 2006-09-01
If you're a real autocompletion freak like me, you should download and use Fish ([http://packages.debian.org/unstable/shells/fish)](http://packages.debian.org/unstable/shells/fish)). Fish is an awesome shell which offers advanced autocompletion out-of-the-box, code colouring, and smart history browsing among other things.

I keep a launcher to it on my panel; it's an excellent piece of work, and I'm not the only person to have asked for it to be the default interactive shell in Ubuntu Edgy.

---

### Post by ayoli on 2006-09-01
hmm, it's also in universe repos, i'll give a try.

---

