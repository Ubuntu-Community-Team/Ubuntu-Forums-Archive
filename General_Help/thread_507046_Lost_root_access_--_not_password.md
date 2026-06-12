---
title: "Lost root access -- not password"
date: 2007-07-22
forum: General Help
---

### Post by Nossie on 2007-07-22
Hi,  

not sure what happened but I can no longer use sudo, admin functions from the menu or anything like that...

I have my root password, it seems to be accepting it but then not doing what its asked.

The problem started when I tried to fix my pidgin away status bug by downloading the right modules etc... I tried to apt-get and was told I wasnt root and my actions would be reported...  I then tried again and the command seemed to work but nothing happened


```
ian@Jupiter-ubuntu:~$ sudo apt-get install pidgin
ian@Jupiter-ubuntu:~$ sudo apt-get remove pidgin
ian@Jupiter-ubuntu:~$ sudo apt-get shoot  pidgin
ian@Jupiter-ubuntu:~$ sudo apt-get setcaton pidgin

```


Now I have no errors... and only 8 things show up in admin, one that does is update manger, when I try to run that, it failed to run as root then completed saying no updates found.... now it just completes with no updates or errors.

any help would be greatly appreciated, ty
Ian.

---

### Post by Nossie on 2007-07-22
I did try to login on an alt account that has no true root access...

all the admin menu displays but obviously wont allow me to enter my root password

---

### Post by Nossie on 2007-07-22
is there an easy way from recovery mode to give my other standard account root access and then check what went wrong with my main account?

I do have the right root password...

---

### Post by Nossie on 2007-07-22
fixed with 

```
adduser <name> admin
```

in recovery mode...

strange thing is, when I went to add it to my alt account it already had root... but my main account worked fine,

any ideas? think its fixed now tho :guitar:

---

### Post by PhilB on 2007-07-25
Cant offer any ideas myself, but I am currently experiencing the same problem-as far as I know everything was ok a couple of days ago, but yesterday I received an update notification which would not install. Today I realized Ive lost root and cant do any admin stuff at all.
Can only assume for now that the most recent (successful) update corrupted something. Will have to wait til the weekend to look into it.
Phil

---

