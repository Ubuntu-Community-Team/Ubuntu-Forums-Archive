---
title: "Extract certain text from variable"
date: 2015-03-02
forum: General Help
---

### Post by HeroCC on 2015-03-02
Hello! This is not specific to Ubuntu, but more like linux and bash in general, If this isn't the best place to have this thread, let me know and I will be happy to move it.

Ok, now for the problem. I have 2 strings: 
```
hello='echo Hello World!'
``` and ```
bye="echo Goodbye World!"
```
I want to just get the first word from inside the "" and the ''. For example, for each I would want to get *echo *and set it to a variable. I am no string manipulation pro and have no idea how to do this. I want to keep it as compatible as possible, as I plan to use this on multiple Unix OSes so I would prefer to have it work on all of them, but if it needs external tools other than regular bash that is OK.

Thanks for the help!

---

### Post by kjohri on 2015-03-02
#!/bin/bash
hello='echo Hello World!'
echo "$hello" | awk '{ print $1 }'
bye="echo Goodbye World!"
echo "$bye" | awk '{ print $1 }'

---

### Post by mme oscar on 2015-03-02
Alternatively, assuming your words are always space-separated:

```
hello="echo Hello World!" ; firstword=$(echo "$hello" | cut -f 1 -d " "); echo "first word is '$firstword'"
```

Another way would be to set the positional parameters:

```
hello="echo Hello World!" ; set -- $hello; echo -e "first word is '$1'\n 2nd word is '$2'\n third word is '$3'"
```

I think that the former is safer for it to work on multiple OSes, but if the shell language is always bash the second should work as well (but you should test, Im' not sure).

---

### Post by HeroCC on 2015-03-02
Close, but I don't want the stuff before the echo, I only want echo. That gives everything before echo as well as echo.

---

### Post by steeldriver on 2015-03-02
what **exactly** are you trying to do? explain the big picture for us

---

### Post by mme oscar on 2015-03-03
Which stuff before the echo? 

With something like: 
firstword=$(echo "$hello" | cut -f 1 -d " ")
the variable "firstword" is assigned all the characters in "hello" until the first space. In the string "echo Hello World!" this is exactly "echo".

---

### Post by HeroCC on 2015-03-03
I am trying to create a function (below) called ialias, that checks to see if you are trying to alias a command to something that doesn't exist. Say I *alias* *apt-get='apt-fast', * and apt-fast doesn't exist, I can't use apt-get without \. I want to use ialias to see if *apt-fast *exists before aliasing it. This is what I have so far:
```

function ialias {
  oldCmd=$(cut -f1 -d"=") <<< "$1"
  newCmd=$(cut -f2 -d"=") <<< "$1"
  baseCmd=$(echo $1 | awk '{ print $1 }')

  if command -v $baseCmd >/dev/null 2>&1; then
    alias $oldCmd=$newCmd
  fi
}

```

Thanks for the help!

---

### Post by mme oscar on 2015-03-04
ok I see what you mean now, then you can just extract it from your previous variable:

```
function ialias {
  oldCmd=$(cut -f1 -d"=") <<< "$1"
  newCmd=$(cut -f2 -d"=") <<< "$1"
  baseCmd=$(cut -f1 -d" ") <<< "$newCmd"

  if command -v $baseCmd >/dev/null 2>&1; then
    alias $oldCmd=$newCmd
  fi
}


```

(please check, I didn't test)

---

### Post by HeroCC on 2015-03-04
> **mme oscar said:**
> ok I see what you mean now, then you can just extract it from your previous variable:

```
function ialias {
  oldCmd=$(cut -f1 -d"=") <<< "$1"
  newCmd=$(cut -f2 -d"=") <<< "$1"
  baseCmd=$(cut -f1 -d" ") <<< "$newCmd"

  if command -v $baseCmd >/dev/null 2>&1; then
    alias $oldCmd=$newCmd
  fi
}


```

(please check, I didn't test)

It works, just what I needed, thanks!

---

