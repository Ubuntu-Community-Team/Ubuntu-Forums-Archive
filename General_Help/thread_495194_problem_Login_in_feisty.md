---
title: "problem Login in feisty"
date: 2007-07-07
forum: General Help
---

### Post by boban984 on 2007-07-07
I have a problem login in , i use gnome , i tried to change password from recovery with "passwd" command , it says Password updated succesfully , but i still cant login.
I loged in as root first from recovery , then entered "startx".
But my setting are not the same,how can i login with my username i created when i installed ubuntu.
I didnt mess with the system , one day it worked and the other it didnt.
I get to the login screen but i cant login from there.
when i use recovery i can login with my username , but only in the terminal (command line).
I then try "startx " but it takes me to the login screen of gnome and then i cant login.
i would hate to reinstall because i have a lot of programs downloaded and i would hate to do all the seting up and downloading of programs.

So is there something i can do,or should i reinstall?

---

### Post by MatteBlack on 2007-07-07
Although I don't know what has caused your problem, perhaps the simplest solution would be to delete the user and create another one, making sure you backup anything in the home directory you want to hang on to just to be on the safe side. 

If you can log in under X as root then it would be easy to do this using the System-Administration-users and groups menu. Although ideally you should never log in under X as root if you can avoid it! So if there are any other users on the system using that account would be better practice.

---

