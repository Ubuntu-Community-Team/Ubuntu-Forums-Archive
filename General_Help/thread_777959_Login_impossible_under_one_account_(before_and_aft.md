---
title: "Login impossible under one account (before and after OS upgrade)"
date: 2008-05-01
forum: General Help
---

### Post by Niamh on 2008-05-01
I have two user accounts on my PC.  One of them (which I will call "B" for simplicity) is a sort of "contingency" account with few privileges, used only in dire situations that disable the main account (e.g. the current case).  The other is my "main" account (which I will call "A"), and is used daily.
This morning, I turned on my computer as always.  Everything seemed to load correctly, and I was greeted with the standard login screen.  I logged in as A, but I was promptly sent back to the login screen; I received the information that my login had lasted for less than 10 seconds, and that something was wrong.  I attempted then to login under the "failsafe" version of GNOME, and then the failsafe *terminal*, receiving the same error message each time.  Desperate, I tried logging in as B.  This worked absolutely perfectly, without any errors whatsoever.
I tried to switch users from B to A; this brought up the same error message as before, followed by a system crash (unfortunately, this effect prevents me from taking a screenshot of the message or quoting it correctly).  I restarted the computer and opened up GRUB, but my attempt to load a different version of Ubuntu was in vain, and had the same result as all my other attempts so far.
I logged in as B, then studied the system log.  I couldn't find anything out of the ordinary.  I tried upgrading to the latest version of Ubuntu, but that had no effect whatsoever.  I am at an utter loss.
The problem only seems to be affecting the A account, but I cannot access same to figure out what might be wrong, or to remedy the situation.  My B account has only limited abilities, and so I can't salvage many of A's files in the event that deleting A's account is the only solution (and some of the files would be impossible or very time-consuming to replace).
I know that not much can be done, but if anyone can provide me with even a little advice, it would be a great help indeed.  Thank you in advance, if applicable.  (If there is any relevant information I have left out, feel free to say so.)

---

### Post by joshsmith on 2008-05-01
im guessing you mean B isnt administrator
you could make a new user account as administrator in terminal, i checked the forums through google and found this command which might work
```

sudo useradd -G admin yourusername

```
if you select recovery mode at grub you could get the a superuser terminal to allow you to run that (although without the sudo bit)
then you could log in as the new adminstrator, and better work out what is going on, and do it in the gui

---

### Post by Monicker on 2008-05-01
You should be able to log in as root using Recovery Mode from the boot menu.  Once logged in you can view /var/log/messages and /var/log/auth.log to see if there is anything relevant about why the one account is not able to login properly.

Using the nano text editor will probably be the easiest way to look at the files.

```
nano /var/log/messages
nano /var/log/auth.log
```

You can search the files for occurrences of the account name which is having problems.

---

### Post by Niamh on 2008-05-01
> **Monicker said:**
> ...you can view /var/log/messages and /var/log/auth.log to see if there is anything relevant about why the one account is not able to login properly.

I attempted this, but couldn't find anything relevant...

At present, I'm burning a DVD of the files I could salvage from A, but I will try the "create admin account" plan after.  Thanks for the help.  ^_^

EDIT: OK, I *think* it's a problem with the "gnome-keyring-daemon".  I tried to login again this morning, and found a new nugget of interest in the logs.  Here they are:
(for security reasons, in this post, my account name has been replaced with curly brackets and the letter a, producing the string "{a}".)
```
May  2 14:37:54 niamh su[5902]: pam_unix(su:session): session opened for user clamav by (uid=0)
May  2 14:37:54 niamh su[5902]: pam_unix(su:session): session closed for user clamav
May  2 14:38:01 niamh gdm[6071]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  2 14:38:01 niamh gdm[6071]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  2 14:38:01 niamh gdm[6071]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  2 14:38:07 niamh gdm[6071]: pam_unix(gdm:session): session opened for user {a} by (uid=0)
May  2 14:38:07 niamh gdm[6273]: gkr-pam: couldn't run gnome-keyring-daemon: Permission denied
May  2 14:38:07 niamh gdm[6071]: gdm[6273]: gkr-pam: couldn't run gnome-keyring-daemon: Permission denied
May  2 14:38:07 niamh gdm[6071]: gkr-pam: gnome-keyring-daemon didn't start properly properly
May  2 14:38:32 niamh gdm[6071]: pam_unix(gdm:session): session closed for user {a}
```

EDIT2: After a bit of examination, I think the problem is this: for whatever reason, I do not possess a specific file called "pam_smbpass.so".  This file should be in "/lib/security/", but it is noticeably absent.  I did some digging as to what it is for, but can't find any info on what to do if one *lacks* this file, or how to re-construct it in the event that one needs it.  Any advice on how to acquire this file?

---

