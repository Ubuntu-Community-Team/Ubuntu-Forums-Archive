---
title: "linux - linux files exchange"
date: 2007-10-28
forum: General Help
---

### Post by le1 on 2007-10-28
hi everybody

I need some help. Before I start I need to say that i got rid of M$ and operate on two linux distros. Ubuntu & mandriva. I am a total beginner not know much about linux but speed and stability blew my mind and now I'm using linux only.

I used to have M$ only, then installed mandriva and on the top of it ubuntu. Later on got rid of M$ and feisty fawn & installed new ubuntu gutsy gibbon. When I still had M$ & wanted to copy some files between distros i just used ntfs on M$ as a middle man. Now mandriva doesn't see ubuntu but ubuntu sees mandriva. I got some files on mandriva desktop but get "The folder contents could not be displayed.You do not have the permissions necessary to view the contents of user" when i want to access it (need these files on ubuntu). I also made 20 GB partition (ext3) and like to use it as a inter exchange partition between my two distros (only ubuntu sees it). I hope you get the picture. How one would go about with it?

---

### Post by taurus on 2007-10-28
Where is that directory when you got that error message, "The folder contents could not be displayed.You do not have the permissions necessary to view the contents of user"?  Probably just a wrong permissions between Mandy and Ubuntu.

---

### Post by le1 on 2007-10-28
madrivia/home when i click on "user" i get that note. 
Flies that i want to access are on desktop in mandriva.

---

### Post by taurus on 2007-10-28
Where do you mount Mandy's partition?  For now, I would assume it's in /media/mandrivia so what's the output of this command from a terminal?

```
ls -la /media/mandrivia/home
```

---

### Post by le1 on 2007-10-28
total 12
drwxr-xr-x  3 root root 4096 date
drwxr-xr-x 22 root adm  4096 date
lrwxrwxrwx  1 root root    8 date guest -> /home/me
drwx--x--x 25  500  500 4096 date me

---

### Post by taurus on 2007-10-28
> **le1 said:**
> total 12
drwxr-xr-x  3 root root 4096 date
drwxr-xr-x 22 root adm  4096 date
lrwxrwxrwx  1 root root    8 date guest -> /home/me
drwx--x--x 25  500  500 4096 date me

Which directory do you want to have access to, "date me" (I am NOT even going to ask why that name)?

Try changing the permissions so you can access it.

```
sudo chmod -R 777 "/media/mandrivia/home/date me"
ls -la /media/mandrivia/home
```

---

### Post by le1 on 2007-10-28
I laughed for few minutes :)

total 12
drwxr-xr-x  3 root root 4096 2007-10-17 11:23 .
drwxr-xr-x 22 root adm  4096 2007-10-28 12:49 ..
lrwxrwxrwx  1 root root    8 2007-10-17 11:22 guest -> /home/me
drwx--x--x 25  500  500 4096 2007-10-28 12:49 me

---

### Post by taurus on 2007-10-28
> **le1 said:**
> I laughed for few minutes :)

Glad you have a good time.

> total 12
drwxr-xr-x  3 root root 4096 2007-10-17 11:23 .
drwxr-xr-x 22 root adm  4096 2007-10-28 12:49 ..
lrwxrwxrwx  1 root root    8 2007-10-17 11:22 guest -> /home/me
drwx--x--x 25  500  500 4096 2007-10-28 12:49 me

Is that the output of 

```
ls -la /media/mandrivia/home
```
How come it doesn't look like the previous output?

```

drwxr-xr-x 3 root root 4096 date
drwxr-xr-x 22 root adm 4096 date
lrwxrwxrwx 1 root root 8 date guest -> /home/me
drwx--x--x 25 500 500 4096 date me

```

---

### Post by le1 on 2007-10-28
I thought that date was irrelevant so I put word "date" instead of date.

But I think you also skipped one phrase from my first post "I am a total beginner"

I really don't know what I should do.

---

