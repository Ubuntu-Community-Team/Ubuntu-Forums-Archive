---
title: "No Admin Privaledges - Main Account deleted in Error"
date: 2006-10-10
forum: General Help
---

### Post by foskaomega on 2006-10-10
Hi all,
I did something really stupid :(  and I hope there is a way to undo it. In trying to move a directory from one home directory to another (main a/c) , I used the rm command and ended up trashing both directories. When I tried to login with the main user account, I get the $HOME.drc something discarded. I recreated the user's home directrory and set 777 permisions to it. I logged in again with the main user and still got the error. Silly me I deleted the main userid and recreated it but now the prermissions are lost. I enabled the root a/c and I still have root access thru the terminal. Can I restore that main user account (UID 1000)? Or if not, how can I creat a new user with admin privaledges. I tried useradd test -g sudo but it didnt work.

Any help will be greatly appreciated,

Rgds,

---

### Post by kiddo on 2006-10-10
I thought the group had to be "admin", not "sudo" ? Try removing the user, then removing its home directory, then useradd test -g admin. 

man useradd tells me that you can specify the userID like this:
useradd test -g admin -u 1000

Your question is a bit foggy though, I have problems understanding what exactly is your problem.

* no admin user available at all? (does not make sense since you are using useradd already)
* lost the data? (well this is most likely without an immediate solution)
* just can't login properly in the GRAPHICAL interface with that user? 

What is a/c? Account?

---

### Post by foskaomega on 2006-10-10
I created another account that should have admin privaledges BEFORE I deleted the original main user, but after I deleted the main user and restarted, The new admin user did not have admin privaledges (maybe I didnt click OK twice when I checked off "perform Administrative duties".

I am going to try that when I get home, I'll let u know how it works out,

Thanks

---

### Post by aysiu on 2006-10-10
Try this:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by foskaomega on 2006-10-11
Thanks a lot guys - I ran the command to create the user with ID 1000 and into admin group and it went in fine! I am at work now so when I get home to see if the newly created user has admin privaledges and let you know.

---

### Post by ayoli on 2006-10-11
about the $HOME/.dmrc error, chmod your homedir to 775 ,not 777. your homedir is not supposed to be writeable by other users.

---

### Post by foskaomega on 2006-10-12
I deleted the main account and recreated it now with the syntax: useradd %user_name% -g admin -d /home/%user_name% - u 1000. When I logged on with this new account, I got a series of errors and nothing worked. I restarted the box and tried logging in again but this new user does not have admin access (ie to the users and groups and full administration menu). I also notice that my sound card doesnt work (doesnt show up) with this user profile. Is there anything I can do to get sound working again in this profile?

---

### Post by mitch.c on 2006-10-12
> **foskaomega said:**
> I deleted the main account and recreated it now with the syntax: useradd %user_name% -g admin -d /home/%user_name% - u 1000. When I logged on with this new account, I got a series of errors and nothing worked. I restarted the box and tried logging in again but this new user does not have admin access (ie to the users and groups and full administration menu). I also notice that my sound card doesnt work (doesnt show up) with this user profile. Is there anything I can do to get sound working again in this profile?
I'm sure you need to be a member of audio, as well as a handful of other groups. If this help, here's the groups my user account belongs to (standard Dapper 6.06 install):
```
adm dialout cdrom floppy audio dip video plugdev users lpadmin scanner admin
```

---

### Post by foskaomega on 2006-10-12
Thanks for this info Mitch - I am sure this will help a lot! I will try again tonight when I get home to see if this works! I'll let you guys know later tonight when I get home from work.

Rgds,

---

### Post by foskaomega on 2006-10-13
PERFECT!!!!
Thanks guys, this worked perfectly!!:)  I recreated the main user with this syntax:
useradd %user_name% -G adm,admin,audio,sudo,lpadmin,scanner -u 1000 -d /home/%user_name%
Then I restarted the PC and logged in as another user and used sudo to chown the home directory back to the main user.
Now my main user has full privaledges again and audio is OK.

Thanks a million guys! Ubuntu really ROXX!!!:cool:

---

