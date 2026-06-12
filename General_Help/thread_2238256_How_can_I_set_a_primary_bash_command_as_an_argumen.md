---
title: "How can I set a primary bash command as an argument of an other hidden command"
date: 2014-08-06
forum: General Help
---

### Post by CkDGTAT on 2014-08-06
Hi,

I have to type a command 100 times a day with only the argument changing.

How can I get the same result with entering only the argument in the terminal, that is,

Entering

```
$ argument
```

Instead of

```
$ myfunction argument
```

I have heard about preexec command but it doesn't seems to be what I need.

Thank you

---

### Post by CantankRus on 2014-08-06
**_[B][[COLOR=#b22222]How to: Create an alias for terminal commands[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1653127")**_[/B]

---

### Post by CkDGTAT on 2014-08-07
You missed the point.

Suppose I run 

```

$ cat ~/file1
content1

```

I need to enter directly the file names to get content1

```

$ ~/file1
content1

```

Thank you

---

### Post by btindie on 2014-08-07
If 'myfunction' has a long name you could use alias to shorten it so you'd only need to type one character to run it. And that would also give you access to bash completion for the file names.
```
$ alias z='myfunction'
$ z ~/file1
```

Or you could use the shells history function. If you run the full command you want
```
$ cat ~/file1
```
once that's finished, press the up cursor key and Ctrl-w to delete the previous word. You can then type the filename of the next one you need and also use bash completion for the file names.

Alternatively, you could create your own wrapper script. Create a file ~/bin/myshell and set 'chmod +x ~/bin/myshell' with the contents:
```
#!/bin/bash

CMD=<myfunction>

while read -e -p \>\  -r FILE; do
  [[ $FILE = "q" ]] && exit
  "$CMD" "$(eval echo "$FILE")"
done
```

replace "<myfunction>" with the name of the command you want to call. And then just run 'myshell' typing the filenames as usual or 'q' to quit, that will also support bash completion to make typing them quicker.

~Indie

---

### Post by nerdtron on 2014-08-07
You say you type about 100 commands, can you give at least 5 examples and what you want to achieve so that we can have a clearer picture?

---

