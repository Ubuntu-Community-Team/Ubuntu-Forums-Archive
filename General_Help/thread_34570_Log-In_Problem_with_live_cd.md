---
title: "Log-In Problem with live cd"
date: 2005-05-15
forum: General Help
---

### Post by gm100 on 2005-05-15
If i go to the Ubuntu's login page first time, it asked me username and password. But i dont know them, where I should get them?

Root and root; Demo and demo.. They just doesn't work...

I really don't know what i should to do, i have used GOOGLE search, but i cant find nothing... ](*,)

---

### Post by ipixel on 2005-05-16
The username seems to be "ubuntu" - but I don't know what the password is. Perhaps someone else could help?

I wanted to be able to log-out and log-in using the LiveCD - in order to test changing some session settings - and came across the same problem (ie., could not log back in again without having to restart the machine)...

---

### Post by fairx on 2005-05-16
me too.. I need to reinstall grub and grub command won't load.

#sudo -s

gave me access as root@ubuntu but still cannot do grub command

please help.

---

### Post by scott.medling on 2005-06-03
I know this was posted a couple of weeks ago but had an issue with not knowing the username and password for the livecd.  I was able to figure out that the username was ubuntu, but I couldn't figure out the password (to log into kde).  With some help from random places I was able to figure out to Ctrl-Alt-1 to a logged in terminal where you can sudo passwd ubuntu to change the password to something that you know without needing to input the current (unknown) password.

If someone knows what the default password is, I am kind of curious.

---

### Post by scott.medling on 2005-06-03
For whatever reason it hadn't auto logged in the first time (probably because it crashed when I was eventually able to try with a correct password) and since it was my first time with the liveCD I didn't really know what was going on.

---

### Post by millerlite86 on 2005-06-06
I am not sure what the password is for the default "ubuntu" username, but a way around this is to:

1. Load Live CD
2. Arrive at loaded desktop
3. From the Menu "System" --> "Administration" --> "Users and Groups"
4. Click on user "ubuntu"
5. Select "Properties"
6. Under the "Password Section" "Set Password by Hand" should be checked
7. Delete the *'s in box 1 and enter a password, eg. hello
8, Delete the *'s in box 2 and rekey the same password as in box 1
9. Click "Ok"

Your Live CD will now have this new password saved for the "ubuntu" login for this Live CD session.  (When you boot Live CD again later this change will not be saved.)

You can now log on with user "ubuntu"!!

Hope that helps!

---

### Post by johl on 2008-03-23
Hi all,

I had the same problem and googled into this thread. Here I found the information that the default user is ubuntu so I just took a stab in the dark that the password may be blank and left the password-field empty. And it worked!

Thanks for doing the hard work, I just thought I'd contribute my lucky guess back.
/J

---

