---
title: "Cannot type @ with xdotool"
date: 2015-03-07
forum: General Help
---

### Post by CkDGTAT on 2015-03-07
Hi,


I cannot type @ with xdotool


```
$ xdotool type $(echo @)

```

will give

```
$&#8539;  
```                                   



Thank you

---

### Post by yetimon_64 on 2015-03-07
> ```
$ xdotool key Shift+2
@
```

xdotool, the shift key and the number 2 for my keyboard (check which number @ corresponds to on your keyboard and change if necessary) works here.

---

### Post by CkDGTAT on 2015-03-08
The idea is to put my address in a file and use "type" function of xdotool:

xdotool type $(cat ~/file)

---

### Post by mikejonesey on 2015-03-08
xdotool type "@"
xdotool type \@

---

### Post by yetimon_64 on 2015-03-08
> **CkDGTAT said:**
> The idea is to put my address in a file **and use "type" function of xdotool:**

xdotool type $(cat ~/file)Yes, I see now. But note from the man file for xdotool ...
> 
type [options] something to type
           Options:

           --window windowid
               Send keystrokes to a specific window id. See "SENDEVENT NOTES"
               below. The default, if no window is given, depends on the
               window stack. If the window stack is empty the current window
               is typed at using XTEST. Otherwise, the default is "%1" (see
               "WINDOW STACK").

           --delay milliseconds
               Delay between keystrokes. Default is 12ms.

           --clearmodifiers
               Clear modifiers before sending keystrokes. See CLEARMODIFIERS
               below.

           Types as if you had typed it. Supports newlines and tabs (ASCII
           newline and tab). Each keystroke is separated by a delay given by
           the delay option.

           [B]With respect to "COMMAND CHAINING", this command consumes the
           remainder of the arguments and types them. That is, no commands
           can chain after 'type'.[/B]

           Example: to type 'Hello world!' you would do:
            xdotool type 'Hello world!'
Note what is bolded. [s]You can't put in further commands in "$(2nd command etc)" as this is "command chaining" and the type option does not allow it here.[/s] Edit: statement incorrect and struck out: see next post by Vaphell.

As mikejonesey just posted ...
> xdotool type "@"
xdotool type \@          seems the only way for using the "type" function.

---

### Post by Vaphell on 2015-03-09
> You can't put in further commands in "$(2nd command etc)" as this is "command chaining" and the type option does not allow it here.

that's not true and it's not the context of that man part. xdotool never sees any command and is fed by the shell with the end result, just as if it was explicitly provided.

works just fine here, also zero problems with @
```
$ xdotool type "$( echo thor@avengers.com )"
thor@avengers.com$ xdotool type --delay 200 "$( echo thor@avengers.com )"
thor@avengers.com$ 
```

---

### Post by yetimon_64 on 2015-03-09
Ok Vaphell, I'll strike out those comments, thanks. I didn't go as far as testing, only on what was in the man file (seems I misinterpreted the man file). Cheers.

---

### Post by CkDGTAT on 2015-03-10
Alt_right+2 leads to @, but I cannot find a way to type 

```

wte () {
    xdotool type mymail
    xdotool key Alt+2
    xdotool type mail.com
}

```

```

mymailmail.com

```

---

### Post by Vaphell on 2015-03-10
why do you need it for exactly in the first place? If it's to paste file contents into active input field or whatever, maybe you could use let's say ```
xsel -pi < file
``` to dump the contents to the copypaste buffer and then emit middleclick paste with ```
xdotool click 2
```?

---

