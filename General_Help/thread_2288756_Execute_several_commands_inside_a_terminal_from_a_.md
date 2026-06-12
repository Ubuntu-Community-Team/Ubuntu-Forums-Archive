---
title: "Execute several commands inside a terminal from a bash script"
date: 2015-07-29
forum: General Help
---

### Post by lowery2 on 2015-07-29
Hello,

I would like to have a button inside firefox that would allow me to download a webpage in epub format.

I already use the [Open With]("https://addons.mozilla.org/fr/firefox/addon/open-with/") addon to call various scripts from its menu.
 
I've added an entry called 'DL book' which points to this script :

```

#!/bin/bash

dest=$(zenity --file-selection --directory --title "Choose a save destination")
cd "$dest"

wget -c --no-check-certificate -O /tmp/page.html "$1"
pandoc -f html -t epub3 -o "$dest"/book.epub /tmp/page.html
rm /tmp/page.html
```

wget downloads the current webpage ($1 is the url passed to the script by the Open with addon) and pandoc makes the conversion into epub.

It works, but I would like to modify the script, so that it's executed inside a terminal and I can see its output.

Usually what I do is simply preceding the command with 'x-terminal-emulator -e <command>', which works fine.
However in this case, I've got several commands and although I tried various methods, none succeeded.
For example I tried chaining the 5 commands (dest=, cd, wget, pandoc and rm) with && to get a very long command and passing it to 'x-terminal-emulator -e' :

```

#!/bin/bash

x-terminal-emulator -e dest=$(zenity --file-selection --directory --title "Choose a save destination") && cd $dest && wget -c --no-check-certificate -O /tmp/page.html "$1" && pandoc -f html -t epub3 -o $dest/book.epub /tmp/page.html && rm /tmp/page.html

```

I don't know why but it doesn't work, I get the following error message :
Failed to execute child process "dest=/home/john/Desktop" (No such file or directory)

... and a blank terminal.

Could someone help me modify the script properly so that I can read its output inside a terminal every time I call it ?

Thank you in advance for your help.

Edit : sorry if my english is bad, it's not my native language.



Edit 2 : ok I know why it doesn't work. It's because some commands passed to x-terminal-emulator are bash built-in commands.

So only bash can execute them.

To do what I want, a better code is :
```

x-terminal-emulator -e bash -c 'dest=$(zenity --file-selection --directory --title "Choose a save destination") && cd "$dest" && wget -c --no-check-certificate -O /tmp/page.html **"$1"** && pandoc -f html -t epub3 -o "$dest"/book.epub /tmp/page.html && rm /tmp/page.html'

```

I tested it by replacing "$1" with a regular url, and it works. But as soon as I replace it with "$1" and call it from a script, it breaks.

It seems x-terminal-emulator doesn't export the url that it's receiving as an argument...



Edit 3 : Let's say I've got this script :

```

x-terminal-emulator -e bash -c 'echo hello > ~/text'

```

I call it foo.sh and make it executable.

If I execute this script I'll have a text file in my home folder containing the word 'hello'.

Now if I modify it to this :

```

x-terminal-emulator -e bash -c 'echo $1 > ~/text'

```

... and I execute it in a terminal like this :

```

./foo.sh hello

```

I get a text file in my home folder containing nothing.

foo.sh receives 'hello' as the first and only argument ($1). **So why doesn't bash receive it ?**



Edit 4 : ok it's dirty (I have to create 2 temporary files /tmp/url and /tmp/page.html but it works. Now I can read the output of the script and see what it does when I call it from 'Open with'.

```

echo "$1" > /tmp/url
x-terminal-emulator -e bash -c 'dest=$(zenity --file-selection --directory --title "Choose a save destination") && cd "$dest" && wget -c --no-check-certificate -O /tmp/page.html $(cat /tmp/url) && pandoc -f html -t epub3 -o "$dest"/book.epub /tmp/page.html && rm /tmp/url /tmp/page.html && read -t30 -n1 -r -p "Press any key to finish..."'

```

If someone knows a better way to do it, especially without the two temporary files, please let me know. Thank you in advance.



Edit 5 : ok I understand why bash didn't get the url argument, it's because it doesn't inherit it from the script automatically.
You have to give it manually starting with $0, which means the first argument you pass to *bash -c 'command'* will be affected to $0 (usually used for the name of the shell or the name of the script).
So to give the url from the script to bash, you have to do : bash -c 'command $0' $1.

I also remembered wget could download to the standard output (-O-) and pipe it  directly to pandoc.
I don't need any temporary files anymore.

Final script :
```

x-terminal-emulator -e bash -c 'dest=$(zenity --file-selection --directory --title "Choose a save destination") ; cd "$dest" ; wget -c --no-check-certificate -O- "$0" | pandoc -f html -t epub3 -o book.epub ; read -t30 -n1 -r -p "Press any key to finish..."' "$1"
```

---

