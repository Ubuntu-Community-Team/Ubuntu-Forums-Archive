---
title: "Trouble with NTFS"
date: 2006-12-31
forum: General Help
---

### Post by CreatorAmongFriends on 2006-12-31
Im sure you've all seen it before. I need to get into my NTFS drive but i am unable to. This is my first real time using Linux, but i have ample expirence using windows. My issue is that its connected to my IDE cable, in device manager its there, "unmounted". My friend brings over his external, hooks up fine, and shows up. Im at a stalemate, i need that information. So much music going untouched, as well as many other important files i need. I'm having trouble understand the whole Linux file structure as well as the terminal. Its been years since dos was a regular occurance. If you guys could help out i'd greatly appreciate it. Thanks a million, look forward to hearing from you.

---

### Post by taurus on 2006-12-31
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by pseudonym on 2006-12-31
Hi, could you post the contents of your /etc/fstab file...

EDIT - what taurus said :)

---

### Post by ruidobranco on 2007-01-01
Hi. Ok, you must edit your FSTAB file in the etc dir. Ok? It not dificult.

Well, i 'll post the comand that works for me. Perhaps you can use. 

/dev/hdd1 /mnt/hdd1 ntfs noauto,users,exec,ro,umask=000,uid=kurumin,gid=kurumin 

Ohh, you should change your HD identification. In my case, it's the slave of the secondary ide controller.

And kurumin it's my debian based distro. Ok? Hope this can help you.

Happy new year.

---

