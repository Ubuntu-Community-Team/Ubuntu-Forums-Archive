---
title: "Getting to the Root Account"
date: 2006-12-26
forum: General Help
---

### Post by pmcastillo on 2006-12-26
I'm trying to configure GRUB, but it keeps telling me that I am not the owner of the file - root is the owner of the file. I am usually logged in as "ubuntu" as the login name and "123" as my password. I tried logging in using "root" as log-in name and nothing in the password, but it won't let me in.

---

### Post by Sef on 2006-12-26
Have you tried root as the password as well?

---

### Post by jincast90 on 2006-12-26
Can't you use the sudo command?

---

### Post by pmcastillo on 2006-12-26
Ummmm... I'm very new to this Ubuntu Stuffs...

>  Have you tried root as the password as well? 

The "root" as password and "root" as username didn't work.

>  Can't you use the sudo command? 

Ummmm... the sudo command is working, but... could you enlighten me how to use it? And to configure the GRUB.

Is there a site that could teach me Ubuntu command lines?

---

### Post by Sef on 2006-12-26
> Ummmm... the sudo command is working, but... could you enlighten me how to use it? And to configure the GRUB.


Sudo is a temporary root.  It is open for 15 minutes.

> Is there a site that could teach me Ubuntu command lines?

What exactly would you want to do?  There a lot of tuturials on the command line.

---

### Post by jincast90 on 2006-12-26
What do you want to configure in grub? Boot order? Boot times or? If you tell us, I am sure that we can help you.

---

### Post by pmcastillo on 2006-12-26
> What exactly would you want to do? There a lot of tuturials on the command line.

Ummmm... Here's what I need to do:

1.) Go to the /boot/grub directory (in MSDOS, its much like: cd\boot\grub)

2.) Edit that menu.lst so it will run WinXP by default and a 3secs timeout. (in MSDOS, its much like: edit menu.lst)

3.) And then give myself a round-of-applause and a bottle of champagne, for fixin this prob. :-D

---

### Post by jincast90 on 2006-12-26
> **pmcastillo said:**
> Ummmm... Here's what I need to do:

1.) Go to the /boot/grub directory (in MSDOS, its much like: cd\boot\grub)

2.) Edit that menu.lst so it will run WinXP by default and a 3secs timeout. (in MSDOS, its much like: edit menu.lst)

3.) And then give myself a round-of-applause and a bottle of champagne, for fixin this prob. :-D

First thing you need to do is make a backup copy of the file located at :/boot/grub/menu.lst.
Afterwards you open up your terminal and type:

sudo gedit /boot/grub/menu.lst

Then you click the find button and write:

timeout

There should be a line in the document saying:

timeout		10

This 10 should be changed to 3, and then next time grub will automaticly choose your os i 3 secs.

Remember to backup the file before modifying it.

I will post how to change the boot order a little later unless someone has posted howto by that time.

---

### Post by 23meg on 2006-12-26
[QUOTE=jincast90]Afterwards you open up your terminal and type:

sudo gedit /boot/grub/menu.lst[/QUOTE]For graphical apps such as gedit you should use *gksudo* instead of *sudo*.```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by jincast90 on 2006-12-26
> **23meg said:**
> For graphical apps such as gedit you should use *gksudo* instead of *sudo*

Really? I did not know that.. Why is this the case?

---

### Post by 23meg on 2006-12-26
> **jincast90 said:**
> Really? I did not know that.. Why is this the case?
See [this thread]("http://www.ubuntuforums.org/showthread.php?t=165957").

---

### Post by pmcastillo on 2006-12-26
Ahhhhh.... so it may:

1. There are other times, though, when side effects can be as mild as Firefox extensions not sticking or as extreme as as not being able to log in any more because the permissions on your .ICEauthority changed.

2. Running graphical applications with sudo also has the downside of always having to be run from the terminal.

3. There are also some graphical applications that simply will not run with the sudo command.

---

