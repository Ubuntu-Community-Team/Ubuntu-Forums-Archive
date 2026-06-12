---
title: "More BASH scripting help"
date: 2013-06-12
forum: General Help
---

### Post by gforster on 2013-06-12
Before I get started, I should preface this by saying I suck at this. I'm trying to learn, but am pressed for time and the people here have been amazing. Any help is greatly appreciated.

From a list of names, I need to create ~200 files that look similar to this:


```
[Groupname;mb;typeservermb1]
     address typeservermb1.server.com #note the whitespace at the beginning of the line
```


the name of the file would be typeservermb1.conf

The items that would be variables are:
mb
type
server
mb
1
typeservermb1 (combo of other variables, I suppose)

The list of names looks like:

typeservermb1
typeserverab2
typeserverpt3
etc.

So, everything needs to be based off of the name given. I would like that list of ~200 names to come from a separate file.

Here's what I have so far (way off track, I am sure)


```
#!/bin/bash
#create files based on name
cat file.txt | while read LINE
do
    echo  >> /home/user/dir/${1}.conf   
done
#for every file created, write the following
#note - this is where I am completely lost
  $mb= #based on name of file? Or from list? Also, can be equal to mb, ab, or pt
  $type= #can be equal to bry o trk
  $server= #can be grx3 or lkh3iu
  $1= #a number - i think 100 is the highest it goes

[Groupname;$mb;$type$server$mb$1]
     address $type$server$mb$1.server.com

```

For the kicker, I potentially want to upload/insert the list of names to a webpage & have it create the files on the server. Am I looking at converting the BASH script to php?

---

### Post by Vaphell on 2013-06-12
what's in file.txt and what is this
```
cat file.txt | while read LINE
do
    echo  >> /home/user/dir/${1}.conf   
done
```
supposed to do? $1 is 1st param of the script and it will do the same thing n times where n is the line count of the file.
besides you don't have to cat file to read it, you can access it directly

```
while read line
do
  > /home/user/dir/"$line".conf
done < file.txt
```

either way describe exactly what your input data looks like (snippet would be nice) and what is supposed to go where, preferably with some small example of input -> desired output.

---

### Post by aromo on 2013-06-12
> **gforster said:**
> 
```

    echo  >> /home/user/dir/${1}.conf   

```

Should be ```
echo  >> /home/user/dir/${LINE}.conf   
```


> **gforster said:**
> 
```

     address $type$server$mb$1.server.com

```


You have to use a variable for the number from the input line and the code should be ```
${type}${server}${mb}${number}.server.com
```

---

### Post by gforster on 2013-06-12
> **Vaphell said:**
> 

either way describe exactly what your input data looks like (snippet would be nice) and what is supposed to go where, preferably with some small example of input -> desired output.

Sorry, In my attempt to not abuse the kind help, I have shot myself in the foot. 

**Input:**

a file with the following (sanitized):

typeservermb1
typeservermb2
typeservermb3
typeserverab1
typeserverab2
typeserverab3
typeserverpt1
typeserverpt2
typeserverpt3
etc,...

**Desired output:**

In a subdirectory called conf, files named

typeservermb1.conf
typeservermb2.conf
typeservermb3.conf
typeserverab1.conf
typeserverab2.conf
typeserverab3.conf
typeserverpt1.conf
typeserverpt2.conf
typeserverpt3.conf
etc,...

The contents of the typeservermb1.conf file looks like:
```
[Groupname;mb;typeservermb1]
         address typeservermb1.server.com
```

The contents of the typeserverab2.conf file looks like:
```
[Groupname;ab; typeserverab2]
        address  typeserverab2.server.com
```

The contents of the typeserverpt3.conf file looks like:
```
[Groupname;pt;typeserverpt3]
       address typeserverpt3.server.com
```

Does that make sense? I hope I am being clear.

---

### Post by HiImTye on 2013-06-12
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
are all the .conf files only two lines?

---

