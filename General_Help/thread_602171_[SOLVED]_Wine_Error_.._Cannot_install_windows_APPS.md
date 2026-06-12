---
title: "[SOLVED] Wine Error .. Cannot install windows APPS"
date: 2007-11-04
forum: General Help
---

### Post by bhencetotozo on 2007-11-04
I have ubunto 7.10 .. i downloaded WINE from add and remove ... it worked..

I tryed to install AIM and Internex explorer 7 .. it didnt work...

i remember it saying CANNOT FIND A VOLUME FOR FILE TO BE EXTRACTED TO  or something..

I think the .exe file is looking for a C: drive... but theres none..

im running linux on a dedicated  320 GB harddrive NO other drives are attached while linux is running ...

i was going to do a partition mod and try to add a fat32 partition on the drive to see but.. im too affraid imma **** up linux...

anyways .

what do i have to do? Thank you

---

### Post by PmDematagoda on 2007-11-04
Make sure you have Wine installed by entering this command in a terminal:-

```
sudo apt-get install wine
```

after that is completed do:-

```
winecfg 

```
in the terminal, after you do the necessary configurations try installing the apps again.

---

### Post by chrishere01 on 2007-11-04
oh yeah i had the same problem

i just used pidgen for the aim

but internet explorer i found something on the internet
ummmm
yeah  for that make sure you have your gecko installed and if its a .exe 
some .msi and etc. wont work

---

### Post by bhencetotozo on 2007-11-04
I configured but still havent been able to do it.. its trying to extract the files somewhere but prolly not findint a compatible partition ...

HELP pleaseeee...

---

### Post by bhencetotozo on 2007-11-04
Did Not Work

---

### Post by PmDematagoda on 2007-11-04
Download the Wine-doors .deb from here:-

[http://www.wine-doors.org/wordpress/?page_id=3](http://www.wine-doors.org/wordpress/?page_id=3)

install it and try and see if you can use it to install your application.

---

### Post by bhencetotozo on 2007-11-05
thank you IT WORKED... NOW WHICH VERSION OF MSN IS COMPATIBLE WITH WINE?

I COULDNT MAKE aim 6 WORK.. I HAD TO DOWNLOAD THE 4.7 VERSION .

SORRI ABOUT CAPS BUT MY WORK KEYBOARD IS BROKEN.

---

### Post by PmDematagoda on 2007-11-05
Sorry about your keyboard:), but why don't you give AMSN a try? It can be installed using:-
```

sudo apt-get install amsn

```

---

