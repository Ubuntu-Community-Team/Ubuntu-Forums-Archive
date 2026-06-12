---
title: "Permission Denied ?"
date: 2007-04-24
forum: General Help
---

### Post by Ne0z on 2007-04-24
Hi, 

any idea what is a filename.sh file means ? ( the .sh extension)

i was building the Program called OpenEmbedded given by one of coursemates. 
I followed the instructions till i was told to enter "filename.sh" at the terminal 

but what i got was this error
> 
bash : ./filename.sh: Permission denied


what can possibly be the problem ? i've tried switching to root but the problem still persists. 
Anyone could shed some light please ? thanks !!

---

### Post by thelocust on 2007-04-24
the .sh is a shell file think of it as a .exe. I dont know what your problem is but try ```
sudo chmod u+x
```
check out [this]("http://en.wikipedia.org/wiki/Bourne_shell") for more info.

---

### Post by Ne0z on 2007-04-24
hi thelocust

i tried what u suggested but

i got this error

> chmod : missing operand after 'u+x'

thanks

---

### Post by thelocust on 2007-04-24
Sorry bro I was in a hurry. first you have to go to the directory were the file is at using command

```
cd /home/bob
```/home/bob is and example of a directory. the you use 

```
sudo chmod u+x filename.sh
```

---

### Post by Ne0z on 2007-04-24
thanks thelocust !!

it worked and its running now

but mind explaining what was these commands ? i'm still new to ubuntu , so wanna learn as much as possible :)

---

### Post by bukwirm on 2007-04-24
chmod is used to modify the permissions of files - read the man pages (ie, type "man chmod") for more details.
cd is used to change directories. (again, read the man page for more information)

You can find plenty of information on these topics by searching the web.

---

### Post by thelocust on 2007-04-25
[COLOR=Red]**cd**[/COLOR] stands for change directory i think and then you put the directory you want after that i.e. **[COLOR=Red]cd /home/bob/.mozilla/firefox[/COLOR]**

 [COLOR=Red]**cd .. **[/COLOR](dont forget the space between d and .) takes you up one directory so it would be **[COLOR=Red]/home/bob/.mozilla[/COLOR]** 

[COLOR=Red]** cd ~**[/COLOR] takes your home folder

[COLOR=Red]** sudo**[/COLOR] makes the following commands as root. **[COLOR=Red]sudo nautilus[/COLOR]** will open nautilus as root

[COLOR=Red]**chmod**[/COLOR] changes the perisions of the file i.e. who can access it and what it does.

the [COLOR=Red]**u**[/COLOR] stand for user the [COLOR=Red]**+**[/COLOR] stands for add and the**[COLOR=Red] x[/COLOR]** stands for execute. so you gave gave permisions to root and changed it to executible.

**[COLOR=Red]./ [/COLOR]**is like run

let me know if this doesnt make any since or you have any other questions. good luck. sorry my spelling sucks.

---

