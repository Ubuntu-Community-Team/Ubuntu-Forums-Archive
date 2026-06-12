---
title: "terminal comand (wait order)"
date: 2007-04-27
forum: General Help
---

### Post by jmvidalvia on 2007-04-27
Just a quick question:
I need to add into a script a command in order to **wait** or **hold** till the user types Enter before the window closes.
Which order can I use? I couldn't find it!

---

### Post by lloyd_b on 2007-04-27
> **jmvidalvia said:**
> Just a quick question:
I need to add into a script a command in order to **wait** or **hold** till the user types Enter before the window closes.
Which order can I use? I couldn't find it!

What I think you're looking for is the "read" builtin command.  Here's a simple shell script to illustrate how to use it for this purpose:
```
#!/bin/bash
echo "This is a test"
echo "Press <RETURN> to continue"
read DUMMY
echo "Ok, *now* we can exit"

```

Lloyd B.

---

### Post by jmvidalvia on 2007-04-27
Thank you very much!

---

### Post by bashologist on 2007-04-27
There's also a -p option for the read command on some systems.
```
read -p "Press Enter to continue " var 
```
You could use a case to check the output of the read.
```
read -p "Do you want to continue [Y/n]? " var
case "$var" in
	"y"|"Y")
		echo "fixme"
	;;
	"n"|"N")
		echo "Abort."
	;;
esac
```
You could if you wanted do the case in one line even!
```
read -p "Do you want to continue [Y/n]? " var
case "$var" in "y"|"Y") echo "Fixme.";; "n"|"N") echo "Abort.";; esac
```

---

### Post by jmvidalvia on 2007-04-27
Uau!
Even better.
Thanks a lot.

---

