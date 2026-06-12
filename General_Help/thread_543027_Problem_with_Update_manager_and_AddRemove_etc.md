---
title: "Problem with Update manager and Add/Remove etc"
date: 2007-09-04
forum: General Help
---

### Post by puke929 on 2007-09-04
I seem to have a problem that comes up with Add/Remove Programs and Update Manager. When i try to do either, it comes up with something about 'dpkg -- configure -a' and some other stuff.

Here is a screenshot - [http://img205.imageshack.us/img205/6942/screenshotec7.png](http://img205.imageshack.us/img205/6942/screenshotec7.png)

It is really confusing me and is getting to be a pain not being able to download new programs been as tho i have just started.

But . .i belive it may be becouse i closed update manager half way through uploading but i have no idea of how to solve it.. 

all help would be grateful.

Cheers,
Luke:confused:

---

### Post by sumguy231 on 2007-09-04
Open a terminal and run 'sudo dpkg --configure -a'.

---

### Post by puke929 on 2007-09-05
sorry im a bit of a noob at this stuff.. where will i find a terminal?

---

### Post by puke929 on 2007-09-05
sorry yes i found the terminal and i enterd 'sudo dpkg --configure -a'  then i enter my pass.. i then get to a list of options.. what do i pick to get that error to stop appearing and be nice and normal?

---

### Post by sumguy231 on 2007-09-05
Make sure you're enterng it exactly as shown without the quotation marks. Could you copy and paste the exact output you're getting?

---

### Post by Seisen on 2007-09-05
Sounds like you entered it with the quotation marks copy and paste this

```
sudo dpkg --configure -a
```

---

### Post by puke929 on 2007-09-06
ah.. gotr it right before you two posted.. its all good i thought i would do it one more time the other day amd compied what was on the webpage becouse i cba to type it and it worked.. cheers guys.. 

and also does anyone know of a good HTML editor like dreamweaver that i can get fof Ubuntu/linux because im failing at finding one anywhere.. and it would be good if i didnt have to use wine becouse atm i cba to set it up and use it for now. . unless i get desprate ...

---

