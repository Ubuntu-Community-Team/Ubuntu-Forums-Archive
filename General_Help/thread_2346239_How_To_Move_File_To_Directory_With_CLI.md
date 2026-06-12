---
title: "How To Move File To Directory With CLI"
date: 2016-12-12
forum: General Help
---

### Post by AUDIOTEK on 2016-12-12
How can I move a file using CLI from the desktop let's say to Documents?

I tried the following but I get mv: cannot stat test.txt no such file or directory

I'm currently in /Documents

mv test.txt documents/

I also created a sub directory in /Documents

mkdir temp

I also would like to move the test.txt from /Desktop to the temp directory in /Documents

---

### Post by Bucky Ball on 2016-12-12
```
mv test.txt documents/
```

What is 'documents/'?

Running by the above, you should have: 

```
mv test.txt /Documents
```

... but doubt that is the right path, either. I don't have 'Documents' folder, but if I did, it would be at

```
/home/username/Documents
```

I'd say yours is too so you are missing a chunk out of your command. While in the same folder as the file you want to move:

```
mv test.txt /home/AUDIOTEK/Documents
```

... presuming your 'username' is 'AUDIOTEK' on your computer as well as here. You may need to add 'sudo':

```
sudo mv test.txt /home/AUDIOTEK/Documents
```

... but try without first. Please use [code] tags for terminal output and commands when posting here. See the green link in my signature, bottom of post. Thanks.

---

### Post by yetimon_64 on 2016-12-12
You have a syntax probem, if you are in the Documents folder in the terminal and you want to move a file from the desktop to where you are. 
```
mv ~/Desktop/test.txt .
```
You have to tell mv where the file is first with ~/Desktop/test.txt and then where to put it, in this case you are already in Documents in the terminal so the period mark "." will do so. 

It is best when learning the terminal to use absolute paths so ...
Try ```
mv ~/Desktop/test.txt ~/Documents/
```
... will work from anywhere, whereas the first code example above will only work if you are in the Documents folder in terminal.

The ~ symbol in use above is a system variable for the home folder of the user, eg /home/<your-username>.

Just remember the mv syntax, "mv <source> <destination>", and use absolute paths even if you are in either the source or destination folder for clarity. Once you get used to the syntax you can often drop the path to a file if you are in the source or destination folder.

With the subfolder "temp" example you will have to recreate the file on the desktop or use mv to move it back from the Documents folder to the desktop (as it no longer exists there if the first move works right). Once you do so just add the temp folder name to the mv command path (use the second code example with the absolute paths in use for easier understanding).

eg. ```
mv ~/Desktop/test.txt ~/Documents/temp/
```

---

### Post by AUDIOTEK on 2016-12-12
Great thanks for the reply I will try all of the following

Another question  I'd like to have gedit to open in background mode when I launch it from bash.  
Manually I do the following and that will open gedit in bg mode so I can go back and forth with the shell an gedit

```
gedit &
```

or

```
gedit textfile.txt &
```


Is the file file to be edited bash.bashrc?

```
/etc/bash.bashrc
```

If I do```
gedit /etc/bash.bashrc
```
and add ```
gedit &
```
I cannot save the file.  I can only do save as which probably indicates I can't modify that file

---

### Post by Bucky Ball on 2016-12-12
> **AUDIOTEK said:**
> 
Another question  I'd like to have gedit to open in background mode when I launch it from bash.  
Manually I do the following and that will open gedit in bg mode so I can go back and forth with the shell an gedit

```
gedit &
```

Is the file file to be edited in bash.bashrc?

```
/etc/bash.bashrc
```

Nothing to do with this or the title of the thread. Generally advised to post one support request a thread here so suggest you start another thread. Having said that, someone will probably disregard and answer it anyhow. Good luck.

---

### Post by oldos2er on 2016-12-12
In order to edit any file outside of your home folder, you need to use admin (or root) privileges. ```
sudo -H gedit
``` When editing system files it is wise to make a backup copy first.

Why do you want to edit /etc/bash.bashrc ?

---

### Post by Bashing-om on 2016-12-12
AUDIOTEK; Hello ..

