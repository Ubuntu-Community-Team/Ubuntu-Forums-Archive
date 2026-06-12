---
title: "Syntax error in script."
date: 2014-06-10
forum: General Help
---

### Post by DrTaylor on 2014-06-10
Hello, all.

I am having trouble with a script I am writing for school.

When I run it, I get this error: 
/home/drtaylor/Downloads/assignment7.sh: line 23: syntax error near unexpected token `newline'
'home/drtaylor/Downloads/assignment7.sh: line 23: `		case $option in 

This is lines 20-25 of the script: 

echo " 8: Email a file to a user "
echo " 9: Quit "
	read option
		case "$option" in 
		1)		users
				;;

I'm not seeing a syntax error, but I'm not very practiced at this. Does anyone see it?

---

### Post by dragonfly41 on 2014-06-10
Use this to test shell scripts ... [http://www.shellcheck.net/](http://www.shellcheck.net/)

---

### Post by DrTaylor on 2014-06-10
OOH, shiny, thank you. I'll try that.

---

### Post by DrTaylor on 2014-06-10
Oh, except it didn't find an error there either.

---

### Post by steeldriver on 2014-06-10
How are you **running **the script? are you trying to run a script that contains **bash **features using **sh**?

---

### Post by DrTaylor on 2014-06-10
Ooh, terminology.

Uh... I'm sorry, I have no idea what you mean.

Sad.

---

### Post by DrTaylor on 2014-06-10
Do you mean, is it a bash script in a file with .sh at the end? Yes.

Heck, I'll give you guys the whole stinking file if you want... it's kinda long.

---

### Post by Frogs Hair on 2014-06-10
Sorry Dr Taylor ,

Open after review.

---

### Post by steeldriver on 2014-06-10
In Linux, the file suffix (the .sh at the end) doesn't really mean anything - the important things are

1. does the script itself have a shebang at the top, like "#!/bin/bash" or "#!/bin/sh" - if so, what is it?

2. are you running the file by setting its executable bit ('chmod +x yourscript.sh') and then doing

```
./yourscript.sh
```
in a terminal, or are you doing something like
```
sh yourscript.sh
```

The latter will cause the system to ignore any shebang in the file and execute script using the particular shell indicated (i.e. in this case /bin/sh - which is 'dash' not 'bash' by default on Ubuntu systems)

---

### Post by spjackson on 2014-06-10
> **DrTaylor said:**
> 
/home/drtaylor/Downloads/assignment7.sh: line 23: syntax error near unexpected token `newline'
'home/drtaylor/Downloads/assignment7.sh: line 23: `        case $option in 

I think you will find that there's a rogue carriage return at the end of that line. Shell scripts need to be linux format text files, not DOS format ones.

---

