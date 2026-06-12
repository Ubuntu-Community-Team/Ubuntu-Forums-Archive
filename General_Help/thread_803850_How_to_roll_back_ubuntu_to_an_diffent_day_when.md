---
title: "How to roll back ubuntu to an diffent day when"
date: 2008-05-22
forum: General Help
---

### Post by dellboy on 2008-05-22
in windows if something goes wrong you can roll back to when your computer worked probably "system restore " how do you do this with ubuntu i need to do this as i update some packages that has  made my computer  not work
i can not seen all  my of what i should be on the screen. so if i could got back to the version i was using yesterday then all would be good.

---

### Post by mikewhatever on 2008-05-22
Ubuntu has no system restore like utility. Try to provide more details about what's going on. Are there any errors?

---

### Post by dellboy on 2008-05-22
ok i think that all i wrong i can not see the toolbar at the bottom of my copy of ubuntu like i can not see the short cut to the desktop worksheet or the bin this all happen after i did to days ubuntu updates  i am also running ubuntu 8.04 also the text seems a bit weird when i am tidying this and looking on a few other websites

thank you for your help

---

### Post by dellboy on 2008-05-27
anyone help me with this when i do a print screen it show up the worksheet short cut icon and the bin but i can not see it my self. 

also some of the text is not looking right as well :(

---

### Post by ibuclaw on 2008-05-27
Have you tested to see if its the same for other users?

Go into "System>Administration>Users and Groups"
Unlock the app, then select "Add User".

Give is a test or dummy name, and a generic password.
Then logout and login to the account.

If the problems you're having aren't present in the new account, then there's probably a desktop setting that's either been deprecated or altered in the upgrade.
And the most convenient way to fix that, is you'll have to "reset" your account by removing most of the hidden files and folders and replacing them with the ones in the /etc/skel folder.

Regards
Iain

---

### Post by dellboy on 2008-05-27
thank you tinivole and mikewhatever for your help 

ok i add a new acount and this time i could not see the shutdown buttion on the top menu bar 

so can you give me a step by step of what i need to do to 

removing the old files :)

---

### Post by ibuclaw on 2008-05-27
Most simplest way, would be to use nautilus.

Open a terminal while still in your test account, and type in:
```
su yourname
```
replace "yourname" with the name of your user account.
Your password is needed.

Then type in:```
sudo -i
```
Again, your password.

Then```

cp /home/yourname /home/yourname.bak -R
nautilus /home
```

When nautilus opens, create a folder named "backup". (should be located in **/home/backup**).

Enter your home folder, select all visible files and folders, and copy them into the backup folder.

Check and double check that they all are there, then delete your account folder.
Create a new folder with the exact same name.

Move all the files in the backup folder into your newly created account folder.

Then type into the location bar **/etc/skel** and you'll be taken to that location.

Press **Ctrl+H** to show hidden files, **Ctrl+A** to select all and **Ctrl+C** to copy all.

Then return to your home folder and press **Ctrl+V** to paste.

Exit nautilus. Then in the terminal, type in:
```

chown yourname /home/yourname -R
chgrp yourname /home/yourname -R

```

Iain

---

### Post by dellboy on 2008-05-28
ok no luck with that any other ideas or i think i do a formate as  i think it needs to be done i am also going to start backing up ubuntu as well as i found a way to back up all date as a zip file 

thank you for your help if anyone knows of anything else that may help before i formate that would be great

---

### Post by phoenix_abhi on 2008-05-28
Select the next oldest kernel to boot and check for the difference

---

### Post by merlin3 on 2008-11-15
This (roll-back) would be a very desirable feature as I have just (STUPIDLY) accepted to downlood all updates and my wireless connectivity is now completely wrecked (polite way of saying it). Considering it took me 2 weeks and several re-inatlls just to get this working I am not pleased at all - if Ubuntu wants to have a chance as a better opsys than the rest then this sort of feature is essential IMHO. This is the thing that makes me nervous about LINUX - its so easy to wreck just by trying out a few suggestions you can wreck your installation.

---

