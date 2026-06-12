---
title: "Help with my mounting script"
date: 2013-08-07
forum: General Help
---

### Post by 7hr08ik2 on 2013-08-07
There is nothing wrong my setup so far. It works for me, and everything is hunk dory. I am just trying to figure out 1 small thing....how to get my script to show stars when i type in my password.

I have 5 HDD's that are all truecrypt encrypted, and i have a custom script that runs through terminal on system start. The script asks for the password, then mounts the 5 HDD's with said password. All i want is for the script to show me stars for the password i type in.

Here is the script:-

```
#!/bin/bash

echo "Enter the password now ... "
echo

oldConfig=`stty -g`
stty -echo
read password
stty $oldConfig

echo "Checking ... "
echo
sleep 3
echo "Opening Pandora's Box ..."
echo
sleep 1
echo

truecrypt -t /dev/TC-c /media/1 --password="$password"  -k "" --protect-hidden=no
truecrypt -t /dev/TC-d1 /media/2 --password="$password"  -k "" --protect-hidden=no
truecrypt -t /dev/TC-a1 /media/3 --password="$password"  -k "" --protect-hidden=no
truecrypt -t /dev/TC-e1 /media/4 --password="$password"  -k "" --protect-hidden=no
truecrypt -t /dev/TC-b5 /media/5 --password="$password" -k "" --protect-hidden=no


echo
echo "Drives mounted ... Closing in ... "
sleep 1
echo
echo "... 3 ..."
sleep 1
echo
echo "... 2 ..."
sleep 1
echo
echo "... 1 ..."
sleep 1
echo
echo "... Goodbye ..."


```

So what im wanting is for the initial part of the script (before truecrypt is called) to ask for the password as it does now, but show me stars for the typed in password.

---

### Post by 7hr08ik2 on 2013-08-07
Oh i do love this......I ask the forums and then i find the answer myself!!!

But heres what i fdound anyways, incase someone else needs it...

Go this from [here]("http://stackoverflow.com/questions/1923435/how-do-i-echo-stars-when-reading-password-with-read")
```
unset password
prompt="Enter Password:"
while IFS= read -p "$prompt" -r -s -n 1 char
do
    if [[ $char == $'\0' ]]
    then
        break
    fi
    prompt='*'
    password+="$char"
done
echo
echo "Done. Password=$password"
```

Tweaked it a smidge so it works for me....and now my script looks like this

```
#!/bin/bash

echo "Give me the Password.."

unset password
prompt=": "
echo
while IFS= read -p "$prompt" -r -s -n 1 char
do
    if [[ $char == $'\0' ]]
    then
        break
    fi
    prompt='*'
    password+="$char"
done

echo
echo
echo "Checking ... "
echo
sleep 3
echo "Opening Pandora's Box ..."
echo
sleep 1
echo

truecrypt -t /dev/TC-c /media/1--password="$password"  -k "" --protect-hidden=no
truecrypt -t /dev/TC-d1 /media/2 --password="$password"  -k "" --protect-hidden=no
truecrypt -t /dev/TC-a1 /media/3 --password="$password"  -k "" --protect-hidden=no
truecrypt -t /dev/TC-e1 /media/4 --password="$password"  -k "" --protect-hidden=no
truecrypt -t /dev/TC-b5 /media/5 --password="$password" -k "" --protect-hidden=no

echo
echo "Drives mounted ... Closing in ... "
sleep 1
echo
echo "... 3 ..."
sleep 1
echo
echo "... 2 ..."
sleep 1
echo
echo "... 1 ..."
sleep 1
echo
echo "... Goodbye ..."

```

Now my output in terminal is...

```
Give me the Password..

: ******************

Checking ...

Opening Pandora's Box ...

blah...blah...blah.....
```

---

### Post by Vaphell on 2013-08-07
doesn't work too well with backspace which makes typos annoying to correct.

you can find upgraded version here
[http://askubuntu.com/questions/299437/how-can-i-use-the-backspace-character-as-a-backspace-when-entering-a-password](http://askubuntu.com/questions/299437/how-can-i-use-the-backspace-character-as-a-backspace-when-entering-a-password)

edit: improved version preventing backspace from working when pw is 0 chars long.
```
#!/bin/bash

prompt=': '
while IFS= read -rs -p "$prompt" -n 1 char
do
    [[ $char == $'\0' ]] && break
    if [[ $char == $'\177' ]]
    then
      (( ${#password} == 0 )) && prompt='' && continue
      prompt=$'\b \b'
      password=${password%?}
    else
      prompt='*'
      password+="$char"
    fi 
done
echo
```

---

