---
title: "Integrate .htaccess with site php login? Please help"
date: 2008-04-03
forum: General Help
---

### Post by lambono on 2008-04-03
Hi guys,
I really hope someone can help me with this...

I am working on a site which uses php authentication to allow users to view pages.
ie. 
   -   user registers username and password
   -   this is stored in mySql database
   -   user logs in
   -   this is checked with values in database 
   -   if this matches display page.

This works fine. 

HOWEVER I also need to grant users access to all files in a user directory.
eg [http://sitename/username](http://sitename/username)

   -   I can do this using .htaccess and a .htpasswd file.
   -   But it effectivally means the user has to log in twice (To view the general php pages and access their personal files)

Now here is the question....

[B]
Is there a way to integrate these so that the 
   -   .htpasswd file is updated when the user registers through the php registration form 
         and
   -   when the user logs in through the php login form they also login for the .htaccess protection.[/B]


Thanks for any help you can provide! 

Lambono

---

### Post by lambono on 2008-04-03
N.B I need to password protect the user directory because as well as accessing the files through the website the user should also be able to automatically download new files in the directory through a podcast managment program like banshee or itunes.

---

### Post by lambono on 2008-04-04
Any thoughts?

---