### Post by Vaphell on 2013-06-12
is **mb** in the header a literal fixed 'mb' ? example says yes but initial code not so much.

also, seeing your comments about possible values, you could produce a list of all possibilities with something like this

```
for mb in {mb,ab,pt}
do
  for server in {bry,trk}{grx3,lkh3iu}$mb$number
  do
    echo "[Groupname;$mb;$server]
      address $server.domain.com" > $server.conf
  done
done
```
no idea if you need something like this though, seeing that you want to read the list from file.

---

### Post by aromo on 2013-06-12
Assuming each line is read into a variable called line:
```
type=`echo $line|cut -c 1-4`
server=`echo $line|cut -c 5-10`
mb=`echo $line|cut -c 11-12`

echo "[Groupname;${mb};${line}]" >> ${line}.conf
echo "        address ${line}.${server}.com" >> ${line}.conf
```

---

### Post by gforster on 2013-06-12
> **Vaphell said:**
> is **mb** in the header a literal fixed 'mb' ? example says yes but initial code not so much.

No, stupid me. In the example, they should be mb, ab, and pt respectively. Sloppy copy/paste job on my behalf. I will edit that post to correct my error.

---

### Post by gforster on 2013-06-12
> **HiImTye said:**
> [CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
are all the .conf files only two lines?

Yes, that is correct.

---

### Post by Vaphell on 2013-06-12
given that you pretty much want to cut the read line to pieces to extract chunks of it, is there any rule to it? is width of $type fixed or variable? Your example is too general and doesn't make it clear. Comments in op indicate it's variable width but the example itself that everything but 2chars+number at the end is fixed.

---

### Post by gforster on 2013-06-13
> **Vaphell said:**
> given that you pretty much want to cut the read line to pieces to extract chunks of it, is there any rule to it? is width of $type fixed or variable? Your example is too general and doesn't make it clear. Comments in op indicate it's variable width but the example itself that everything but 2chars+number at the end is fixed.

each $variable is a variable width. At least, potentially. For the most part, looking through the list, it is fixed, but I can guarantee there is an oddball or two in there, so the width should be variable to be safe.

---

### Post by gforster on 2013-06-13
The more I look at it, the more I think there are, in reality only two real variables that matter:

1) Each line (obviously, they are all different)
2) The only *real variable that seems tough to get & has to be extracted from each line - The $mb

As I look closer, the mb is variably either 2 or 3 characters followed by a number that is variably either 2 or 3 characters.

I have also double & triple checked that the $mb variable is always preceded by either ex or ys


Now, I could have likely created these manually, one at a time, but I am more interested in the HOW/WHY of scripting something like this out. Again, many thanks for the help.

---

### Post by Vaphell on 2013-06-13
something like this should do
```
while read -r server
do
  mb=$( echo "$server" | sed -r 's/.*(er|ys)(.+)[0-9]+$/\2/' )
  echo "[group;$mb;$server]
     $server.domain.com" > "$server.conf"
done < servers.txt

```

is it possible in your case to generate servers automatically instead of supplying them via file as i mentioned earlier? if let's say you have prefix, core, suffix, number each in 2 variants it's trivial to generate all possibilities, eg

```
for name in {pre1,pre2}{core1,core2}{sfxA,sfxB}{1..3}
do
  echo "$name"
done
```

```
pre1core1sfxA1
pre1core1sfxA2
pre1core1sfxA3
pre1core1sfxB1
pre1core1sfxB2
pre1core1sfxB3
pre1core2sfxA1
pre1core2sfxA2
pre1core2sfxA3
pre1core2sfxB1
pre1core2sfxB2
pre1core2sfxB3
pre2core1sfxA1
pre2core1sfxA2
pre2core1sfxA3
pre2core1sfxB1
pre2core1sfxB2
pre2core1sfxB3
pre2core2sfxA1
pre2core2sfxA2
pre2core2sfxA3
pre2core2sfxB1
pre2core2sfxB2
pre2core2sfxB3

```

---

