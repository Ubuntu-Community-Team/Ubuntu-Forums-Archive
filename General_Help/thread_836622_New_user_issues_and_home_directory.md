---
title: "New user issues and home directory"
date: 2008-06-21
forum: General Help
---

### Post by Kleppemeister on 2008-06-21
Somehow I managed to screw up my main users home directory, or that is, i managed to change it, to somewhere there is no directory, and now I is impossible to log in with that user(or any other users, since I dont have one)
I search google and the forums here for an answer, but I found non, so I tryed to created a new user via the terminal, using adduser NAME and added a password to the account, so I went back to the X login screen, and tryed to log in, I got up a box, that said: New user added. And after that, the screen went all white one me, I can see and move my mouse around, but thats it, no menus, no right click dropdown menu, nothing at all but a white screem, and a mouse that I can move around.

So the question I got is, Is there a way to change what a users home directory is via the terminal? 
Or.... what is the problem with the new account I created? 
I would prefer if there was a way to change home directory via terminal 

Thank for you help in advance :)

---

### Post by unutbu on 2008-06-21
Please give us some more background information.
How was the original user account messed up?
Also post

```
cd /home
ls -l
```

What is the name of your original user account, and what is the name of your new user account?

Next, when you go to the gdm login screen, press F10 and select GNOME (or KDE) as the type of session you want. Then try logging in as the new user. Do you still get the white screen? 

If so, press Ctrl-Alt-F2 to get to a text terminal. Then type (and post)

```
cat ~/.xsession-errors
cd 
ls -la

```
I hope the last command isn't too prying -- edit it if you wish. It would just be helpful to see if the normal user account files are present.

---

### Post by Kleppemeister on 2008-06-21
Thanks,

For the first commands you asked me to do, I get:

```
drwr-xr-x 22 kleppe kleppe 4096 2008-06-21 22:58 kleppe
drwr-xr-x 22 stian stian 4096 2008-06-21 00:34 stian
```

I have to type it, since Im using my laptop now, since I cant use my desktop(The one that dosent work, and I only got Ubuntu on it)

For the 2nd command... My keyboard get put back to english setup in terminal, so I cant find the keys to use, so I dont get to use that one. THe key that I cant find is, ~, that one.
The account isent really broken I guess, its just then when I try to boot with it, I cant, becouse my I tryed to change my home directory, but I forgot to delete the old path, so it's stuck with two paths in a way, so it looks something like this```
/stian/home /media/disk/temp
```
So it have two paths, and that makes it say that it cant find path to home directory when I try to log in. 

So if there is any command to just change that path to what it should be, that would be most helpfull


Oh, and yeah, the one that is broken is stian, the new account is kleppe, and I am still getting a white screen.

---

### Post by unutbu on 2008-06-21
> **Kleppemeister said:**
> 
I forgot to delete the old path, so it's stuck with two paths in a way, so it looks something like this```
/stian/home /media/disk/temp
```

I don't understand. Where does it say 
```
/stian/home /media/disk/temp
```
?

---

### Post by Kleppemeister on 2008-06-21
> **unutbu said:**
> I don't understand. Where does it say 
```
/stian/home /media/disk/temp
```
?


THats the path to my home directory :S And ti pops up in a message box when I attempt to log in with the account, and says it cant find it, and that true, because there is no such path on my computer. 

It should be ```
/home/stian
```

But I managed to screw that completely up... so now it wount log me in. So what I need to do, is change it back to /home/stian . All the files are there, the directory is still intact with all the content it in, but I managed to change the path in the GUI User menu to that wierd thing I did. 
So if there is anyway to change the home directory to an account via the terminal, that would solve the issue.

or I hope atleast it will.

---

### Post by unutbu on 2008-06-21
Edited 2008-09-01: WARNING: It is very hazardous to change the path of your home account. Your home account is filled with configuration files that make reference to /home/olduser. If you change the path to your home account to /home/newuser, the configuration files will still make reference to /home/olduser, and subsequently a lot of applications will start acting weird because the configuration file is broken.

I think this should work.
```
sudo usermod --home /home/stian stian
```

If it doesn't, run the command
```
grep stian /etc/passwd
```
and post the result.

---

### Post by Kleppemeister on 2008-06-22
Ok, so that removed the boxs with the error when I logged in. But.. now I got a white screen with stian to.

I tryed the grep stian /etc/passwd command and i got this: 
```
stian:x:1000:stian,,,,:/home/stian:/bin/bash
```

The screen is just white, I got the bar at the top for a second or 2, before it just whited out on me. 
But atleast now my home directory is right.

---

### Post by unutbu on 2008-06-22
Try 

```
sudo apt-get install ubuntu-desktop
```

---

### Post by Kleppemeister on 2008-06-22
I got:
Blah blah, is already at newest version.
0 upgrade 0 newly installed, 0 to remove and 1  not upgrade

---

### Post by Kleppemeister on 2008-06-22
I am sorry, but I installed Windows Vista again, and going to use Wubi again to install a new ubuntu. For the year I've used Ubuntu now, I only had troubles, but I am not ready to give up yet. Atleast my ATI Radeon 1950 Pro card is working now, something I tryed for 6 months :)

Thank you for your effort tho

---

