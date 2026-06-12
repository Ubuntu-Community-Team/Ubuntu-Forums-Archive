---
title: "Medical Billing Software"
date: 2007-08-29
forum: General Help
---

### Post by computergee on 2007-08-29
I have a friend who works in the medical billing field, and he uses a program called Rollin's Advocare.  He has trouble keeping his Windows install clean, and I often have to clean it out for him. Now I am convincing him to try switching to Ubuntu, but I need to make sure this program can run. They didn't provide him with any means of re-installing the program by himself, which I find really strange. I think if I just copy the program's folder over, it should work. It seems to just be internet browser based. A look in the program's folder showed that it was filled with html and asp files. I copied this folder to my Ubuntu installation, but I could not get the program to display correctly. Do asp files need some sort of server program running in order for them to run? Here is a link to the program's requirements, it seems to need some sort of server running...

[http://www.rollinshealthcare.com/advocare_hwsw.html](http://www.rollinshealthcare.com/advocare_hwsw.html)

Thanks in advance for any help.

---

### Post by solar george on 2007-08-29
Try installing the LAMP server package and putting all of the html and asp pages into /var/www

---

### Post by computergee on 2007-08-29
I put it in the /var/www/html/ folder of my MythTV box (mythweb works fine), when i type /192.168.0.105/AdvoCare into a web browser, I just get an index of the directory. If I click on the index.html, firefox just shows the code. How do I launch this?

---

### Post by solar george on 2007-08-30
Don't have a clue - I don't know how mythweb works. Try the LAMP server on a clean install.

---

