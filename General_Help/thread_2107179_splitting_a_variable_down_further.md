---
title: "splitting a variable down further"
date: 2013-01-21
forum: General Help
---

### Post by cbillson on 2013-01-21
if i had a variable $myvar that was equal to 1234-123-12 is there any way i could take the elements split by - to get:
 
$var1=1234
$var2=123
$var3=12
 
the only issue i have is the data between - is not fixed length, so i cant take a charector position and use that ..
 
Cheers
Chris

---

### Post by steeldriver on 2013-01-21
You could do simple substitutions like

```
$ echo "${myvar##*-}"
12
$ echo "${myvar%%-*}"
1234
$ 

```(remove the longest matching front string and longest matching back string respectively) or maybe change the delimiter to a space then it's easy to construct it as an array

```
$ echo "${myvar//-/ }"
1234 123 12
$ arr=(${myvar//-/ })
$ echo ${arr[0]}
1234
$ echo ${arr[1]}
123
$ echo ${arr[2]}
12

```

---

### Post by Vaphell on 2013-01-21
is this perl?

```
@arr = split(/-/, $myvar)
```
you can access individual elements by $arr[index]


expanding steeldriver's bash:

```
$ str='1-22-333-4444-55555'
$ IFS=- read -a arr <<< "$str"
$ printf "%s\n" "${arr[@]}"
1
22
333
4444
55555
$ printf "%s\n" "${arr[3]}"
4444

```

---

### Post by cbillson on 2013-01-22
Managed it in the end with a bit of trial and error
 
 
[FONT=Calibri][SIZE=3]str1=12-123-1234-12[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]var1=$(echo $str1 | cut -f1 -d-)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]var2=$(echo $str1 | cut -f2 -d-)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]var3=$(echo $str1 | cut -f3 -d-)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]var4=$(echo $str1 | cut -f4 -d-)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]echo $var1[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]echo $var2[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]echo $var3[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]echo $var4[/SIZE][/FONT]

---

