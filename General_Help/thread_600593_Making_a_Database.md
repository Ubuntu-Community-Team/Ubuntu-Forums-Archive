---
title: "Making a Database"
date: 2007-11-02
forum: General Help
---

### Post by TorchlightJay on 2007-11-02
Okay so I have some background in the whole LAMP deal. Not a whole lot but enough to get by, or at least get started. I am still learning, anyways, I want to setup a customer database in MySQL. I want to put it on it's own server so that i can access it from more than one computer should I be on the field and need to reach it with my notebook or an employee needs to or whatever. 

I want the database to contain like customer information, vendor information, a task list, call list, etc. Basically I want us to be able to go to the database, see all of our vendor contacts and also see all customer information including jobs we've done for them in the past, next appointments, etc. I want it to also have something like a calendar and address book. I was wondering, what would be a good viewer or additional software to make this all happen? 

Like I know openoffice.org base can integrate with MySQL so if we want to , we can edit forms and stuff with openoffice.org (correct me if I am wrong) but are there other software pieces we can use to edit this information or forms, whatever. Also, what is a good online calendar and contact software I can integrate with all of this? Like I want to be able to store contacts on the database, be be able to view the contact list pretty easily and cleanly. Same with a calendar. 

I hope I am making sense. I am sure I can make something in php or download a php program and do it all online but i'd like to localize it to the computer if at all possible. Thank for all your help. I hope I made sense.

---

### Post by jonnymccullagh on 2007-11-02
SugarCRM ?

---

### Post by TorchlightJay on 2007-11-02
Ya, I have SugarCRM but I still need to log into it in order to do all the stuff. That and I can't really make much sense out of it. I was wondering if there was something simpler out there.

---

### Post by Scimu on 2007-11-02
Well if you just want to look at your tables and all, just look at it via PHPMyAdmin or make a simple PHP script. Then login to PHPMyAdmin by like [http://www.yourdomain.com/phpmyadmin](http://www.yourdomain.com/phpmyadmin) or [http://YourIP/phpmyadmin](http://YourIP/phpmyadmin) or if your on the computer where it is running on [http://localhost/phpmyadmin](http://localhost/phpmyadmin). This would require an HTTPD server though. If you want I will gladly write a little script to get info from MySQL using PHP.

---

