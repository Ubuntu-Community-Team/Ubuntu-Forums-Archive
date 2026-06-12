---
title: "Apache / PHP problems"
date: 2008-05-30
forum: General Help
---

### Post by rax_m on 2008-05-30
Hi. 

I am trying to install/configure an application (refbase - A reference manager) onto Apache. The install seemed to go fine. 

One of the steps is to navigate to [http://localhost/refbase/install.php](http://localhost/refbase/install.php)
I manage to do that but after clicking "install" I get a blank page. I also get a blank page for index.php. 

Yet if my test.php in /var/www works fine. 

Any ideas what can cause this?

Thanks
Rax

PS I have posted to the refbase forums as well. No solution yet.

---

### Post by tigerplug on 2008-05-30
Does this application require a mySQL database?

If so have you already created a user fro the application with the relevant rights/permissions and created the database?

---

### Post by rax_m on 2008-05-30
Hi. 
Yep, it does require a MySQL database. In theory the install.php script should create the user and DB for me. 
However, because of this issue, I created the user and db and tables myself according to the manual install instructions. 
Problem is, even the default index.php just shows a blank page. The only two php files that seem to load correctly are install.php and upgrade.php. But executing either just brings a blank page. 

Rax

---

