---
title: "/home/andy/bin/test.sh: line 93: syntax error: unexpected end of file"
date: 2019-04-06
forum: General Help
---

### Post by raleigh3 on 2019-04-06
I am trying to modify some code I found. I want to add seconds to it.

I get the message

```
andy@7_~/Downloads$ test.sh -s 5
/home/andy/bin/test.sh: line 93: syntax error: unexpected end of file


```
```
#!/bin/bash
# 
 
if [ "$#" -lt "2" ] ; then 
	echo "Incorrect usage ! Example:" 
	echo 'CountDown.sh -d  "Jun 10 2011 16:06"' 
	echo 'or' 
	echo 'CountDown.sh -m  90' 
	echo 'or'
	echo 'CountDown.sh -s 5'
	exit 1 
fi 
 
now=`date +%s` 
 
if [ "$1" = "-d" ] ; then 
	until=`date -d "$2" +%s` 
	sec_rem=`expr $until - $now` 
	echo "-d" 
	if [ $sec_rem -lt 1 ]; then 
		echo "$2 is already history !" 
	fi 
fi 
 
if [ "$1" = "-m" ] ; then 
	until=`expr 60 \* $2` 
	until=`expr $until + $now` 
	sec_rem=`expr $until - $now` 
	echo "-m" 
	if [ $sec_rem -lt 1 ]; then 
		echo "$2 is already history !" 
	fi
if [ "$1" = "-s" ] ; then 
    until=`expr \* $2` 
    until=`expr $until + $now` 
    sec_rem=`expr $until - $now` 
    echo "-s" 
    if [ $sec_rem -lt 1 ]; then 
        echo "$2 is already history !" 
    fi 	
	 
fi 
 
_R=0
_C=7
tmp=0
percent=0
total_time=0
col=`tput cols`
col=$[ $col -5 ]

while [ $sec_rem -gt 0 ]; do 
	clear 
	date 
	let sec_rem=$sec_rem-1 
	interval=$sec_rem 
	seconds=`expr $interval % 60` 
	interval=`expr $interval - $seconds` 
	minutes=`expr $interval % 3600 / 60` 
	interval=`expr $interval - $minutes` 
	hours=`expr $interval % 86400 / 3600` 
	interval=`expr $interval - $hours` 
	days=`expr $interval % 604800 / 86400` 
	interval=`expr $interval - $hours` 
	weeks=`expr $interval / 604800` 
	echo "----------------------------" 
	echo "Seconds: " $seconds 
	echo "Minutes: " $minutes 
	echo "Hours:   " $hours 
	echo "Days:    " $days 
	echo "Weeks:   " $weeks 

	echo -n 
	"["	progress=$[$progress + 1]
	if [ $total_time -lt 1 ] ; then
		total_time=$[$hours * 3600 + $minutes * 60 + $seconds]
	fi
	
	printf -v f "%$(echo $_R)s>" ; printf "%s\n" "${f// /=}"
	_C=7
	tput cup 7 $col

	tmp=$percent
	percent=$[$progress * 100 / $total_time]
	printf "]%d%%" $percent
	change=$[$percent - $tmp]

	_R=$[ $col * $percent / 100 ]

	sleep 1
done
printf "\n"

```

---

### Post by #&amp;thj^% on 2019-04-06
There are only 92 Lines there:
```
91 done
92 printf "\n"
```
93 is missing, and possibly here, a way to complete the task it was told to do.
Where is the original code your using, I would need to see that first before advising anything else.
I could guess, but what's the point in that. :)

---

### Post by yetimon_64 on 2019-04-06
> **1fallen said:**
> There are only 92 Lines there:
```
91 done
92 printf "\n"
```
93 is missing, and possibly here, a way to complete the task it was told to do.
Where is the original code your using, I would need to see that first before advising anything else.
I could guess, but what's the point in that. :)

That I've seen before when the script is still looking for more code lines. Like one of the logic blocks is incomplete.

