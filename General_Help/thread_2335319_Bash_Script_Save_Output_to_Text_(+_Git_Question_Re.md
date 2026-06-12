---
title: "Bash Script Save Output to Text (+ Git Question Regarding a Script to git reset)"
date: 2016-08-27
forum: General Help
---

### Post by calimer on 2016-08-27
I hope this is the proper place to post, but I have a bash script to update all my git repos.  I'm trying to make it so that from inside the script it posts the results updating.  From the command line if I do ./updategits.sh > update.log I do get a file.  But I'd like to just be able to double click the script and have it save the log instead of manually having to type it in every time.  I'm rather new to Linux so I could be missing something super simple.  I have googled it extensively as well but everything I've tried hasn't worked.

```
#!/bin/bash

# store the current dir
CUR_DIR=$(pwd)

# Let the person running the script know what's going on.
echo "\n\033[1mPulling in latest changes for all repositories...\033[0m\n"

# Find all git repositories and update it to the master latest revision
for i in $(find . -name ".git" | cut -c 3-); do
    echo "";
    echo "\033[33m"+$i+"\033[0m";

    # We have to go to the .git parent directory to call the pull command
    cd "$i";
    cd ..;

    # finally pull
    git pull origin master;

    # lets get back to the CUR_DIR
    cd $CUR_DIR
done

echo "\n\033[32mComplete!\033[0m\n"
read
```

Also as a side question, I had the gits originally on a windows HD and I think maybe something to do with spaces sometimes keeps the gits from updating properly so I have to do a git reset --hard origin/master  I'd like to be able to just have do that to all the gits so they are all set instead of me having to do it manually for every git that has a problem.  There are well over 100 gits so it'd be a big help.  

Thank you so much for any insight!!!

---

### Post by &amp;KyT$0P# on 2016-08-27
Pipe everything you want to output to the logfile into [FONT=Courier New]tee[/FONT] (use [FONT=Courier New]-a[/FONT] flag for appending to the logfile).  See tee's man page for more information.

> **calimer said:**
> Also as a side question, I had the gits originally on a windows HD and I think maybe something to do with spaces sometimes keeps the gits from updating properly so I have to do a git reset --hard origin/master  I'd like to be able to just have do that to all the gits so they are all set instead of me having to do it manually for every git that has a problem.  There are well over 100 gits so it'd be a big help.  
Use [for loop]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-7.html")?

---

### Post by sudodus on 2016-08-27
> **calimer said:**
> ... But I'd like to just be able to double click the script and have it save the log instead of manually having to type it in every time.  I'm rather new to Linux so I could be missing something super simple.

A simple solution is to make an alias:

```
alias u='./updategits.sh > update.log'
```

or to run it from any place, add the paths (use the real paths instead of path1 and path2)

```
alias u='/path1/updategits.sh > /path2/update.log'
```

So if you have a terminal window open, you simply type ***u*** (and the Enter key) to run the command.

In order to make it persistent, you add a line in ~/.bashrc next to the other aliases, and the next terminal window you open will have this alias activated.

It is also possible to create a desktop file for it (a file that you double-click to run), but it is more complicated, and once you get used the terminal window, it is very easy to use aliases for the commands, that you use often. (I have a terminal window open most of the time.)

---

### Post by calimer on 2016-08-27
That alias suggestion is awesome!  I didn't know you could do something like that.  Thanks so much!  I'll also have to check into "tee"  Learning so much :)  Thank you both!

EDIT - I did notice it is important where I launch the command from.  I launched from the desktop and it updated ALL my gits.  Hoping a cd /path/to/the/gits at the start of the script will work :)  It is running now so I can't test yet.

---

### Post by sudodus on 2016-08-28
Yes, I think a **cd /path/to/the/gits** will do the trick for you. Good luck and let us know the result :-)

---

### Post by calimer on 2016-08-28
It works great, thank you so much!  I also added in a bit so that the log pops up in a text editor when it is done.  I can't believe how powerful aliases are.  Linux is amazing me more and more every day, so many awesome customizations you can make!!

---

### Post by sudodus on 2016-08-28
Congratulations :KS

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

