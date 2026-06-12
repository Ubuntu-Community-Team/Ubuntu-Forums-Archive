---
title: "change user account icon"
date: 2013-08-06
forum: General Help
---

### Post by freddyfields on 2013-08-06
Hi all.  Been trying to figure out how to change the user account icon.  I wanted to change it to a costum picture when prompted to put in a password to login.  Tried a few times unsucessfully.  Anyone know how?

---

### Post by Cheesemill on 2013-08-06
Go to Settings > Users and click on the picture next to your name.

---

### Post by freddyfields on 2013-08-06
i go to system > users and groups and my name comes up with a silhouette and my name, but its not clickable.  theres an advanced options and add user, but it doesnt give any option to change the picture.  Maybe im lost or ubuntu studio doesnt have that option?

---

### Post by cub on 2013-08-08
Since Ubuntu Studio use Xfce just as Xubuntu I was under the impression that this (maybe not the most intuitive) process would work: [http://askubuntu.com/questions/47186/is-there-a-way-to-change-user-picture-in-xubuntu-and-actually-display-it-on-log](http://askubuntu.com/questions/47186/is-there-a-way-to-change-user-picture-in-xubuntu-and-actually-display-it-on-log)

However after several tries with 64x64, 96x72 or 96x96 either JPG or PNG I can't get anything to show on my Ubuntu Studio 13.04.

---

### Post by sudodus on 2013-08-08
Take the picture you like (at least jpg and png files work). Make it small (*Edit*: mine happens to be a transparent png file sized 121x150). Copy it to .face in your home directory (~/.face)

The system will recognize it as the user account icon next time you log in.

---

### Post by cub on 2013-08-08
> **sudodus said:**
> Take the picture you like (at least jpg and png files work). Make it small (*Edit*: mine happens to be a transparent png file sized 121x150). Copy it to .face in your home directory (~/.face)

The system will recognize it as the user account icon next time you log in.
Are you doing that on a Ubuntu Studio edition? Because I can't get it to work on US 13.04 at least.

---

### Post by sudodus on 2013-08-08
No, but it works with Xubuntu, Ubuntu and Linux Mint, and at least Ubuntu Studio 12.04 has the Xubuntu (XFCE) desktop environment, so I thought it should work. Did you log out and log in again (or reboot)? Are you running only Ubuntu Studio 13.04?

Are we talking about the same user logo, the one that shows in some log in screens and 'change user' menus?

---

### Post by sudodus on 2013-08-08
I just checked in Ubuntu 12.04 and Lubuntu 13.10 (Saucy alpha 2). It works with .face in the home directory. For example ***users-admin*** will use it.

---

### Post by grahammechanical on 2013-08-08
The technique of putting a .face image in the home folder will put that image alongside the user name in Users and Groups. To put it alongside the name at log in on Ubuntu Studio we need to go to Settings Manager>Session and Starup>General tab>Session chooser and tick the box Display Chooser on Login. And then log out and log in. I have just tested it on Ubuntu Studio Saucy Salamander.

Regards.

---

### Post by cub on 2013-08-08
> **sudodus said:**
> No, but it works with Xubuntu, Ubuntu and Linux Mint, and at least Ubuntu Studio 12.04 has the Xubuntu (XFCE) desktop environment, so I thought it should work. Did you log out and log in again (or reboot)? Are you running only Ubuntu Studio 13.04?

Are we talking about the same user logo, the one that shows in some log in screens and 'change user' menus?
I know. It *should* work since US use Xfce. And yes, I mean the same user logo.

I only have access to a US 13.04 machine at the moment but will check on 12.04 later on. I did log out/in and reboots as well during my tests.

Mind you, I'm not the OP just confused why it won't work on Ubuntu Studio since it should behave in the same way as Xubuntu.

---

### Post by sudodus on 2013-08-08
Thanks *grahammechanical*, that explaíns the problems!

It works in different ways in the different flavours. Lubuntu Saucy will carry it directly to the login screen (and replace the default symbol with the picture in .face. I noticed however, that it expands to square shape, so the .face file should be square too (otherwise it will be slightly distorted). My face is shown thicker than usual in the Lubuntu log in screen ;-)

---

### Post by cub on 2013-08-08
> **grahammechanical said:**
> The technique of putting a .face image in the home folder will put that image alongside the user name in Users and Groups. To put it alongside the name at log in on Ubuntu Studio we need to go to Settings Manager>Session and Starup>General tab>Session chooser and tick the box Display Chooser on Login. And then log out and log in. I have just tested it on Ubuntu Studio Saucy Salamander.

Regards.
Interesting! Could you give more details on the picture size and png/jpg? Also if the name of the file matters?

Because I followed your instructions on 12.04, 13.04 and 13.10 and still won't get any picture in Users and Groups or the Login.

---

### Post by cub on 2013-08-09
Right, I just ran the same test with Xubuntu 13.04 and still not working. Though it works for other people. Quite confusing as I can't see what I am doing wrong, if anything.

---

### Post by sudodus on 2013-08-09
Do you put a picture file renamed or copied to .face (dot-face) in the home directory? Nothing in front of the dot.

```

ls -l
-rw-r--r-- 1 sudodus sudodus 28801 jun 12  2010 .face

```

---

### Post by cub on 2013-08-09
Moahahaa no. All this time I have read it as to put a png or a jpg file in a ~/.face/, a directory. Not create the file ~/.face . Problem solved for me.

Still no word from the OP. Perhaps he/she wasn't as stupid as I ...

---

### Post by sudodus on 2013-08-09
The only stupid question is the one not asked ;-)

---

