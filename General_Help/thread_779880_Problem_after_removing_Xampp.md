---
title: "Problem after removing Xampp"
date: 2008-05-03
forum: General Help
---

### Post by reyhan on 2008-05-03
i just remove Xampp from 

[http://www.apachefriends.org/en/xampp-linux.html]("http://www.apachefriends.org/en/xampp-linux.html")

after i remove it by this command

```
rm -rf /opt/lampp 
```

and i Install the Lamp server 

why i have this problem?

---

### Post by Monicker on 2008-05-03
Why are you trying to go to a url for xampp, after you uninstalled it???

---

### Post by scusick on 2009-03-18
This is a pretty old post, just wondering if anyone knows what the issue here is.  I did exactly the same thing.  I did 

rm -rf /opt/lampp


Then reinstalled apache2 etc..

I go to localhost, and everything works fine.  However, if I type in my ip address it gives me exactly what I see above.  It has [http://www.myipaddress/xampp/](http://www.myipaddress/xampp/)

I am not sure how to get rid of the xampp.  Any clues??

Appreciate the help.

C

---

### Post by tkearn5000 on 2009-04-12
I don't know if I'm having the same exact problem, but, after uninstalling xampp, I have found that many of the programs that are bundled with it are still in my /etc directory. Maybe this is what is causing your problems.

Has anyone had to deal with this? Is there any way to delete them all. I can go through and delete some of them by hand, but since so many programs came with xampp, I don't know the names of all of them. Also, where elso on my PC are files that I no longer want hiding because of this?

Thanks,
-TK

---

