---
title: "can not login after new install"
date: 2006-07-01
forum: General Help
---

### Post by audio on 2006-07-01
iv used ubuntu before but moved away, i wanted to move back and am having issues. 

iv searched for this issue and nothing seems to help

im getting an incorrect username or password error. 

i couldnt solve this so i reinstalled being very carful with the user and password
all lower case and simple password so. 

i went in under recovery console. and when i tryand add the user i made during the install i get:

'the group audio already exists'

i saw one thing using the admin group but i was told there was no such group when trying to add the new user to this group. 

i added another user and i could log in, only problem i cant get into any admin options. 

i tryed adding this user to the audio group also just to see if i could the root but i still cant get in under audio. 

and when i use the new name still cant get into options like users. 

the sudo option will come up then after i enter the password i get another error. 


thanks in advanced. 

(sorry typing this on a mini-;aptop with 7" screen)

---

### Post by encompass on 2006-07-01
Nice lappy...
well, if your trying to make a user names audio that is bad.  if you are trying to add a user to the audio group shouldn't have to that is default.
If your trying to use root, there is no root on strait install of ubuntu administration is done with the sudo command and your first user.
If you want to make a user with admin you can do that with the gui... it is faster when you want to make alot of changes to the user. IMO that is found in system admin, users and groups then click on the user you want and properties, under the administration tab.
Hope this helps... I am trying here...

---

### Post by audio on 2006-07-01
ok so it might b the username i selected , as the only user that will log in is not admin and it also cant get into the users and groups. 

the root was making the user part of the root group
also i wanted to make it part of the sudo group

ill see if i can start the install with a new/diff username

in the terminal how to i make a user hav admin rights

---

### Post by audio on 2006-07-01
ok i reinstalled using the oem install

and it all ok now, can log in and start playing :D

---

### Post by encompass on 2006-07-03
good... yeah, it is good practice to use a username that is not common anyway for security reasons.  What would be the first set of usernames a hacker would try.  Administrator, Admin, God, that kinda stuff.

---

