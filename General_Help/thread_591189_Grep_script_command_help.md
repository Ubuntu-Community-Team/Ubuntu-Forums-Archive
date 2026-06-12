---
title: "Grep script command help"
date: 2007-10-25
forum: General Help
---

### Post by stonneway on 2007-10-25
Hi Chaps 

Sure this isnt the right forum for this, but you are SOOO clever :) 

I need to create a script that will be actioned by a 2nd script, which in turn performs an action based on the first scripts response (think of it as an adhoc monitoring and response thing). 

I have an smbfs mount (/media/nas) which for some reason, every few days will either unmount for no reason or will return a timeout error. To help this, i have created a file on the root of the nas share that the mount points to called 'THIS IS THE NAS'. 

I need to hack together a small script or less of commands strung together that will basically do an "ls /media/nas" and then return 0 if "THIS IS THE NAS" is found in the results and 1 if it's not found in the results. 

I've got about as far as doing the 'ls' bit :) 

Can anyone help me with this ? The following line returns "THIS IS THE NAS" if it's found, but i dont know how to make it return 0 if its found and 1 if it isn't. I know that i should be looking at the IF command and/or the EXPR command, but really thats beyond me

ls /media/nas|grep "THIS IS THE NAS" 

S.

---

### Post by kast on 2007-10-25
Something like this shoould work


**#!/bin/sh**
[B]
 nas="THIS IS THE NAS"

 if [ ls /media/nas | grep "$nas" ] then
  return 0

  else
  return 1
 
 fi[/B]

---

### Post by kast on 2007-10-25
What is that supposed to help with though? looking at it now it doesn't make much sense :)

---

### Post by stonneway on 2007-10-25
So to make that a script that i can reuse for other folders, could i replace

... ls /media/nas | grep "$nas" ....

with 

... ls $1 | grep $2 ...

and that would let me use the same script as dir_list_check "/media/othernas" "THIS IS THE OTHER NAS" etc ?

S.

---

### Post by stonneway on 2007-10-25
> **kast said:**
> What is that supposed to help with though? looking at it now it doesn't make much sense :)

Well, if the nas bombs out, the script will return 1 as the "THIS IS NAS" file wont be returned in the listing. Same applies for if the LS command returns a time out for whatever reason.

I appreciate it doesnt fix the underlying cause, but at the moment i need an elasterplast before i start doing the corrective surgery :)

---

### Post by kast on 2007-10-25
If you want the script to take input then $1 and $2 should work, but there probably a better way, there always is :)

---

### Post by stonneway on 2007-10-25
Kast,

Just tried it, but i get this error;
./dir_exists.sh: line 2: [: missing `]'
grep: is: No such file or directory
grep: the: No such file or directory
grep: nas: No such file or directory
grep: ]: No such file or directory
1

Cant see what i've done. The script i have reads as ....

#!/bin/sh
if [ ls $1 | grep $2 ] 
then
echo "0"
else
echo "1"
fi


Any ideas ? I'm sure i've done something dumb, but i cant see it.

S

---

### Post by stonneway on 2007-10-25
Right, i got it working a different way. It's not perfect but it works after a fashion.

#!/bin/sh
if [ $(expr length "$(ls $1|grep $2)") != 0 ]
then
echo 0
else
echo 1
fi


This checks the length of the result of "ls $1 | grep $2" and if it's greater than 0 then its fine. Basically, if the grep returns a result, its length will be more than 0 and its deemed fine. No result is clearly 0 in length and 1 is returned.

Only catch is that $2 has to be one word, which isn't dreadful.

---

### Post by kast on 2007-10-25
I'm going to assume your passing this script two arguments for $1 $2?
$1 would represents say a directory, and $2 would be the file/name that your trying to grep.

So..
Script file1 file2 

 and also that echoing just 0 or 1 is helping you in some way?  :)

if that's the case try 

#!/bin/sh
if [ "ls $1 | grep $2" ]
then
echo "0"
else
echo "1"
fi

---

### Post by kast on 2007-10-25
yeah that looks good! as long as it does the trick! :)

---

