---
title: "Character encoding in Firefox"
date: 2006-08-24
forum: General Help
---

### Post by jpmonette on 2006-08-24
Hi

I have a little problem with charsets. First of all, I'm speaking french and i use iso-8859-1 on my websites. I made my website on Ubuntu with gedit and i tried it via [http://localhost/index.php](http://localhost/index.php). I have a form to send some info on my MySQL DB. When I put some éèï and every other accent characters and i go get the result in PHPMyAdmin, all my accents are messed up (QuÃƒÂ©bec).

I have this meta at the top of my index.php:
> <meta http-equiv="Content-Type" content="text/html;charset=iso-8859-1" />

When i open the page with Firefox, i look in the browser encoding and it's set on UTF-8! I also tried to change my index.php encoding to utf-8 and my characters are messed up too in PHPMyAdmin.

I have two other questions. I'd like to know if it's possible to do automaticaly a chmod -R 755 on my /home/user/dev/www folder because each time i add a new file in the rep, i need to chmod it by hand.

Last question, i'm searching for another text editor thant gedit for programming because i have some problems with the syntax coloration. Is there another text editor allowing to color html and php at the same time?

Thanks

---

### Post by jpmonette on 2006-08-24
Nobody have the answer? Or at least one of these 3 questions?

---

### Post by MiniMe on 2008-01-17
I'm having exactly the same problem with Ubuntu Gutsy. I'm guessing there must be a simple solution to this because I have no problems with the French characters when developing on Windows XP.

---

### Post by erginemr on 2008-01-17
Question #3: Give a try to Geany with
```
sudo aptitude install geany
```
it is a light-weight, but also feature rich programmer's editor. Its home page is:
[http://geany.uvena.de/](http://geany.uvena.de/)

For HTML editing, you may also try Bluefish:
[http://bluefish.openoffice.nl/](http://bluefish.openoffice.nl/)

---

### Post by MiniMe on 2008-05-05
I think I figured out why I'm not getting the special characters to display correctly. The default Ubuntu encoding is UTF-8 however, on the webserver we're using it's iso-8859-1. This seems to be causing problems even though in the webpage I define:
 <meta http-equiv="Content-Type" content="text/html;charset=iso-8859-1" /> 

Ubuntu seems to check out the file UTF-8. Is there a way I can change the default encoding on Ubuntu to iso-8859-1?

Thanks in advance.

---

