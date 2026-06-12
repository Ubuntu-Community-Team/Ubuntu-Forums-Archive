---
title: "Cannot save to opt/lampp/htdocs OR /bin"
date: 2006-12-10
forum: General Help
---

### Post by rakesh1 on 2006-12-10
Hello All,

I recently downloaded and installed XAMPP for Linux.

I extracted the files like this:

tar xvfz xampp-linux-1.5.5a.tar.gz -C /opt

as it said to on the XAMPP site.

I am able to get Apache up and running.  

My problem occurs when I try to save files to the htdocs folder.  I've used XAMPP in windows and I know that to run files on the webserver, they have to be saved in htdocs.  So I'm assuming the same goes for XAMPP on Linux.

I get this message when trying to save a simple "hello world" php file with an echo statement:

"Could not save the file "/opt/lampp/htdocs/hello.php"

I thought it was a priviledges thing so I think I made sure that I was logged in as the superuser by typing "su" in the terminal and entering my password.  I'm the only user.  Am I still not logged on as the "root" or "superuser"?

So I basically need to find out why I can't save to the htdocs folder.

Thank You in advance,

rakesh1.

---

### Post by rakesh1 on 2006-12-10
Anyone have any ideas at all?

---

### Post by rakesh1 on 2006-12-11
It looks like I had to chmod the desired folder to 777.  If I am the only user and I did log in as superuser from the terminal, why was I not able to write to this directory until after I did a chmod ?

---

