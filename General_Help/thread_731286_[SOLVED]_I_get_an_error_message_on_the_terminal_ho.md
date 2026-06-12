---
title: "[SOLVED] I get an error message on the terminal how do i fix this?"
date: 2008-03-21
forum: General Help
---

### Post by north-east-angler on 2008-03-21
i have enter anything  into the terminal and i get thefollowing mesage below, 
[COLOR="Red"]
andrew@andrew-laptop:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for andrew:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem[/COLOR]. 



im a complete newbie at this stuff and im starting to get stressed out with all the faffing about i have to to just to go on youtube and listen to music etc.

---

### Post by overdrank on 2008-03-21
> **north-east-angler said:**
> i have enter anything  into the terminal and i get thefollowing mesage below, 
[COLOR="Red"]
andrew@andrew-laptop:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for andrew:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem[/COLOR]. 



im a complete newbie at this stuff and im starting to get stressed out with all the faffing about i have to to just to go on youtube and listen to music etc.

Hi and then you need to run the command ```
sudo dpkg --configure -a
```
and you may need to run also  ```
sudo apt-get install -f
```

---

### Post by north-east-angler on 2008-03-21
Thanks very much my good man

---

### Post by north-east-angler on 2008-03-21
But now i get this
[COLOR="Red"]
andrew@andrew-laptop:~$ sudo dpkg --configure -a
Setting up sun-java6-doc (6-03-0ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort[/COLOR]

---

### Post by forrestcupp on 2008-03-21
Well, you can try just doing what it says.  Go to that web site and download the file it tells you to download.  Save the file somewhere in your /home directory and open a terminal.  Use the 'cd' command to change to the directory where you saved the file.  Assuming the file is really called jdk-6-doc.zip, you can do this
```
sudo chown root ./jdk-6-doc.zip
```
to change its ownership to root, then
```
sudo mv ./jdk-6-doc.zip /tmp
```
to move it to /tmp, like it says.

Then rerun the commands you were trying, and hopefully it will work this time.

---

