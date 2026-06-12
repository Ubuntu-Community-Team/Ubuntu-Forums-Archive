---
title: "please, make me happy"
date: 2008-04-10
forum: General Help
---

### Post by jusbug on 2008-04-10
hi guyz,
i just installed ubuntu studio 7.10 and i must tell you, i'm very happy, i just like it.
i installed the two software that i need which is apple shake and the foundry nuke and they rock under linux.
but if you want to help me and make me even more happier can you guys please show me how to do some magic tricks, i'll explain:
i have shake installed in 
/usr/shake-v4.10.0606
and the plugin that i want to use under shake is in /usr/nreal/Furnace3.0v1_shake4.00-linux-x86-release-32/include
now i need to tell Shake where to look for the plug-ins, and following furnace's doc (it's the plugin i want to use with shake) i have to set environment variables to my .login file,
"setenv NR_INCLUDE_PATH /usr/nreal/
   Furnace3.0v1_shake4.00-linux-x86-release-32/
   include"
my question is how i do this?
i know how to do it under window, you set the variable "NR_INCLUDE_PATH" and the path to the directory underneath.

and one more thing guys, is it normal when you browse with a software you you dont see the other NTFS partition. 

big big thanks guyz.

---

### Post by fguilhon on 2008-04-10
Welcome to the captivating world of Ubuntu!
That's how things are in Ubuntu: they just work.
As to your question, I don't know this setenv command, maybe it's only for *BSD.The command to use for env vars in Linux is **export**.
So, you edit ~/.profile (or ~/.bash_profile or ~/.bash_login, if they exist) with:
```
gedit ~/.profile
```
and put this into the file:
```
export NR_INCLUDE_PATH=/usr/nreal/Furnace3.0v1_shake4.00-linux-x86-release-32/
```

---

### Post by opscure on 2008-04-10
You could also try and softlink the folder to your nreal directory.
```

ln -s /usr/nreal/Furnace3.0v1_shake4.00-linux-x86-release-32/include/ /usr/nreal/Furnace3.0

```

There is also more information about environment variables in this post [http://ubuntuforums.org/showthread.php?t=2793&highlight=%252Fetc%252Fprofile+PATH](http://ubuntuforums.org/showthread.php?t=2793&highlight=%252Fetc%252Fprofile+PATH)

---

### Post by jusbug on 2008-04-11
i did what exactly "fguilhon" said, and now i have a big probleme, after the username and password i got
an error message saying something about gtk and the line i added, and then logout and if i try to login again the system freez.
any help to delete those lines with command under a safemose?

---

### Post by fguilhon on 2008-04-14
I'm terribly sorry... this command isn't supposed to behave like this.. it's a simple env var setting.. but I should have warned you because ~/.profile is a login script.. and any error keep you from loggin in.. I'm really sorry..
If you can't log in now, the only way is to enter rescue mode... (the option that pop ups when you boot)
you can find more info in [http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch08.html]("http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch08.html")

---

### Post by panayk on 2008-04-14
At the login screen, lower-left corner, click "Options"->"Select Session"->"Failsafe GNOME" and login.
After you've fixed the problem remember to re-login using GNOME or Xclient session.

---

