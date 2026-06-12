---
title: "MySQL: the Great Root Password Mystery"
date: 2005-07-04
forum: General Help
---

### Post by Akir on 2005-07-04
I'm trying to start somewhat of a webpage, though I'm not yet sure that others will be able to fiew it because of a router. on this webpage, there will be a forum. That forum will be phpBB. However phpBB requires an SQL, especially MySQL (postgreSQL isn't an option here mostly on personal prefrences, and the others are MS).
     The problem is this: I had set it up via Synaptic. However, it had set up the root user *with a password*. ](*,)
     All I need to know is what it is and/or how I can change it.

---

### Post by revs on 2005-07-05
try this

```
mysqladmin -u root password put_your_password_here
```

a simple google for "ubuntu mysql install" helps  :) 

[See here](http://majalah.com/#installmysqldatabaseserver) 


regarding the bit about others seeing your page behind a router - what you will have to do is forward the ports on the router to the server. i.e. forward port 80. This means that any request on port 80 gets sent to the server.

revs

---

### Post by Akir on 2005-07-05
I tried that, but it didn't work. So I figure that it was already set and that the command was disabled for security purposes. I'll try it again, but It will have to wait ~2 weeks on a count of a summer event I am attending. 
 
As per the Router problem, I think I have it solved. It uses literally virtual networking; supplying me with a psudo-IP. All I had to do was regester my Psudo-IP and Port into the "Virtual Server" list, and give people the actual IP.

---

### Post by Abhi Kalyan on 2006-11-04
> **Akir said:**
> I tried that, but it didn't work. So I figure that it was already set and that the command was disabled for security purposes. I'll try it again, but It will have to wait ~2 weeks on a count of a summer event I am attending. 
 
As per the Router problem, I think I have it solved. It uses literally virtual networking; supplying me with a psudo-IP. All I had to do was regester my Psudo-IP and Port into the "Virtual Server" list, and give people the actual IP.
MY GOD!
Guys i had a major time out with the proper syntax GRHHH!!!
exactly as i typed it atlast, does every comma and space matter so much, GRHHH!

SET Password = PASSWORD( 'sathyam' );

this i typed after logging into the mysql,
after loads of trying i found that me being so dumb had set my password to
"newrootsqlpassword"
Please laugh

Thank you guys You are wonderful
Love you all

---

