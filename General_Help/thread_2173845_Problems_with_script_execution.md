---
title: "Problems with script execution"
date: 2013-09-11
forum: General Help
---

### Post by LinuxUser666 on 2013-09-11
Hello fellow Ubuntu users, I am running on Ubuntu 12.04, 32-bit. I am having some trouble with executing script I need for rooting my tablet. I followed the instructions as seen on here: [http://www.neumrli.com/blog/2012/12/30/root-your-alcatel-onetouch-t10/](http://www.neumrli.com/blog/2012/12/30/root-your-alcatel-onetouch-t10/)
I run the script with ./RunMe.bat but it ends me with message like this: 
```
slayer1@Slayer1-desktop:~/Desktop/root-toolkit$ ./RunMe.bat ./RunMe.bat: line 1: @echo: command not found
./RunMe.bat: line 2: COLOR: command not found
======================================================================
= This script will root your Android phone with adb restore function =
./RunMe.bat: line 5: syntax error near unexpected token `('
'/RunMe.bat: line 5: `echo = Script by Bin4ry (thanks to Goroh_kun and tkymgr for the idea)     =



```
Does anyone know what is going on and how may I fix it because I could really use help with that.

My regards, stay brutal.:)

---

### Post by dcstar on 2013-09-17
You can't run Windows scripts on Linux. Ask on that website if there is a Linux version.

---

### Post by LinuxUser666 on 2013-09-26
Since nobody had any good idea or suggestion I found out something useful and that is actually working:
1st thing: install wine
```
sudo apt-get install wine
```
2nd thing you do:
```
 wine cmd
``` 
3rd thing:
You do ```
 cd path_to_your_script's_dir
``` 
Then you enter your scripts name and execute it. 

My regards, stay brutal.

---

