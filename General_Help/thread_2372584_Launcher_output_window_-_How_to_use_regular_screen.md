---
title: "Launcher output window - How to use regular screen"
date: 2017-09-26
forum: General Help
---

### Post by pizzipie on 2017-09-26
The following CODE is run when I run the launcher. How can I get this to run in my regular laptop screen instead of the tiny black screen which is very hard to read. Plus unless I put in the last two lines of CODE 
```
 read -t 20 || exit
read -p "Press <enter> to close."
```  the output just runs so fast you can't see it and then the tiny screen closes. 

```
#!/bin/bash 
  #Sun 24 Sep 2017 18:23:28 
  
  # This is the companion script to mydb-mysqldump.sh
  # mydb-mysqlrestore.sh  will restore the files dumped by that program
  
  #File: DB-Web/mydb-mysqlrestore.sh
  
folder="/home/rick/DB-Web/mydb-bakup-folder"

# if gzip files unzip them
find "$folder" -type f -iname '*gz' -exec gunzip {} + 

   echo "-- Start"
   echo
   echo -- Restoring --
   echo
    
    for I in $(ls -d "$folder"/* ) 
        do
           echo "$I" | awk -F_ '{print $2}'      
            mysql -urick -prick < $I 
        done


echo

        
echo "-- Finish"   

read -t 20 || exit
read -p "Press <enter> to close."
```

---

### Post by efflandt on 2017-09-26
If you want it to pause in a bash script you can use **sleep** with a space and time in seconds. In a /bin/sh script you could use /bin/sleep similarly (since it is not a dash built-in) if in a minimal environment with no PATH defined.

But I am not sure how to increase font size in a terminal window if you are using a very high resolution on a small screen.

---

### Post by pizzipie on 2017-09-26
What I'm trying to say, Is there any way to use the NORMAL screen display as used on laptops instead of that little black screen (see attachment).

R

---

### Post by &amp;KyT$0P# on 2017-09-26
What terminal emulator program do you want to use?

* That is, which terminal emulator program are you calling "the NORMAL screen display"?

---

### Post by pizzipie on 2017-09-27
I guess it's the gnome terminal. 

The only time the one that I'm complaining about shows up is when I invoke a program that is contained in a  launcher.

---

### Post by &amp;KyT$0P# on 2017-09-28
Please post the output from running this command -
```
x-terminal-emulator --help
```

---

### Post by pizzipie on 2017-09-29
I got thinking about the Gnome Launcher itself and I found the answer is contained in this link: [https://ubuntu-mate.community/t/launcher-application-in-terminal-uses-mate-terminal/4918](https://ubuntu-mate.community/t/launcher-application-in-terminal-uses-mate-terminal/4918)

Specifically: > MY SOLUTION

There's many solutions, including forgetting the "Application in Terminal" altogether and just run mate-terminal with the -e option but I wanted to have my cake and eat it, too. And it's a one-time command: 

```
sudo ln /usr/bin/mate-terminal /usr/bin/gnome-terminal
```

If _gnome-terminal_ is not installed the launcher  defaults to x-term which produces that little black background window.

I hope this helps someone else who has a similar problem.

R

---

### Post by &amp;KyT$0P# on 2017-09-29
That command could cause problems down the road.  You may want to revert it like so...
```
sudo rm -v /usr/bin/gnome-terminal
```
... then do your solution in a stable way -
```
sudo ln [COLOR="#FF0000"]**-s**[/COLOR] /usr/bin/mate-terminal /usr/[COLOR="#FF0000"]**local/**[/COLOR]bin/gnome-terminal
```
The [FONT=Courier New]-s[/FONT] does a symbolic link instead of a hard link, i.e. it points to the path [FONT=Courier New]/usr/bin/mate-terminal[/FONT] (which is constant) instead of the exact file (which changes with upgrades, so you could be left stuck with an old mate-terminal binary).

Also it's best practice to put the link in [FONT=Courier New]/usr/local/bin[/FONT] so that it won't collide with installed packages.

---

