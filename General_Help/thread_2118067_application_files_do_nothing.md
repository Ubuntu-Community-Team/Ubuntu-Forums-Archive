---
title: "application files do nothing"
date: 2013-02-20
forum: General Help
---

### Post by V Boti on 2013-02-20
after upgrading to 12.10, applications files do nothing, I have checked the "allow execyting as programs" but still nothing. only the installed apps works in the usr/bin.

---

### Post by kc1di on 2013-02-20
Hello V Boti and welcome to Ubuntu/xubuntu,

Could you give us a little more information about what applications your trying to run and where they are located?

We would be just guessing at this point what your talking about without further information.
So give us a little more to go on.

---

### Post by schragge on 2013-02-20
+1 to more information.

Only applications that are on your $PATH get executed without further ado. So while you're at it, please also run
```

echo $PATH

```
and post the output here

---

### Post by V Boti on 2013-02-20
I have downloaded apps like bluegriffon, Kompozer, these are not installable deb files I just unzipped them, these are in download folder. I also have a game named gridwars that does not need installation, it wrked before the upgrade now does nothing when I click the executable, no error message, no nothing


the $path returns:

boti@boti:~$ echo $PATH
/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games

---

### Post by kc1di on 2013-02-20
kompozer and Bluegriffon can simply be unzip /tarred and place in a folder and executed from their files. kompozer will be missing some dependancies in 12.10 and has not been updated in about 3 years. 
that's why it was dropped form 12.10 repositories. 

so simply unpack bluegriffon to a folder on home directory and exicute it from there.
when you get it working let me know and I will guide you through how to add it to your menu.

---

### Post by V Boti on 2013-02-20
this is exaclly what I have done, but when I doubleclic on the executable, nothing happens, not even an error message, nothing.

---

### Post by kc1di on 2013-02-20
> **V Boti said:**
> this is exaclly what I have done, but when I doubleclic on the executable, nothing happens, not even an error message, nothing.

go to a terminal and cd to the folder where bluegriffon is at.
and type in the command for the executable. list the error message you get in the terminal.. if I remember right there are some extra libraries you must install with it.  been a while since I did that.

---

