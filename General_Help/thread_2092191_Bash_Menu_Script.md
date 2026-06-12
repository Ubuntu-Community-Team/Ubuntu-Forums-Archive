---
title: "Bash Menu Script"
date: 2012-12-07
forum: General Help
---

### Post by cowsquad on 2012-12-07
HOMEWORK ASSIGNMENT
I am creating a bash Menu script that would prompt a user to select options. Option 4 is for changing directory. I have accomplished this by using the following:
change_directory () {
read -p ' Please enter your directory :' dir
   cd "/$dir"

But my question is, what if the user inputs a directory that isnt in the / path? How could I go from there? I have no clue in how to do that. So i need your help guys. 
thank you in advance

---

### Post by CaptainMark on 2012-12-07
You should use an If statement and nest the cd command inside like so ```
if [ -d "/$dir" ]; then
    cd "/$dir"
fi
```This allows you to only execute commands if the statement (the bit between [ and ] ) evaluate to true, in this case we ask bash if the statement [ is $dir a directory ] evaluates to true, if it is bash runs everything from "then" to "fi"
To add alternative options there is also the "elif" option where you can specify a second possible statement, and the "else" option which is a failsafe incase none of the statements evaluate to true, for example```

if [ $dir is in users home dir ]; then
    cd /$dir
elif [ $dir is a directory outside of users home ]; then
    echo $dir isn't your folder
else
    echo $dir isn't a directory
fi
```
If deliberately not used proper code here to keep it easy to read for beginners

---

### Post by cowsquad on 2012-12-07
> **CaptainMark said:**
> You should use an If statement and nest the cd command inside like so ```
if [ -d "/$dir" ]; then
    cd "/$dir"
fi
```This allows you to only execute commands if the statement (the bit between [ and ] ) evaluate to true, in this case we ask bash if the statement [ is $dir a directory ] evaluates to true, if it is bash runs everything from "then" to "fi"
To add alternative options there is also the "elif" option where you can specify a second possible statement, and the "else" option which is a failsafe incase none of the statements evaluate to true, for example```

if [ $dir is in users home dir ]; then
    cd /$dir
elif [ $dir is a directory outside of users home ]; then
    echo $dir isn't your folder
else
    echo $dir isn't a directory
fi
```
If deliberately not used proper code here to keep it easy to read for beginners

thank you very much for your explanation. I do get your code, What I dont get is: How do I create a condition that would state that $dir is in my Home directory?
I have tried if [ $dir = $HOME ]; then 
cd "$HOME"

I am definitely doing something wrong, since I am a novice in this.

---

### Post by Vaphell on 2012-12-07
$HOME is /home/yourusername
$dir is dir

glue these 2 together with / to form the full path and check with -d its existence.

---

### Post by cowsquad on 2012-12-07
> **Vaphell said:**
> $HOME is /home/yourusername
$dir is dir

glue these 2 together with / to form the full path and check with -d its existence.

I just that and I came out with this code

```
change_directory () {
        read -r -p 'please enter your directory ' dir
        if [ -d "/$dir" ]
        then
                cd "/$dir"; echo "You're in `pwd` and these are your files"
                sleep 1.5; ls | more
        elif [ -d "/home/$dir" ]
        then
                cd "/home/$dir"; echo "You're in `pwd` and these are your files"
                sleep 1.5; ls | more
        elif [ -d "$HOME/$dir" ]
        then
                cd "$HOME/$dir"; echo "You're in `pwd` and these are your files"
                sleep 1.5; ls | more
        else
                echo "$dir name does not exist"
        fi
        read -r -p 'Please [ENTER] to continue...'
        clear
```

That gave me access to / and $HOME. And i probably am gonna leave it like that. I can't figure out how to cd to a different directory in different path, like for example: /etc/random or /home/user/Documents/random.

---

