---
title: "Apache2 Problems"
date: 2005-07-28
forum: General Help
---

### Post by Norrad on 2005-07-28
Hi Everyone, thanks for all the help so far. Its made my transition to linux very pleasant.

I have one last problem now. I have installed Apache/MySQL/PHP4 and I can view my pages at [http://localhost](http://localhost) but I have run into a small problem. I have created a new folder called mysite in my var/www/ directory and changed it's ownership from root to myusername. When I upload a php or html file I can view it fine but when I upload images or stylesheets they do not display. I created a new folder called images in /var/www/mysite/images and when I view it at [http://localhost/mysite/images](http://localhost/mysite/images) I get a listing of all the images but when I click on one of them I get a permission denied error. Is this a common problem? How do I fix it?

Kind regards,
Norrad

---

### Post by heimo on 2005-07-28
It's file permission error. You need to give read permission to those files for the user Apache runs (typically www-data). Open terminal, change into that directory and run something like
 ```
chmod a+r *
```
To give read permission to everyone for those files (no matter who owns them).


EDIT: Probably something like this could work too:
 ```
chgrp www-data /var/www/mysite/images/*
chmod g+r /var/www/mysite/images/*

```

---

### Post by Norrad on 2005-07-28
I've just checked their permissions and everyone can read them  :-|

---

### Post by heimo on 2005-07-28
Check the directory permissions too. To me, it sounds like those should be ok as you already can change into that directory and list files. But you can try:

 ```
chown www-data:www-data /path/to/directory
chmod ug+rx /path/to/directory

``` 
Or you can move one of those images back to wwwroot (parent directory) and  ```
chmod 777 filename

``` 
... just to make sure that it's not about permissions.

Oh! Just re-read your first post - change the group of that directory under /var/www/ to www-data and add your user to www-data group.

---

### Post by Norrad on 2005-07-28
Thanks a million, going to give it a try when I get home  :)

---

### Post by heimo on 2005-07-28
No problem. I edited my post abowe just a minute ago, so check that you didn't miss my last addition. Hopefully you can get it fixed (been there, I know how it can be hard to notice some small detail). It's not a big thing, very probably just some permission "bit".

---

