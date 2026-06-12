---
title: "Apache Settings"
date: 2008-03-23
forum: General Help
---

### Post by Touch.Code on 2008-03-23
Hi,

How can I edit the settings of Apache? I can't even allow downloads. In abyss, I would do 127.0.0.1:8080 but Apache doesn't work like that.

Thanks,
James

---

### Post by ikonia on 2008-03-23
what do you actually want to change ??

it looks like your trying to use apache as a proxy server, 

apache is actually a webserver, are you sure you have the right tool for the job.

---

### Post by Touch.Code on 2008-03-23
Look, [Example]("http://jamesb.webhop.org/downloads/HDD%20PM/HDDPM.png")

I need it so people can download stuff etc. How can I remove apache and install abyss then?

---

### Post by ikonia on 2008-03-23
please change that link - I'm not comfortable seeing a link in forum that links to a download called "spammer.exe"

---

### Post by Touch.Code on 2008-03-23
Sorry. Done. Now goes to an image :)

---

### Post by ikonia on 2008-03-23
ok, so your connection is now working, the file your offering just has the wrong permissions.

it needs execute or even better read permissions by the user/group that is running the apache process.

check which user owns the apache process, then change permissions so that, that user can read and execute the file you want to download.

---

### Post by Touch.Code on 2008-03-23
I chmod the whole folder to 775.

---

### Post by Touch.Code on 2008-03-23
So I am now confused. I tried to do, sudo chmod 775 /var/www it didn't do anything. Same error again :(

Done it :) -R parameter works!

---

### Post by ikonia on 2008-03-23
you've had a problem because you've not read what I advised you to do.

I asked you to change the permissions of the FILE you want to download, /var/www is the DIRECTORY that the file is under.

When you did a chmod -R you did a recursive chown which has changed the permissions of everything underneith /var/www which seems a bit over the top. 

Please read the advice given to you as recursive chowns/chmods in the wrong place could break your system for good.

---

### Post by Touch.Code on 2008-03-24
I have done it. I did it that way as I didn't want to go through over 100 directories only changing a couple at a time. All done though :)

---

