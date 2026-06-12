---
title: "Help installing program"
date: 2006-11-25
forum: General Help
---

### Post by thegino on 2006-11-25
Hi 

I D/l tunapie 1.3 to watch shoutcast tv, I'm having a problem installing it

i dont know how to install .sh commands, I tried first I extract file then  typed

cd /(username)/desktop/tunapie-1.3 

then

sh ~/desktop/tunapie-1.3 compile

that didnt work
so the i tried

sh ~/desktop/tunapie-1.3 install.sh

but its not working,

i did this all as root and user and still nothing 

Dont know if thats the right way to install script :confused: 

also i opened file and double clicked in install.sh file and ran it in terminal but it flashed the terminal and closed it fast
I would like the right way to install a .sh file or am i missing a step

Also in tunapie folder there is a file called compile it opens with text editor and reads "import tunapie" thats all,  

Thanks to all who help :)

---

### Post by taurus on 2006-11-25
```
cd ~/Desktop/tunapie-1.3
chmod 755 install.sh
sudo ./install.sh
```

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by thegino on 2006-11-25
I followed the steps you gave me after typed sudo .install.sh i got this


Traceback (most recent call last):
  File "src/compile", line 1, in ?
    import Tunapie
  File "/home/(username)/Desktop/tunapie-1.3/src/Tunapie.py", line 23, in ?
    import wxversion
ImportError: No module named wxversion
cp: cannot stat `src/*.jpg': No such file or directory

is wxversion? something i need to install or is this tar.gz package corrupted

---

### Post by taurus on 2006-11-25
Is there a README or INSTALL in ~/Desktop/tunapie-1.3?  What's the output of this command then?

```
ls -la ~/Desktop/tunapie-1.3
```

---

### Post by thegino on 2006-11-25
total 72
drwxr-xr-x 3 frank frank  4096 2006-11-19 07:54 .
drwxr-xr-x 3 frank frank  4096 2006-11-25 11:04 ..
-rw-r--r-- 1 frank frank     0 2006-11-19 07:50 build-stamp
-rw-r--r-- 1 frank frank  8422 2006-11-19 07:50 CHANGELOG
-rw-r--r-- 1 frank frank     0 2006-11-19 07:50 configure-stamp
-rw-r--r-- 1 frank frank 18009 2006-11-19 07:50 COPYING
-rw-r--r-- 1 frank frank  1180 2006-11-19 07:50 INSTALL
-rwxr-xr-x 1 frank frank   354 2006-11-19 07:50 install.sh
-rw-r--r-- 1 frank frank  1790 2006-11-19 07:50 README
drwxr-xr-x 2 frank frank  4096 2006-11-19 07:54 src
-rwxr-xr-x 1 frank frank    53 2006-11-19 07:50 tunapie
-rw-r--r-- 1 frank frank  1834 2006-11-19 07:50 tunapie.1
-rw-r--r-- 1 frank frank   175 2006-11-19 07:50 tunapie.desktop
-rwxr-xr-x 1 frank frank   186 2006-11-19 07:50 uninstall.sh

is what was giving

---

### Post by taurus on 2006-11-25
So what does the INSTALL say?

```
more INSTALL
(hit space bar for the new 24 lines...
```

---

### Post by thegino on 2006-11-25
hey i got it to work with wxpython somehow i installed wxpython and ran sudo ./install not in python terminal but root and then clicked on tunapie execute and the program started lol 

Thanks taurus for the help  sorry to take your time guess i just need wxpython wierd EH!:redface: 

dont ask how it (I have no clue when it comes to python) worked it just worked LOL, looked up on google "how to install tunapie" and showed me that i had to install wxpython, weird thing its not on developer website

---

### Post by taurus on 2006-11-25
Usually in either README or INSTALL, it will tell you what you need to have in your system first, libraries, before you can install the program.  That's why I asked about those two files, especially the INSTALL...

---

### Post by thegino on 2006-11-25
> **thegino said:**
> total 72
drwxr-xr-x 3 frank frank  4096 2006-11-19 07:54 .
drwxr-xr-x 3 frank frank  4096 2006-11-25 11:04 ..
-rw-r--r-- 1 frank frank     0 2006-11-19 07:50 build-stamp
-rw-r--r-- 1 frank frank  8422 2006-11-19 07:50 CHANGELOG
-rw-r--r-- 1 frank frank     0 2006-11-19 07:50 configure-stamp
-rw-r--r-- 1 frank frank 18009 2006-11-19 07:50 COPYING
-rw-r--r-- 1 frank frank  1180 2006-11-19 07:50 INSTALL
-rwxr-xr-x 1 frank frank   354 2006-11-19 07:50 install.sh
-rw-r--r-- 1 frank frank  1790 2006-11-19 07:50 README
drwxr-xr-x 2 frank frank  4096 2006-11-19 07:54 src
-rwxr-xr-x 1 frank frank    53 2006-11-19 07:50 tunapie
-rw-r--r-- 1 frank frank  1834 2006-11-19 07:50 tunapie.1
-rw-r--r-- 1 frank frank   175 2006-11-19 07:50 tunapie.desktop
-rwxr-xr-x 1 frank frank   186 2006-11-19 07:50 uninstall.sh 

Same thing with more install no option to hit space goes back to cmd line

but its installed and working now i need a good player to play .NSV i have totem but it does not work, playes well with mplayer but no option to control audio or full screen mode, does not work with kmplayer, kaffeine,VLC and xine 

and thanks for the help sorry to take up so much of your time i will follow those instructions you gave to install scripts

---

