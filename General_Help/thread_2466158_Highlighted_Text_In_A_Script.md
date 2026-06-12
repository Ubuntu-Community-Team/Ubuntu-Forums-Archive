---
title: "Highlighted Text In A Script"
date: 2021-08-21
forum: General Help
---

### Post by wyattwhiteeagle on 2021-08-21
I'm considering doing some practice with CLI Bash scripting.

Does the color of the text matter?

If I use black for the first ten lines, then use green for the next ten lines, with it being a script...is the color of the script like a command code for something that is executed while the script is running?

---

### Post by sudodus on 2021-08-21
The script itself consists of commands. You can watch it and edit it in a text editor, and you can render the text (and background) in different ways without changing the script.

You can also make the script produce output, and in that output you can use colours to make it easier to read or simply more attractive. But the script itself is not coloured.

In Linux text screens and terminal windows you can use [ANSI escape codes to render colour effects](https://askubuntu.com/questions/958435/changing-text-color-in-line/958460#958460) on text and background.

Simple example:

```

alias redtext='echo -e "\0033[31m"'
redtext; echo Hello World"

```

The Ubuntu prompt will reset the colour to the set values of the terminal window.

Some useful colouring variables, that you can use in bash scripts:

```

inversvid="\0033[7m"
resetvid="\0033[0m"
faintvid="\0033[2m"
redback="\0033[1;37;41m"
greenback="\0033[1;37;42m"
blueback="\0033[1;37;44m"
logoansi="\0033[38;5;0;48;5;148m"
logorgb="'#afd700'"

```

---

