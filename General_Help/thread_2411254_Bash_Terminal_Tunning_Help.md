---
title: "Bash Terminal Tunning Help"
date: 2019-01-27
forum: General Help
---

### Post by emint on 2019-01-27
hi!

i have added this to the end of my .bashrc

```

path_lenght=${#PWD}
lenght_to_new_line=10
if (( $path_lenght > $lenght_to_new_line )); then
    PS1=${PS1%?}
    PS1=${PS1%?}\n'$ '
fi

```

this make the prompt start in a new line if the path is log
cause when im inside a very long path, i prefer the prompt to start in a new line

if i start the terminal in my home dir, its ok, the prompt will be in the same line, (cause the path is short)
if i start the terminal inside a long path the prompt will be in next line!

but my problem is, when i start the terminal in short path and the i do 

cd /logpath/longpath/longpath/longpath

i will be still in the same line cause the .bashrc is only executed when i start the terminal... how could i solve that... to re execute the PS1 value in every dir change?

thanks in advance

---

### Post by Holger_Gehrke on 2019-01-28
I'd redefine 'cd' using a function definition in ~/.bashrc, something along the lines of:
```

cd() {
  builtin cd "$@"
  if [[ ${#PWD} -gt 10 ]] ; then
    #define prompt for long path
  else
    #define prompt for short path
  fi
}

```

Holger

---

### Post by sisco311 on 2019-01-28
Check out the PROMPT_COMMAND variable. If set its value is executed as a command prior to issuing each primary prompt.

---

### Post by sisco311 on 2019-01-28
Something like:
```

unset newline
PS1='whatever... $newline$ '

prompt_command(){
max_l=10
if (( ${#PWD} > max_l ))
then
    newline="
"
else
    newline=
fi
}

PROMPT_COMMAND=prompt_command
```should do the trick.

---

### Post by emint on 2019-01-29
thanks!!!

thats my final version


```
# emi added# Add a new line at the end of the command prompt
#PS1=${PS1}\\n
unset newline
prompt_command(){
	max_l=25
	if (( ${#PWD} > max_l ))
	then
	    newline=$'\n''-> $ '
	else
	    newline=' '
	fi
}
PROMPT_COMMAND=prompt_command
PS1=${PS1%?}'$newline'

```

---

### Post by sisco311 on 2019-01-29
Cool!

Something just popped in my head. It would make sense to define max_l as a local variable:
```
local max_l=blah_blah
```otherwise you would not be able to use max_l as a variable name in your interactive shell...

If max_l is defined as a global variable, then each time the primary prompt is displayed its value will be set to the value you defined in the function.

---

### Post by emint on 2019-01-30
> **sisco311 said:**
> Cool!

Something just popped in my head. It would make sense to define max_l as a local variable:
```
local max_l=blah_blah
```otherwise you would not be able to use max_l as a variable name in your interactive shell...

If max_l is defined as a global variable, then each time the primary prompt is displayed its value will be set to the value you defined in the function.

outside [COLOR=#000000][FONT=&quot]prompt_command()?[/FONT][/COLOR]

---

### Post by sisco311 on 2019-01-30
No.   Inside the command_prompt function.

---

### Post by emint on 2019-01-30
thx

---

