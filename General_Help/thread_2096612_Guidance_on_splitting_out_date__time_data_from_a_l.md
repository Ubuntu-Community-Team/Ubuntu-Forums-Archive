---
title: "Guidance on splitting out date / time data from a line"
date: 2012-12-20
forum: General Help
---

### Post by cbillson on 2012-12-20
Each line of my log file starts with the date / time in the format (dd/mm-hh:mm:ss.sss) 19/12-21:54:50.381

My next step with this data is to extract it based on the rest of the line and compare each one against others to understand the time between tasks.

At this stage i'd like to understand how i can take specific fixed areas of data and use that as a variable. in Dos you could use a command similar to Set dd=%cdate:~0,2% to extract the day as being the first two characters from the variable cdate.

I apologise for taking up the communities time, but could anyone break down the command so i can understand.

I know the command:

myvar=$(wc -l file.txt | awk -F" " '{ print $1 }')

sets $myvar to "777"

This is because the output of wc -l file is 777 path/file" where 'file' has 777 lines. 

i assume this is because the two pieces of text are split into variables $1 and $2 though i'm lost when it comes to taking parts of words or data where they are joined (such as 01/01 (dd/mm))

any help / guidance appreciated

Cheers
Chris

---

### Post by steeldriver on 2012-12-20
I'm a bit confused about what you are asking

In your wc example, it is awk that is doing the text splitting - based on a space delimiter (the -F" " parameter - called the input field separator in awk terminology)

OTOH if the file isn't easily delimited, you could use regular expressions to extract the datetimes

If you can give an example of exactly what you want to do I'm sure one of us can point you in the right direction

---

### Post by dcstar on 2012-12-21
> **cbillson said:**
> Each line of my log file starts with the date / time in the format (dd/mm-hh:mm:ss.sss) 19/12-21:54:50.381

My next step with this data is to extract it based on the rest of the line and compare each one against others to understand the time between tasks.

At this stage i'd like to understand how i can take specific fixed areas of data and use that as a variable.
...........


```
man cut
```

---

### Post by cbillson on 2012-12-21
> **dcstar said:**
> ```
man cut
```

Thanks, had a look at this command and it does look like it will do what i need, though i cannot get my head round their examples!

in Dos, its fairly logical, dd=%cdate:~0,2% <- start at position 0 and take two characters. move these two digits anywhere along the string to snip the data required.
    **echo** **abcdefghi** **|** **cut** **-c6,2,4-7,1**         yields **"abdefg"** .

I can see this is doing similar, but i cannot for the life of me understand why this command starts with a 6 or ends with a 1.

Can anyone translate? :)

Thanks
Chris

---

### Post by cbillson on 2012-12-21
Although its probably not the most elegant solution, i think i've sussed it enough to get what i need..

19/12-22:48:34.186  INFO mydata

day=$(cat split/files/myfile | grep mydata | cut -c1-2)
month=$(cat split/files/myfile | grep mydata | cut -c4-5)
hour=$(cat split/files/myfile | grep mydata | cut -c7-8)
min=$(cat split/files/myfile | grep mydata | cut -c10-11)
sec=$(cat split/files/myfile | grep mydata | cut -c13-18)

echo $day
echo $month
echo $hour
echo $min
echo $sec

---

### Post by steeldriver on 2012-12-21
if your date strings are in a format that your locale understands, then you could do something more elegant (and - more importantly - more robust) using the 'date' function e.g.

```

$ datestring="12-12-19 22:48:34.186"
$ month=$(date '+%m' --date="$datestring"); echo "$month"
12
$ day=$(date '+%d' --date="$datestring"); echo "$day"
19

```

---