There is one block of code further up the script, I can see, that is missing a "fi" statement ....
```
if [ "$1" = "-m" ] ; then      until=`expr 60 \* $2` 
    until=`expr $until + $now` 
    sec_rem=`expr $until - $now` 
    echo "-m" 
    if [ $sec_rem -lt 1 ]; then 
        echo "$2 is already history !" 
    fi
**fi**

```
One line is missing containing "fi".
 I've added in what is needed in bold text.

Cheers, yeti.

---

### Post by #&amp;thj^% on 2019-04-06
Nice Spot! :KS
And there's that missing line.
Good to see me ole mate yeti kickn bout

---

### Post by raleigh3 on 2019-04-06
> **yetimon_64 said:**
> That I've seen before when the script is still looking for more code lines. Like one of the logic blocks is incomplete.

There is one block of code further up the script, I can see, that is missing a "fi" statement ....
```
if [ "$1" = "-m" ] ; then      until=`expr 60 \* $2` 
    until=`expr $until + $now` 
    sec_rem=`expr $until - $now` 
    echo "-m" 
    if [ $sec_rem -lt 1 ]; then 
        echo "$2 is already history !" 
    fi
**fi**

```
One line is missing containing "fi".
 I've added in what is needed in bold text.

Cheers, yeti.

Thanks, I added the fi.

```
andy@7_~/Downloads$ test.sh -s 20
expr: syntax error
-s
20 is already history !
```

I only partially understand much of the code.

There must be something I left out.

---

### Post by raleigh3 on 2019-04-06
Here is the original unmodified code.

It came from here.

