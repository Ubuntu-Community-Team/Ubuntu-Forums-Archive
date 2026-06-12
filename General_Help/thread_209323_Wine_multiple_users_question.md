---
title: "Wine multiple users question"
date: 2006-07-05
forum: General Help
---

### Post by Kashirigi on 2006-07-05
I've managed to get things ticking along quite smoothly, and while my switch to linux has been pretty painless, there's a few applications that I kind of need from Windows, unfortunately. Luckily, I've been able to get them to work using wine, so it's not as bad as it could be.

However, I'm not the only user who needs these applications. So here's my question -- how do I install wine apps so that they're visible to particular groups? Or do I need to install the apps for each user, or copy registry keys for each user.

Thanks for any help or pointers you can provide.

---

### Post by eks on 2008-02-01
I was googling "wine install multiple users" and this post came third. I have exactly the same question, how to install a software in Wine and have it available for other users?

Anyone...?


eks

---

### Post by PeterJS on 2008-02-01
By default the wine sets it self up in ~/.wine, making it only accessable to the user that's installing the program. Your best bet would be to create a common folder, may I suggest /home/wine,  setting it to be world readable/writeable, and then symlink each user's .wine folder to the global wine folder.

---

### Post by eks on 2008-02-01
Ok, found it:

[http://wiki.jswindle.com/index.php/Advanced_Wine_Installation#Sharing_a_Wine_Installation](http://wiki.jswindle.com/index.php/Advanced_Wine_Installation#Sharing_a_Wine_Installation)

But it's a bit complicated for someone that "just installed Wine through synaptic".... I would need a couple of evenings to get meself better knowledgeable on Wine... Oh well, maybe in some years, if I get proper vacations... :(

EDIT: But I will give PeterJS solution a try ;)


eks

---

