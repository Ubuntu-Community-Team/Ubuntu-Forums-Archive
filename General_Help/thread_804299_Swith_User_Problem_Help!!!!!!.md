---
title: "Swith User Problem Help!!!!!!"
date: 2008-05-23
forum: General Help
---

### Post by D_JKR130 on 2008-05-23
Ok Guys This is my problem with ubuntu 8.04

I have two accounts on ubuntu my account and my brother's account when i log in to my account everyting works fine but when i swith user to my brother's account the only thing i see is the background i cant see the menus and nothigs loads.

The only way i can log to my broters account is by restaring ubuntu and log in to my brother account and i cant log on i need to restar the computer everytime i want to switch user 

Can someone help me Please  :( :confused:

---

### Post by fsmithred on 2008-05-23
How did you create your brother's account in the first place? It sounds like something is wrong with the files in his home directory. 

Things that might fix it:

You can delete all the hidden files/directories in his home and then log in as him. Those files will be re-created automatically, as needed. Note that you'll lose any custom desktop settings, but it doesn't sound like that will be a problem in this case.

If you're the admin, you can delete his account and his home directory entirely, and then re-create his account. (I don't know what happens if you try to delete the first account.) And you'll probably want to add him to some groups, like plugdev and cdrom.

---

### Post by D_JKR130 on 2008-05-23
So what r u telling me to do is to delete my brothers account and delete all the files in the home directory and then make another account for him
:confused:

---

### Post by fsmithred on 2008-05-24
Yeah. If there are any files that you want to save, then move them first. What I'm suggesting are quick fixes, and may not even help. If you want to know what went wrong, that's more difficult, and you need to retrace your steps. 

What happens if you kill the x-server with ctrl-alt-backspace? Can you log in as the other user then?

Compare your problem to this one -
[http://ubuntuforums.org/showthread.php?t=803491&highlight=switch+user](http://ubuntuforums.org/showthread.php?t=803491&highlight=switch+user)

---

