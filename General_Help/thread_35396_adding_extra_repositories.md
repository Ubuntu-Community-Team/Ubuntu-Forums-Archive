---
title: "adding extra repositories"
date: 2005-05-18
forum: General Help
---

### Post by nuke16433 on 2005-05-18
I want to add extra repositories... I did all steps according to Ubuntu guide, but in 6th step ( This command: gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907 ) I have a problem.
I can not connect to key server, I think it's because of port filtering from my ISP... now I wanna know is it possible to recieve these keys by another way?

--Respect.
    ToTo

---

### Post by dave9191 on 2005-05-18
I didnt even know that there was a 6th step. I just added the extra addresses to my repository files and did an apt-get update. 

Dave

---

### Post by bruizer on 2005-05-18
You only need to add this particular keyserver and key if you want to use the ftp.nerim sites... You can use all the others without adding the keyserver.

I had to use the key to get it to work for me, but dave9191 didn't. Try updating without adding the keys.

Let us knw how it works!

---

### Post by bruizer on 2005-05-18
BTW - if you are interested, Ubuntu also has a backports project. Check it out:
[http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)

---

### Post by nuke16433 on 2005-05-19
Thanks for your reply...
I did it once without keys, and I updated apt-get successfully ,but I could not install any package.
I will try it again later 'n i'll inform you about the result  ;-)

---

