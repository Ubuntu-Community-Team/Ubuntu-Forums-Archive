---
title: "Trouble with Users/Groups Added"
date: 2006-11-06
forum: General Help
---

### Post by Ubuntu Joe on 2006-11-06
:( Using Ubuntu Edgy, I created an additional user profile for my wife so she can have a nice pretty desktop while I have my awesome, GUY desktop . . . Sounds simple, right?

I simply added a user from the menu at the top of my awesomely manly desktop and everything seemed fine . . . 

However, when using her desktop, I found that I can't "Save As" in OpenOffice . . . the program crashes everytime . . . What on earth would cause THAT?!

I can "save As" no problem under my own profile . . .

HELP!  MY WIFE WILL KILL ME!

:(

---

### Post by boban on 2006-11-06
I don't know if it will help, but - try adding her to the same groups your user is in... (you'll have to logout her before changes take effect)

---

### Post by Ubuntu Joe on 2006-11-06
I initially added her to my group, then I tried making her her own group . . . we both have identical permissions, but no dice, either way!

---

### Post by boban on 2006-11-06
Every user in linux belongs to two type of groups: his "native" group and other groups...
Check /etc/group file... I think that there is correlation between graphical tool "User and Groups", tab "Permissions" and  that file (but I'm not good at graphical management of Linux). Maybe you should look at her permissions there and check if both of you have the same permissions...

And in this "Users and Groups" you have manage gropus button. Click on it and check every group's proprties - if your user is there, then add your's wife user...

(you are aware that I am making a guess what could be wrong with open office?)

---

### Post by Ubuntu Joe on 2006-11-06
All right, dawgs . . .



I deleted my wife's profile and added her through the terminal instead and that totally WORKED, baby . . . Message to self: Always use the terminal . . .

```
sudo adduser -m "username" -G adm,dialout,cdrom,floppy,audio,dip,video,plugdev,lpadmin,scanner,admin
```

This added her to a group with her own name and all of the groups I had permission to as well . . . awesome!

---

### Post by boban on 2006-11-07
Just one notice for the future... You didn't need to remove her profile... You could just try using gpasswd... Sorry for not telling you about this command earlier :(

---

### Post by Ubuntu Joe on 2006-11-07
What does gpasswd do?

---

### Post by boban on 2006-11-07
In this context:

```

sudo gpasswd -a boban adm

```

Would add user 'boban' to group 'adm'... That way you could add your wife user to any groups you want :)

You can get more info on gpasswd (or any command you want) with man gpaswwd... (or you can ask at this forums, but you'll get info from man instantly :) )

---

### Post by Ubuntu Joe on 2006-11-07
Thanks, bro!

---

### Post by boban on 2006-11-07
> **saalota said:**
> Thanks, bro!

You are welcome... I'm glad I could help :)

---

