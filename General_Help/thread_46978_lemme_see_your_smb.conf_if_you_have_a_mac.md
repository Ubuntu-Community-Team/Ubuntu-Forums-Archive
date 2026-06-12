---
title: "lemme see your smb.conf if you have a mac"
date: 2005-07-06
forum: General Help
---

### Post by Digitallysick on 2005-07-06
I want to connect to my linux box from my mac, can't get samba to work, both comps see each other but cannot connect any ideas??

---

### Post by jarrett.wold on 2005-07-06
Something that got me at first was that I had to use sambapasswd to create a user that could access the samba share.

man sambapasswd is what got me over it.

---

### Post by Digitallysick on 2005-07-07
well i finally fixed it, here is what i did. 

i started with a fresh smb.conf file,  my max and ubuntu were seeing eachother but i wasn't able to connect,  i finally got the smb.conf file right, now the issue became that my mac sees ubuntu in the network but cant connect, and it still cant, but if i open up the finder and click "go to server" and put in smb://Ubuntu , it works! also remember that you the smb.conf file is case sensitive,  (apparently) i had going to /home/files which was showing nothing, i changed it to /home/Files, and now it works right!! thanks to all that helped, and if you need any help i will do my best!! thanks, an ubuntu fan once again

---

