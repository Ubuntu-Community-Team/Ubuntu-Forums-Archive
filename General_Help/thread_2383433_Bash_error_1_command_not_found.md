---
title: "Bash error 1: command not found"
date: 2018-01-25
forum: General Help
---

### Post by pankajk2526 on 2018-01-25
There is an Error in ```
ch=$ch$($i)
``` in the following code:


```
#!/bin/bash


origclip="open documents open music"
i=0
set -- $origclip
ch=$1




while [[ ch != "" ]]; do
    ((i++))
    ch=$ch$($i)                      #this does not execute even ch=$($i) doesn't execute
    echo $ch
done
```


I want to achieve following output.


```

open
open documents
open documents open
open documents open music

```


new line and space are not required, presence of space don't matter in output.


In short I want to achieve output of following code, with a variable 'i' which increments as in previous code


```

origclip="open documents open music"
set -- $origclip
echo $1
echo $1$2
echo $1$2$3
echo $1$2$3$4

```


Also there is a problem in achieving end of line ```
while [[ ch != "" ]]; do
``` i am not sure of this.

---

### Post by Holger_Gehrke on 2018-01-25
'$( ... )' is a command substitution, so $($i) substitutes the value for the variable and tries to execute it and put it's output into the command. What you probably want to do is a _variable indirection_.

And the literal string 'ch' is never going to be equal to an empty string (and neither is $ch, the value of the variable ch). You probably want to compare $i to the _number of positional parameters_.

Search the bash manual page for the underlined terms ...

And if you want to simplify the script, you might want to take a look at the bash-built-in command 'shift'

Holger

---

