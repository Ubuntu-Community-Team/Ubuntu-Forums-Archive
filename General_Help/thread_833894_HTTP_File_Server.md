---
title: "HTTP File Server?"
date: 2008-06-19
forum: General Help
---

### Post by n8dude on 2008-06-19
I hope I'm posting this in the right section, but I was wondering if anybody knew of anything like [http://www.rejetto.com/hfs/?f=intro](http://www.rejetto.com/hfs/?f=intro) 
Wine wouldn't be an answer because it would be running on a server that runs with no desktop environment. If anybody knows of anything like that for linux, please tell me :) (Yes, I have googled it)

---

### Post by manfer on 2008-06-19
Let's see if I understood. You want something like that but not that program under wine because you want something running in text mode runlevel.

That program is a web server as you can see clients uses the http protocol to access the server. What it offers is a lot of easy ways to configure folders to share, permission, ... , saving the shares between sessions ...

I don't know if there is something like that, so easy to work with for that particular purpose of sharing, with so much other soft you have to do such things. There's a lot of P2P sharing staff.

But if you don't need so much easy features that includes that soft and only need that kind of sharing sometimes. Why don't you just install apache web server, creates on it a share folder, and put in it symblinks to the folders on your system you want to share?

```

prompt:~$ **sudo   apt-get   install   apache2**
prompt:~$ **sudo   mkdir   /var/www/share**
prompt:~$ **sudo   ln   -s   /home/your_user_name/folder_to_share   /var/www/share**
prompt:~$ **sudo   ln   -s   /home/your_user_name/otherfolder_to_share   /var/www/share**

```

And people just can access that share with their web browsers;

[http://your_IP/share/](http://your_IP/share/)

If you need to restrict access, for sure you could do it too.

When you want to stop the sharing:

```

prompt:~$ **sudo   rm   /var/www/share/***

```

*Note: That won't remove data on your original folders, only removes the symblinks on the share *folder.

---

### Post by n8dude on 2008-06-19
Thanks, I was not aware that Apache Could do something like that. Thanks for the Help :)

---

