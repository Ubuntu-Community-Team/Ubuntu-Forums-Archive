---
title: "Ubuntu 13.04, Gksu/Gedit command error"
date: 2013-07-19
forum: General Help
---

### Post by dccmgb on 2013-07-19
I am trying to execute the following command within Ubuntu 13.04 so to eventually install a Realtek driver rtl8192cu; "gksu gedit /etc/modprobe.d/blacklist.conf".  Once I key in the command, a separate password screen appears to which I key in my admin password (the same one as the initial logon password) but it comes back flagged as invalid.  I have double checked that I am keying in the correct password but it is flagged invalid.  Any suggestions would be appreciated.

---

### Post by mc4man on 2013-07-19
in a terminal go 
```
 gksu-properties
```

Change the authentication mode to sudo as in screen

---

### Post by dccmgb on 2013-08-06
When I keyed in "gksu-properties" command I was then presented with the same pop-up screen asking for my administrative password, which when keyed in came back as invalid.  I assume that my administrative password is the same one that I key in for the initial Ubuntu login screen.  If yes, I don't know why it is coming back as invalid (I never had this issue with 12.10).  Any other suggestions?

---

### Post by sioxs on 2013-08-06
Sounds to me like permission problems?
Are you on the sudoers list?
$ sudo cat /etc/sudoers
you should see your username in the list or a line that permits users within the group of sudoers
In which case you could do: $ groupadd -f sudo
Or open users & groups UI and make sure your in the sudo group. 
Or perhaps you need your root password? You might have created this when you installed Ubuntu 
Although in order to preform such a task you need root access first.
Kinda like the chicken and the egg. But it is possible...

PS. when I do $ gksu-properties
a small UI window opens
 "privilege granting preferences"
Behaviour:
Authentication Mode: 'su'

Screen Grabbing:
Grab Mode: 'enabled'

 Peace!

---

### Post by deadflowr on 2013-08-06
If you're getting a password authentication screen when entering the gksu-properties screen , then I would suggest making sure there are no spaces in the phrase.
If it said gksu -properties, then the program will think that you'd need to run whatever command comes after as root and ask for permission.

---

### Post by dccmgb on 2013-08-11
Problem solved.  I first had to do the following from Recovery Mode, then selecting "Root" from the menu, and then the following to create a new root account password;

mount -rw -o remount /

sudo passwd root

I thought this was done already when downloading/setting up 13.04 (I did not have to do this in 12.10) but apparently not.  Thanks for your help. dc

---

### Post by oldos2er on 2013-08-11
If your issue is resolved can you please mark the thread as 'Solved' (under Thread Tools)? Thanks.

---

