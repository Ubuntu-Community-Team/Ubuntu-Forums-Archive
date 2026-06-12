---
title: "Bash script color output"
date: 2014-06-13
forum: General Help
---

### Post by Tristan_Williams on 2014-06-13
I have this script:
```

while IFS= line=`cat ./srcfile.sh`; do
    length="${#line}"
    bol=1
    for (( offset = 0 ; offset < length ; offset++ )); do
        char="${line:offset:1}"
        printf '%s' "$char"
        if (( bol )) && [[ "$char" == " " ]]; then
            continue
        fi
        bol=0
        sleep 0.1
    done

    if (( length == 0 )); then
        sleep 0.$(( RANDOM % 3 + 2 ))
    else
        sleep 0.$(( RANDOM % 7 + 3 ))
    fi

    printf '\n'
done

```

It outputs the text inside ./srcfile.sh one character at a time.

How could I modify it, so that it outputs the text in a color coded manner, much in the same way that nano and Gedit have syntax highlighting?

---

### Post by Vaphell on 2014-06-13
[https://wiki.archlinux.org/index.php/Color_Bash_Prompt](https://wiki.archlinux.org/index.php/Color_Bash_Prompt)
that said you won't do this on your own because syntax highlighting means you need to have a tool that knows the structure of the language. Use *highlight* or something like that.


```
while IFS= line=`cat ./srcfile.sh`; do 
```

this doesn't make much sense. You run infinite loop with $line storing the contents of the whole file, which makes the if block completely useless (no way you are going to hit 0 lenght on non-empty file)

If you wanted to read on per line basis you should use something like this
```
while IFS= read -r line; do ...; done < <( highlight -O ansi "$0" )
```

---

### Post by Tristan_Williams on 2014-06-18
> **Vaphell said:**
> [https://wiki.archlinux.org/index.php/Color_Bash_Prompt](https://wiki.archlinux.org/index.php/Color_Bash_Prompt)
that said you won't do this on your own because syntax highlighting means you need to have a tool that knows the structure of the language. Use *highlight* or something like that.

How could I use *highlight* to filter everything that bash outputs?
I would like to have error messages in red, warnings and important statements in yellow, names of commands in green, etc...

---

