---
title: "I need help Command menu script"
date: 2008-06-05
forum: General Help
---

### Post by bigguns99 on 2008-06-05
I am trying to write a shell script for my linux class and I am having abit of difficulty geeting it to work. I am trying to build a commnd menu that allows forces the user to continue to return to the menu untill they enter the exit option. The instructor wants us to use while or until to force it back to the menu until it meets the requirment to terminate the shell script. This is where I am getting lost. Any one have any ideas? I also to create a emailer program which would accessible through a menu any hints. 


**Menu Display Below:** 

COMMAND MENU

 a. Emailer PRogram
 b. Users currently logged in
 c. Name of the working directory
 d. Contents of the working directory

 e. Current Date and Time
 f. This months Calendar
 g. Find the IP of a Web Address
 h. Print a file(on the screen)
 i. See you Fortune
 j. Exit
Enter a, b, c, d, e, f, g, h, i, or j: e

Shell Script Below: 

#!/bin/bash
#menu interface to simple commands
exit=j

echo  -e "\n COMMAND MENU\n"
echo " a. Emailer PRogram"
echo " b. Users currently logged in"
echo " c. Name of the working directory"
echo -e " d. Contents of the working directory\n"
echo " e. Current Date and Time"
echo " f. This months Calendar"
echo " g. Find the IP of a Web Address"
echo " h. Print a file(on the screen)"
echo " i. See you Fortune"
echo " j. Exit"
echo -e "Enter a, b, c, d, e, f, g, h, i, or j: \c"

read answer
echo
case "$answer" in

a)
        mail -s
until [ "$answer"="$exit" ]

b
        users
until [ "$answer"="exit" ]

c
        pwd
until [ "$answer"="$exit" ]

d
        ls
until [ "$answer"="$exit" ]

e
        date
until [ "answer"="$exit" ]

f
        cal
until [ "answer"="$exit" ]

g
        host
until [ "answer"="$exit" ]

h
        lpr
until [ "answer"="$exit" ]

i
        Fortune
until [ "answer"="$exit" ]

j
        Exit
until [ "answer"="$exit" ]



*
        echo "There is no selection: $answer"



exit 0
fi

Please help!:confused:

---

### Post by dagnabit dang doohickey on 2008-06-05
Looking over this code may help with creating your script.
```
#!/usr/bin/env bash

#menu interface to simple commands
exit=j

until [ "$answer" = "$exit" ] ; do
	echo -e "\n COMMAND MENU\n"
	echo " a. Emailer PRogram"
	echo " b. Users currently logged in"
	echo " c. Name of the working directory"
	echo -e " d. Contents of the working directory\n"
	echo " e. Current Date and Time"
	echo " f. This months Calendar"
	echo " g. Find the IP of a Web Address"
	echo " h. Print a file(on the screen)"
	echo " i. See you Fortune"
	echo " j. Exit"
	echo -e "Enter a, b, c, d, e, f, g, h, i, or j: \c"

	read answer
	echo
	case "$answer" in
		a)
			mail -s
			;;
		b)
			users
			;;
		c)
			pwd
			;;
		d)
			ls
			;;
		e)
			date
			;;
		f)
			cal
			;;
		g)
			host
			;;
		h)
			lpr
			;;
		i)
			Fortune
			;;
		j)
			echo 'Exit'
			exit 0
			;;
		*)
			echo "There is no selection: $answer"
			;;
	esac
done

```

---