[https://linuxconfig.org/time-countdown-bash-script-example](https://linuxconfig.org/time-countdown-bash-script-example)

```
#!/bin/bash 
 
if [ "$#" -lt "2" ] ; then 
	echo "Incorrect usage ! Example:" 
	echo './countdown.sh -d  "Jun 10 2011 16:06"' 
	echo 'or' 
	echo './countdown.sh -m  90' 
	exit 1 
fi 
 
now=`date +%s` 
 
if [ "$1" = "-d" ] ; then 
	until=`date -d "$2" +%s` 
	sec_rem=`expr $until - $now` 
	echo "-d" 
	if [ $sec_rem -lt 1 ]; then 
		echo "$2 is already history !" 
	fi 
fi 
 
if [ "$1" = "-m" ] ; then 
	until=`expr 60 \* $2` 
	until=`expr $until + $now` 
	sec_rem=`expr $until - $now` 
	echo "-m" 
	if [ $sec_rem -lt 1 ]; then 
		echo "$2 is already history !" 
	fi 
fi 
 
_R=0
_C=7
tmp=0
percent=0
total_time=0
col=`tput cols`
col=$[ $col -5 ]

while [ $sec_rem -gt 0 ]; do 
	clear 
	date 
	let sec_rem=$sec_rem-1 
	interval=$sec_rem 
	seconds=`expr $interval % 60` 
	interval=`expr $interval - $seconds` 
	minutes=`expr $interval % 3600 / 60` 
	interval=`expr $interval - $minutes` 
	hours=`expr $interval % 86400 / 3600` 
	interval=`expr $interval - $hours` 
	days=`expr $interval % 604800 / 86400` 
	interval=`expr $interval - $hours` 
	weeks=`expr $interval / 604800` 
	echo "----------------------------" 
	echo "Seconds: " $seconds 
	echo "Minutes: " $minutes 
	echo "Hours:   " $hours 
	echo "Days:    " $days 
	echo "Weeks:   " $weeks 

	echo -n "["

	progress=$[$progress + 1]
	if [ $total_time -lt 1 ] ; then
		total_time=$[$hours * 3600 + $minutes * 60 + $seconds]
	fi
	
	printf -v f "%$(echo $_R)s>" ; printf "%s\n" "${f// /=}"
	_C=7
	tput cup 7 $col

	tmp=$percent
	percent=$[$progress * 100 / $total_time]
	printf "]%d%%" $percent
	change=$[$percent - $tmp]

	_R=$[ $col * $percent / 100 ]

	sleep 1
done
printf "\n"
```

---

### Post by raleigh3 on 2019-04-07
```
# [: -gt: unary operator expected

while [ $sec_rem -gt 0 ]; do
```

---

### Post by again? on 2019-04-07
In the section you added for secs, you only removed the 60 and not the operators. Doesn't need any conversion.
Your addition...
```
if [ "$1" = "-s" ] ; then 
    **[COLOR="#FF0000"]until=`expr \* $2`[/COLOR]** 
    until=`expr $until + $now` 
    sec_rem=`expr $until - $now` 
    echo "-s" 
    if [ $sec_rem -lt 1 ]; then 
        echo "$2 is already history !" 
    fi 	
fi 
```

Should be...
```
if [ "$1" = "-s" ] ; then 
   ** [COLOR="#FF0000"]until=$2[/COLOR]**
    until=`expr $until + $now` 
    sec_rem=`expr $until - $now` 
    echo "-s" 
    if [ $sec_rem -lt 1 ]; then 
        echo "$2 is already history !" 
    fi 	
fi 
```

Complete script...
```
#!/bin/bash 
 
if [ "$#" -lt "2" ] ; then 
	echo "Incorrect usage ! Example:" 
	echo './countdown.sh -d  "Jun 10 2011 16:06"' 
	echo 'or' 
	echo './countdown.sh -m  90' 
	exit 1 
fi 
 
now=`date +%s` 
 
if [ "$1" = "-d" ] ; then 
	until=`date -d "$2" +%s` 
	sec_rem=`expr $until - $now` 
	echo "-d" 
	if [ $sec_rem -lt 1 ]; then 
		echo "$2 is already history !" 
	fi 
fi 
 
if [ "$1" = "-m" ] ; then 
	until=`expr 60 \* $2` 
	until=`expr $until + $now` 
	sec_rem=`expr $until - $now` 
	echo "-m" 
	if [ $sec_rem -lt 1 ]; then 
		echo "$2 is already history !" 
	fi 
fi 

[COLOR="#FF0000"]if [ "$1" = "-s" ] ; then 
    until=$2
    until=`expr $until + $now` 
    sec_rem=`expr $until - $now` 
    echo "-s" 
    if [ $sec_rem -lt 1 ]; then 
        echo "$2 is already history !" 
    fi 	
fi [/COLOR]
 
_R=0
_C=7
tmp=0
percent=0
total_time=0
col=`tput cols`
col=$[ $col -5 ]

while [ $sec_rem -gt 0 ]; do 
	clear 
	date 
	let sec_rem=$sec_rem-1 
	interval=$sec_rem 
	seconds=`expr $interval % 60` 
	interval=`expr $interval - $seconds` 
	minutes=`expr $interval % 3600 / 60` 
	interval=`expr $interval - $minutes` 
	hours=`expr $interval % 86400 / 3600` 
	interval=`expr $interval - $hours` 
	days=`expr $interval % 604800 / 86400` 
	interval=`expr $interval - $hours` 
	weeks=`expr $interval / 604800` 
	echo "----------------------------" 
	echo "Seconds: " $seconds 
	echo "Minutes: " $minutes 
	echo "Hours:   " $hours 
	echo "Days:    " $days 
	echo "Weeks:   " $weeks 

	echo -n "["

	progress=$[$progress + 1]
	if [ $total_time -lt 1 ] ; then
		total_time=$[$hours * 3600 + $minutes * 60 + $seconds]
	fi
	
	printf -v f "%$(echo $_R)s>" ; printf "%s\n" "${f// /=}"
	_C=7
	tput cup 7 $col

	tmp=$percent
	percent=$[$progress * 100 / $total_time]
	printf "]%d%%" $percent
	change=$[$percent - $tmp]

	_R=$[ $col * $percent / 100 ]

	sleep 1
done
printf "\n"
```

---

### Post by raleigh3 on 2019-04-07
Thanks guber2.

---

