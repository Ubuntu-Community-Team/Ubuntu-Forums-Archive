---
title: "oops... little help..."
date: 2007-09-25
forum: General Help
---

### Post by Chondro_Biak on 2007-09-25
If someone has a sec I need some help...

I hosed my computer over the weekend and don't know how to fix it... 

I got a new video card (which is working great) but I was trying to get the 1440x900 resolution to be set when I opened it and found out the file was owned by root... So I thought I would take a short cut and change my user profile to root in the users options... So I changed my directory from home/username to /root and changed my permissions from username to root... If you go into your user profiles you should be able to see what I mean if I said that wrong... Well that obviously didn't work so I logged out and was going to try login in as root and found out I can't log in at root except from the terminal... So I tried to log back in and it would not let me because of the setting I changed... I can get to the terminal, but I have no clue how to change these settings from the terminal (still learning to walk)... Any chance you have a few minutes to give me a play by play??? 

thanks

---

### Post by Linder on 2007-09-25
Can't walk you thru the problem, unfortunately. But WHEN someone does, here's an advice for you:

NEVER be root. And never even TRY to login as root. It's inherently dangerous :D If you want to edit a file AS root (since it's can't be edited by a user) simply type

```
gksudo gedit /etc/X11/xorg.conf
```

for instance, to edit xorg.conf as root. The gksudo is the graphical version of sudo. 

su generally means "switch user". And sudo means "switch user and do". It basically means that for ONE command, you become root and then yourself again. 

Did I make sense?

---

### Post by Chondro_Biak on 2007-09-25
Yup that makes sense... Now I just need to know how to change my settings back, so I can use my computer... lol 

thanks

---

### Post by anaconda on 2007-09-25
graphical root login is disabled by default. that is propably the reason why you can only login to text mode.

log in to text mode (as root). and make a new user and then give that new user sudo rights. then you will be able to login as this new user and correct the problem. (eg. enabling graphical root login, or changing things back the way they were.

to create a new user:
adduser newusername
(and answer the questions. eg. name, username password etc..)

to give that new user admin rights:
adduser newusername admin

and then reboot.

hmmm... just remembered that it MIGHT be possible to get to the GUI with just logging in as root and typing :
startx
I think this will go round the disabled graphical root login.. (you dont login, you are already lin and just start the X)

PS. if you really want to have the root as the default user. you should just have enabled root user and copied the files to roots home.

---

### Post by Chondro_Biak on 2007-09-25
Hello

I actually already tried to create a new account to fix the problem and even gave it sudo privileges, but it still didn't work...  It gives me the same error... I think when I create a new account it mirrors the settings of the original account, which are hosed... 

I tried the startx and it did not work... 

Any more ideas?

---

### Post by Chondro_Biak on 2007-09-25
Does anyone else have any ideas?

I need to change my directory to /home/username and change my permissions to username from the terminal...

If you go to your profile there is two tabs... I changes my setting that said /home/username to /root and I believe on the other tab you have the option of permissions and it was set to my username and I scrolled up to root... 

Does anyone know how to change that from the terminal?

thanks

---

### Post by r4ik on 2007-09-25
This might be of some help although i am not to sure about it,

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_set.2Fchange.2Fenable_root_user_password](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_set.2Fchange.2Fenable_root_user_password)

Good luck !

---

### Post by PmDematagoda on 2007-09-25
What are the errors you get when trying to startx? I believe you should be able to get back to the terminal in recovery mode after an unsuccessful "startx" by pressing ALT+F2. When you get back to the terminal, post the errors you get as shown on your terminal.

---

