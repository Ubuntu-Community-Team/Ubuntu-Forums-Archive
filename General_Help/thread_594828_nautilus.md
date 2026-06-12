---
title: "nautilus"
date: 2007-10-28
forum: General Help
---

### Post by kotak07 on 2007-10-28
cannot open display: 
Run 'nautilus --help' to see a full list of available command line options.


Thats my problem when i run nautilus in terminal. i want to put a mozilla profile with my passwords and bookmarks and everything to the firefox profile in ubuntu. need help. thanks. kotak.

---

### Post by Wiebelhaus on 2007-10-28
I ran into this with a failing hard drive , Sorry mate that's all I can add.

---

### Post by kotak07 on 2007-10-28
i doubt that my harddrive is failing cuz its only about 2 years old. But if it is. how would i find out. and anyone have any other suggestions to this problem?

---

### Post by nick_h on 2007-10-28
I'm not an expert on this, but what do you get if you type:
```
echo $DISPLAY
```
?

---

### Post by kotak07 on 2007-10-28
if i type it in as normal user i get this

```
neal@Neals-Laptop:~$ echo $DISPLAY
:0.0

```

if i type it in as root i get this.

```
root@Neals-Laptop:~# echo $DISPLAY


```

thats supposed to be a blank line underneath root btw.

---

### Post by nick_h on 2007-10-28
Does nautilus work as a normal user and not as root?

If so you can specify the display with the --display=:0.0 option.

---

### Post by kotak07 on 2007-10-28
no nautilus doesnt display anything in both normal user or root. all i want to do is put the file with all the passwords for mozilla firefox into the profile for firefox in ubuntu. but i need to be root to do that. if i could log in as root then i would do it but idk the login or the password. but yeah nautilus doesnt work either way.

btw is anyone knows the file that holds the passwords..can you please specify that file? thanks

---

### Post by kotak07 on 2007-10-29
i tried looking around for possible solutions but i didnt find any or none of them were clear to me on how to fix the problem so again if anyone has any suggestions please do tell. oh and btw this happened in feisty fawn and i just upgraded to 7.10 so yeah its still happening

---

### Post by nick_h on 2007-10-29
Firefox stores data in profiles which are under the directory ~/.mozilla/firefox - they will have names like xxxxxx.default.

I suggest that you either copy the directory from the command line without using nautilus or run nautilus from the GUI and install the nautilus-gksu package.

---

### Post by kotak07 on 2007-10-29
can you please assist me in how i should go upon doing that?

---

### Post by nick_h on 2007-10-29
Where are you copying from?  Is it another Linux installation?

To copy a directory and its contents you will need to use the cp command (copy) with the -R option (recursive).

Something like:
```
sudo cp -R /media/sda2/home/user/.mozilla/firefox/xxxxx.default ~/.mozilla/firefox/xxxxx.default
```

---

### Post by kotak07 on 2007-10-30
i am copying the profile from my external hdd and btw i should mention that now the gedit display wont come up when i wanna change my dhcp

---

### Post by nick_h on 2007-10-30
It seems to me that you need to sort out your display problem anyway.

Just to clarify a few things -

Do you have a working GUI?
Do nautilus and gedit work OK when invoked from the GUI?
When you start the program are you doing so from a terminal window in the GUI or from a VT?
You have tried the --display=:0.0 option and it doesn't work?

---

### Post by kotak07 on 2007-10-30
gui? do u mean like if i see the desktop. if in that case yeah. how do i invoke nautilus from the gui? cuz from terminal it doesnt work.

---

### Post by nick_h on 2007-10-30
Yes, under Places->Home, for example, does it start nautilus OK?

---

### Post by nick_h on 2007-10-30
Then open a terminal using Applications->Accessories->Terminal and type:
```
nautilus
```
From what you are saying this doesn't work?

---

### Post by kotak07 on 2007-10-30
ok yeah nautilus works in normal user. but i want to use it as root user so i can make changes and it doesnt work when using it in root user.

---

### Post by nick_h on 2007-10-30
Open a terminal using Applications->Accessories->Terminal and type:
```
gksudo nautilus
```
It is just this that doesn't work?

---

### Post by kotak07 on 2007-10-30
see now thats genius. it worked. even for gedit

---

### Post by nick_h on 2007-10-31
It's good that you got it working.  I assume you were starting it in a different way before.

You mat still find nautilus-gksu usful - it adds an "open as administrator" option when you right click on a file in nautilus.

You can install it with:
```
sudo apt-get install nautilus-gksu
```

---