In linux case is important .. in that d does not equate to D . Is this what you are suffering from ?

With the (P)resent (W)orking (D)irectory as your home then this :
```

cp test.txt Documents/temp/

```should work .
Where you can see if the target file does exist:
```

ls -al test.txt

```
bear in mind that if your PWD is Documents, then the system from that perspective will not see the files on you desktop. Here the system only "sees" the contents of the Documents directory . One can always give the explicit full path of the source and the destination to effect the copy operation. ( ~/ is shorthand for /home/<username ) .. 
one could run form anywhere :
```

mv ~/test.txt ~/Documents/temp/

```
which is equivalent " mv /home/AUDIOTEK/test.txt /home/AUDIOTEK/Documents/temp/test.txt"

Ya see;
[INDENT][INDENT]where you are at
[INDENT][INDENT][INDENT]is also important
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by AUDIOTEK on 2016-12-12
What's the 

[COLOR=#000000][FONT=&quot]sudo -H gedit[/FONT][/COLOR][COLOR=#000000][FONT=&quot]

[/FONT][/COLOR]Supposed to do?[COLOR=#000000][FONT=&quot][/FONT][/COLOR]

---

### Post by AUDIOTEK on 2016-12-12
> **yetimon_64 said:**
> You have a syntax probem, if you are in the Documents folder in the terminal and you want to move a file from the desktop to where you are. 
```
mv ~/Desktop/test.txt .
```
You have to tell mv where the file is first with ~/Desktop/test.txt and then where to put it, in this case you are already in Documents in the terminal so the period mark "." will do so. 

It is best when learning the terminal to use absolute paths so ...
Try ```
mv ~/Desktop/test.txt ~/Documents/
```
... will work from anywhere, whereas the first code example above will only work if you are in the Documents folder in terminal.

The ~ symbol in use above is a system variable for the home folder of the user, eg /home/<your-username>.

Just remember the mv syntax, "mv <source> <destination>", and use absolute paths even if you are in either the source or destination folder for clarity. Once you get used to the syntax you can often drop the path to a file if you are in the source or destination folder.

With the subfolder "temp" example you will have to recreate the file on the desktop or use mv to move it back from the Documents folder to the desktop (as it no longer exists there if the first move works right). Once you do so just add the temp folder name to the mv command path (use the second code example with the absolute paths in use for easier understanding).

eg. ```
mv ~/Desktop/test.txt ~/Documents/temp/
```


That's it   I tried it and it works and make sense now.  Thanks for explaining it better than the course I'm taking online.   I'll have to remember the   mv <source> <destination"  totally make sense but it'd mot explained that well. Thanks

---

### Post by Bashing-om on 2016-12-13
AUDIOTEK; Well

> **AUDIOTEK said:**
> What's the 

[COLOR=#000000][FONT=&quot]sudo -H gedit[/FONT][/COLOR][COLOR=#000000][FONT=&quot]

[/FONT][/COLOR]Supposed to do?[COLOR=#000000][FONT=&quot][/FONT][/COLOR]

Now you are getting into the "guts".
As you know 'sudo' gives you administrative authority . But it is "root" and operating at a high level . So high that what it touches also can be owned by root So what you want is to keep this from happening particularly in directories owned by "you" and directed at ANY GUI application that you start with root privileges .
see :
```

man sudo

```
where we see:
> 
-H, --set-home
                 Request that the security policy set the HOME environment
                 variable to the home directory specified by the target user's
                 password database entry.  Depending on the policy, this may
                 be the default behavior.

You may also want to investigate 'gksudo' and 'gksu' that is now depreciated in favor of
pkexe :)
see also:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

But do exercise a high degree of discretion ! Read and head but DO NOT do until the need to do arises !!

[INDENT][INDENT]how do you spell
[INDENT][INDENT]borked !
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by vasa1 on 2016-12-13
> **AUDIOTEK said:**
> ...

Another question ...
As Bucky Ball said [here]("https://ubuntuforums.org/showthread.php?t=2346239&p=13581979#post13581979"), please ask just one question per thread. Thanks!

---

