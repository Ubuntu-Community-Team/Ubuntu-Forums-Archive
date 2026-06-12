---
title: "Wine problems"
date: 2005-10-29
forum: General Help
---

### Post by not_cool on 2005-10-29
Problem One:

I installed wine and got Starcraft and Lords of Magic: SE to install. When I try to run them it says that the cd isn't in the drive and to check and retry. But the cd is in the drive. How do i get wine to recognize the drive? (I've tried autodetect but that didn't help)

Problem Two:

I am trying to install SmartMusic [http://www.smartmusic.com](http://www.smartmusic.com) but so far have had no luck.

```
markus@ubuntu:~$ wine /home/markus/Downloads/InstallSmartMusic8-5Win.exe
markus@ubuntu:~$ wine '/home/markus/.wine/drive_c/Program Files/SmartMusic8.5Win/SETUP.exe '

```

(I have also tried installing from a CD, but you don't need it to run the program)

After running SETUP.exe, SM says it is begining setup. After it finishes begining setup, I get an error message saying "Setup was unsucsesful."

Any ideas?

---

### Post by dhess31 on 2005-10-29
If I remember correctly, there are issues with WINE (well, at least their used to be) and games that use cd-based copy protection.  You might give Cadega a try, as they have code that fixes this in most cases.

Don

---

### Post by ofek on 2005-10-29
About the starcraft problem u should go and have a look at [http://frankscorner.org/]("http://frankscorner.org/").
and remember wine isn't perfect and won't get all windows apps/games to work just some of em.

---

### Post by The Headhunter on 2005-10-29
ok.

Type in winecfg in the terminal window.

Click on "Drives".

Autodetect didn't work for me either so I clicked on "Add" and a new drive of a new letter will appear.  The path for your cdrom should be /media/cdrom0, so type that in under path and for type, choose "CD-ROM".

---

### Post by not_cool on 2005-10-29
Thanks for the help with the games, I'm going to try out Cadega now. But do you have any ideas with my SmartMusic problem? And I know Wine isn't perfect. (It just entered beta!)

---

### Post by dhess31 on 2005-10-29
Sorry.  I've never tried smartmusic so I can't help you out there.

Don

---

### Post by moffa on 2005-10-30
btw its cedega, and you have to pay $5 a month for it I think.

The website is: [http://www.transgaming.com/](http://www.transgaming.com/) and version 5 is coming out soon, so you might want to wait for that if the current version doesn't help

---

### Post by dhess31 on 2005-10-30
[QUOTE=moffa]btw its cedega, and you have to pay $5 a month for it I think.

The website is: [http://www.transgaming.com/](http://www.transgaming.com/) and version 5 is coming out soon, so you might want to wait for that if the current version doesn't help[/QUOTE]

You can get versions of it for free from their CVS, but I'm not sure if it is crippled or not.

Don

---

### Post by not_cool on 2005-10-30
I don't want to pay the $5 a month so I tried out the CVS version, but had trouble. And yes, it is crippled, it doesn't allow you to play without a CD. Do you know how to use a no-cd crack with games on wine?

---

