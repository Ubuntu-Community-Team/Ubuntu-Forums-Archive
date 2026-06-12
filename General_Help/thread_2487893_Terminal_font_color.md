---
title: "Terminal font color"
date: 2023-06-17
forum: General Help
---

### Post by rainbowgrisea-74 on 2023-06-17
I don't know how but my terminal is now not colorful. 
This is how it looks now and this is how it looked like (still colorful on desktop).

[IMG]https://cdn.discordapp.com/attachments/690588805648089169/1119639853819236413/image.png[/IMG]
[IMG]https://cdn.discordapp.com/attachments/690588805648089169/1119660980373307452/image.png[/IMG]

Settings:
[IMG]https://cdn.discordapp.com/attachments/690588805648089169/1119639854138019971/image.png[/IMG]

---

### Post by sudodus on 2023-06-17
If both terminals are running locally it seems you have disabled the coloring settings.

- You can compare the settings in the file **~/.bashrc** between the desktop and laptop computers, particularly the section about 'fancy prompt' and/or 'force colour prompt' and/or 'xterm-color'

- You can also compare the settings of gnome-terminal between the desktop and laptop computers.

By modifying such settings to be more like in the computer with colours, you should get the colours back also in the other computer.

[hr][/hr]
If the terminal without colours is running **remotely**, for example via **ssh**, it will probably be without colours, according to the setting of the environment variable TERM.

```

echo $TERM

```

---

### Post by ajgreeny on 2023-06-17
Let's see the section of your .bashrc file that looks a bit like the section I show below.  There are many changes that can be made to show colours in terminal but we have no idea what you have set in that .bashrc file at the moment.
```
# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
force_color_prompt=yes

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
```

---

